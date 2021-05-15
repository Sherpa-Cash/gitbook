# Nasıl Çalışır

Bir blok zincirindeki işlemler, tek ve uzun bir uzun zincir oluşturur. Bu da işlemleri izlemeyi kolaylaştırır. Sherpa Cash ise, alıcı ve hedef adresler arasındaki zincirin üzerinde bulunan bağlantıyı kırarak işlem gizliliğini arttırır.

Sherpa Cash, bunu belirli bir token için; sabit bir birimle token yatırmayı kabul eden akıllı sözleşmeleri kullanarak yapar.

Örneğin, 0.1 AVAX sözleşmesi, yalnızca 0.1 AVAX yatırmaya ve çekmeye izin verecektir. Başlangıçta aşağıdaki token ve birim kombinasyonlarına sahip olacağız:

* 0.1 AVAX
* 1 AVAX
* 10 AVAX
* 100 AVAX

Fonlar yatırıldıktan sonra kullanıcı, yatırdığı miktarın kanıtı veya sahip olduğu hakkı bildiren bir "not" alacaktır. Bu not, kullanıcının yatırdığı miktarın, daha sonra başka bir adres tarafından çekilmesi için kullanılır. Sonuç olarak bu sayede, iki adres arasında doğrudan bir bağlantı olmadan; bir adresten başka bir adrese transfer gerçekleştirmiş olursunuz.

Bunların hepsi çok kafa karıştırıcı geliyorsa basit bir örnekle açıklamamıza izin verin. Örneğin, Alice'in 100 AVAX'ı A cüzdanından B cüzdanına aktarmak istediğini düşünün:

1. Alice ilk olarak Sherpa'nın 100 AVAX sözleşmesine 100 AVAX yatırır. Karşılığında aşağıdaki gibi görünen bir not alır. ** Bu not gizli tutulmalıdır! **
2. Alice, 100 AVAX'ı geri çekmek için; notu ve B cüzdanının adresini yapıştırır ve geri çekme fonksiyonunu çağırır. Hepsi bu kadar!

```text
sherpa-eth-0.1-1-0x07f00caa131a209ac0db1401be7f2f568d8a49f0459e92a5b9e28610ac71fad948537e978ece8a62091b9305a8df2817113f7e8010c5ec5510149c5bfb25
```

### **Fonları Relayer\(Aktarıcı\) ile Çekme**

* Fonları bir ağ üzerinden çekerken belirli bir miktarda gaz ücreti ödenmesi gerekir. Fakat bu gaz, esasen herhangi bir yerden gelmiş olan AVAX’tır. Bu da onu takip edilebilir yapar. Peki ya Alice hiç işlem geçmişine sahip olmayan bir adrese para çekmek isterse?
* Bu durumda, Alice bir relayer kullanarak çekme işlemini gerçekleştirebilir. Relayer, Alice için fonları çekme fonksiyonunu çağırır ve fonları, gaz ücretini keserek, kendisinin cüzdanına aktarır.

### **Anonimlik Dizisi**

* Anonimlik dizisi, çekim işleminizin potansiyel kaynağı olabilecek yatırma işlemi sayısıdır.
* Eğer anonimlik dizisinin değeri 1 ise; fonları çekme işleminiz, açıklanamaz bir şekilde hesabınıza yatırılan fonlarla ilişkilendirilecektir.
* Yani dizinin sayısı ne kadar yüksekse, çekme işleminizin; hesabınıza yatırılan fonlarla bağdaşması veya ilişkilendirilmesi o kadar zor olur.
* Bu nedenle, fonlarınızı çekmeden önce anonimlik dizisinin artması için biraz beklemenizi tavsiye ederiz.

### Kulağa sihirli gibi geliyor. Peki bunu nasıl yapabiliyor?

En önemli detay, fonları yatırdığınızda oluşturulan nottadır. Sözleşmeyi, notunuz ile birlikte sunduktan sonra; sözleşme, önce yatırma işleminin yapılıp yapılmadığını kontrol eder. Ardından fonları çekme işleminizin daha önce yapıp yapmadığınızı kontrol eder. \(Bu işlemin sıfır bilgi ispatını kullanarak nasıl gerçekleştiği hakkında daha fazla bilgi için orjinal whitepaper’ı okuyabilirsiniz.\) Bu iki kontrolden geçildiği takdirde ise sözleşme fonlarınızı çekmenize izin verir.