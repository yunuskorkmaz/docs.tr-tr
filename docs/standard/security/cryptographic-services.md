---
title: Şifreleme Hizmetleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryption [.NET Framework]
- private keys
- MAC algorithms
- cryptographic algorithms
- private keys, overview
- encryption [.NET Framework]
- security [.NET Framework], encryption
- cryptographic services
- symmetric cryptographic algorithms
- hash
- message authentication codes
- derived class inheritance
- cryptography [.NET Framework], about
- random number generation
ms.assetid: f96284bc-7b73-44b5-ac59-fac613ad09f8
ms.openlocfilehash: c1783a578d0b55b0b62a1ffb870802faca97623f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187005"
---
# <a name="cryptographic-services"></a>Şifreleme Hizmetleri

Internet gibi genel ağlar, varlıklar arasında güvenli bir iletişim aracı sağlamaz. Bu tür ağlar üzerinden iletişim, yetkisiz üçüncü şahıslar tarafından okunmaya ve hatta değiştirilmeye açıktır. Şifreleme, verilerin görüntülenmesini korumaya yardımcı olur, verilerin değiştirilip değiştirilmediğini algılamanın yollarını sağlar ve aksi takdirde güvenli olmayan kanallar üzerinden güvenli bir iletişim aracı sağlamaya yardımcı olur. Örneğin, veriler bir şifreleme algoritması kullanılarak şifrelenebilir, şifreli bir durumda iletilebilir ve daha sonra amaçlanan taraf tarafından şifresi çözülebilir. Üçüncü bir taraf şifrelenmiş verileri ele gevelürse, şifreyi çözmek zor olacaktır.

.NET Framework'de, <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanındaki sınıflar sizin için şifrelemenin birçok ayrıntısını yönetir. Bazıları yönetilmeyen Microsoft Şifreleme API'si (CryptoAPI) için paketleyiciler, diğerleri ise tamamen yönetilen uygulamalardır. Bu sınıfları kullanmak için şifreleme uzmanı olmanız gerekmez. Şifreleme algoritması sınıflarından birinin yeni bir örneğini oluşturduğunuzda, anahtarlar kullanım kolaylığı için otomatik olarak oluşturulur ve varsayılan özellikler olabildiğince güvenli ve emniyetli olur.

Bu genel bakış, .NET Framework 3.5'te tanıtılan ClickOnce bildirimleri, Suite B ve Şifreleme Yeni Nesil (CNG) desteği de dahil olmak üzere .NET Framework tarafından desteklenen şifreleme yöntemlerinin ve uygulamalarının bir özetini sağlar.

Şifreleme ve Microsoft hizmetleri, bileşenleri ve uygulamalarınız için şifreleme güvenliği eklemenize olanak tanıyan araçlar hakkında daha fazla bilgi için bu belgelerin Win32 ve COM Geliştirme, Güvenlik bölümüne bakın.

## <a name="cryptographic-primitives"></a>Kriptografik İlkeller

Şifrelemenin kullanıldığı tipik bir durumda, iki taraf (Gamze ve Kemal) güvenli olmayan bir kanal üzerinden iletişim kurar. Alice ve Bob, dinleyen herkes tarafından iletişimlerinin anlaşılmaz kalmasını istiyor. Ayrıca, Gamze ve Bob uzak konumlarda olduğundan, Gamze'nin Bob'dan aldığı bilgilerin iletim sırasında kimse tarafından değiştirilmediğinden emin olması gerekir. Buna ek olarak, bilgilerin gerçekten Bob'u taklit eden birinden değil, Bob'dan kaynaklandığından emin olmalıdır.

Şifreleme aşağıdaki hedeflere ulaşmak için kullanılır:

- Gizlilik: Kullanıcının kimliğinin veya verilerinin okunmasını korumaya yardımcı olmak için.

- Veri bütünlüğü: Verilerin değiştirilmesini korumaya yardımcı olmak için.

- Kimlik doğrulama: Verilerin belirli bir partiden kaynaklandığından emin olmak için.

- İnkar etmeme: Belirli bir tarafın bir ileti gönderdiğini reddetmesini engellemek için.

Bu hedeflere ulaşmak için, şifreleme düzeni oluşturmak için şifreleme ilkelolarak bilinen algoritmalar ve uygulamaların bir birleşimini kullanabilirsiniz. Aşağıdaki tabloda şifreleme ilkelleri ve kullanımları listelenebilmelidir.

|Kriptografik ilkel|Kullanım|
|-----------------------------|---------|
|Gizli anahtar şifrelemesi (simetrik şifreleme)|Üçüncü şahıslar tarafından okunmasını engellemek için veriler üzerinde bir dönüşüm gerçekleştirir. Bu tür şifreleme, verileri şifrelemek ve şifresini çözmek için tek bir paylaşılan gizli anahtar kullanır.|
|Ortak anahtar şifrelemesi (asimetrik şifreleme)|Üçüncü şahıslar tarafından okunmasını engellemek için veriler üzerinde bir dönüşüm gerçekleştirir. Bu tür şifreleme, verileri şifrelemek ve şifresini çözmek için ortak/özel anahtar çiftini kullanır.|
|Şifreleme imzalama|Bu tarafa özgü bir dijital imza oluşturarak verilerin belirli bir partiden kaynaklandığını doğrulamaya yardımcı olur. Bu işlem karma işlevleri de kullanır.|
|Şifreleme karmaları|Verileri herhangi bir uzunluktan sabit uzunlukta bayt sırasına göre eşler. Haşiyeler istatistiksel olarak benzersizdir; farklı bir iki bayt dizisi aynı değere karma olmaz.|

## <a name="secret-key-encryption"></a>Gizli Anahtar Şifrelemesi

Gizli anahtar şifreleme algoritmaları, verileri şifrelemek ve çözmek için tek bir gizli anahtar kullanır. Anahtarıyetkisiz aracılar tarafından erişimden korumanız gerekir, çünkü anahtara sahip olan herhangi bir taraf, verilerinizi şifrelemek veya kendi verilerini şifrelemek için kullanabilir ve bu anahtarın sizden kaynaklandığını iddia edebilir.

Aynı anahtar şifreleme ve şifre çözme için kullanıldığından, gizli anahtar şifrelemesi de simetrik şifreleme olarak adlandırılır. Gizli anahtar şifreleme algoritmaları çok hızlıdır (ortak anahtar algoritmalarıyla karşılaştırıldığında) ve büyük veri akışları üzerinde şifreleme dönüşümleri gerçekleştirmek için uygundur. RSA gibi asimetrik şifreleme algoritmaları matematiksel olarak ne kadar veriyi şifreleyebilirler. Simetrik şifreleme algoritmaları genellikle bu sorunları yok.

Bir anda bir veri bloğunu şifrelemek için blok şifresi adı verilen bir gizli anahtar algoritması türü kullanılır. Veri Şifreleme Standardı (DES), TripleDES ve Advanced Encryption Standard (AES) gibi blok şifreleri, *n* bayt giriş bloğunu şifreli baytlardan oluşan bir çıkış bloğuna dönüştürün. Bir bayt dizisini şifrelemek veya şifresini çözmek istiyorsanız, bunu engelleme yle yapmanız gerekir. *n* küçük olduğundan (DES ve TripleDES için 8 bayt; 16 bayt [varsayılan], 24 bayt veya AES için 32 bayt), *n'den* büyük veri değerlerinin bir defada bir blok şifrelenilmesi gerekir. *N'den* küçük olan veri değerlerinin işlenmesi için *n'ye* genişletilmesi gerekir.

Blok şifresinin basit bir biçimine elektronik kod kitabı (ECB) modu denir. Ecb modu güvenli olarak kabul edilmez, çünkü ilk düz metin bloğunu başlatmak için bir başlatma vektörü kullanmaz. Belirli bir gizli anahtar *k*için, bir başlatma vektörü kullanmayan basit bir blok şifresi, aynı giriş bloğunu düz metin bloğunu şifrelemek için aynı çıkış bloğunu şifreler. Bu nedenle, giriş düz metin akışınızda yinelenen bloklar varsa, çıktı şifreleme metni akışınızda yinelenen bloklar olacaktır. Bu yinelenen çıktı blokları, yetkisiz kullanıcıları, kullanılmış olabilecek algoritmaları ve olası saldırı modlarını kullanan zayıf şifrelemeye karşı uyarır. Bu nedenle ECB şifreleme modu analize ve nihayetinde önemli keşiflere karşı oldukça savunmasızdır.

Taban sınıf kitaplığında sağlanan blok şifreleme sınıfları, isterseniz bu varsayılanı değiştirebilirsiniz, ancak şifreleme bloğu zincirleme (CBC) adı verilen varsayılan zincirleme modu kullanır.

CBC şifreleri, ilk düz metin bloğunu şifrelemek için bir başlatma vektörü (IV) kullanarak ECB şifreleriyle ilişkili sorunların üstesinden gelir. Sonraki her düz metin bloğu, şifrelenmeden`XOR`önce önceki şifreleme bloğuyla bitwise özel OR ( ) işleminden geçer. Bu nedenle, her şifreleme metni bloğu önceki tüm bloklar bağlıdır. Bu sistem kullanıldığında, yetkisiz bir kullanıcı tarafından bilinen ortak ileti üstbilgisi, bir anahtarı tersine mühendislikle tasarlamak için kullanılamaz.

CBC şifresi ile şifrelenmiş verileri tehlikeye atmanın bir yolu, mümkün olan her anahtarda kapsamlı bir arama yapmaktır. Şifreleme gerçekleştirmek için kullanılan anahtarın boyutuna bağlı olarak, bu tür bir arama en hızlı bilgisayarları bile kullanarak çok zaman alır ve bu nedenle olanaksızdır. Daha büyük anahtar boyutlarını çözmek daha zordur. Şifreleme, bir düşmanın şifrelenmiş verileri almayı teorik olarak imkansız hale getirmese de, bunu yapmanın maliyetini yükseltir. Yalnızca birkaç gün için anlamlı olan verileri almak için kapsamlı bir arama yapmak üç ay sürerse, kapsamlı arama yöntemi pratik değildir.

Gizli anahtar şifrelemesinin dezavantajı, iki tarafın bir anahtar ve IV üzerinde anlaştığını ve değerlerini ilettiğini varsayıyor olmasıdır. IV bir sır olarak kabul edilmez ve mesaj ile düz metin olarak iletilebilir. Ancak, anahtar yetkisiz kullanıcılardan gizli tutulmalıdır. Bu sorunlar nedeniyle, gizli anahtar şifrelemegenellikle anahtar ve IV değerlerini özel olarak iletmek için ortak anahtar şifrelemesi ile birlikte kullanılır.

Gamze ve Bob'un güvenli olmayan bir kanal üzerinden iletişim kurmak isteyen iki taraf olduğunu varsayarsak, gizli anahtar şifrelemesini aşağıdaki gibi kullanabilirler: Gamze ve Bob belirli bir algoritmayı (örneğin AES, örneğin) belirli bir anahtar ve IV ile kullanmayı kabul ederler. Alice bir ileti oluşturur ve iletiyi göndermek için bir ağ akışı (belki de adlandırılmış bir kanal veya ağ e-postası) oluşturur. Sonra, anahtarı ve IV'u kullanarak metni şifreler ve intranet üzerinden Bob'a şifrelenmiş mesajı ve IV'u gönderir. Bob şifrelenmiş metni alır ve IV kullanarak şifresini çözer ve daha önce anahtar üzerinde anlaşmış. İleti ele geçirilirse, anahtardan anlamadıkları için ele geçirici orijinal iletiyi kurtaramaz. Bu senaryoda, yalnızca anahtar gizli kalmalıdır. Gerçek bir dünya senaryosunda, Gamze veya Bob gizli bir anahtar oluşturur ve gizli (simetrik) anahtarı diğer tarafa aktarmak için ortak anahtar (asimetrik) şifreleme kullanır. Ortak anahtar şifrelemesi hakkında daha fazla bilgi için bir sonraki bölüme bakın.

.NET Framework, gizli anahtar şifreleme algoritmalarını uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.AesManaged>(.NET Framework 3.5'te sunulmuştur).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1>(Bu teknik olarak gizli anahtar algoritmasıdır, çünkü gizli bir anahtarla birlikte bir şifreleme karma işlevi kullanılarak hesaplanan ileti kimlik doğrulama kodunu temsil eder. Bu konunun ilerleyen saatlerinde [Karma Değerler'e](#hash-values)bakın.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

## <a name="public-key-encryption"></a>Ortak Anahtar Şifreleme

Ortak anahtar şifrelemesi, yetkisiz kullanıcılardan gizli tutulması gereken özel bir anahtar ve herkese açık hale getirilebilen bir ortak anahtar kullanır. Ortak anahtar ve özel anahtar matematiksel olarak birbirine bağlıdır; ortak anahtarla şifrelenen veriler yalnızca özel anahtarla çözülebilir ve özel anahtarla imzalanan veriler yalnızca ortak anahtarla doğrulanabilir. Ortak anahtar herkes tarafından kullanılabilir hale getirilebilir; özel anahtarın koruyucuya gönderilmek üzere verileri şifrelemek için kullanılır. Verileri şifrelemek için bir anahtar gerektiğinden, verilerin şifresini çözmek için başka bir anahtar gerektiğinden, genel anahtar şifreleme algoritmaları asimetrik algoritmalar olarak da bilinir. Temel bir şifreleme kuralı anahtarın yeniden kullanılmasını yasaklar ve her iki anahtar da her iletişim oturumu için benzersiz olmalıdır. Ancak, uygulamada, asimetrik tuşları genellikle uzun ömürlüdür.

İki taraf (Gamze ve Gamze) ortak anahtar şifrelemesini aşağıdaki gibi kullanabilir: İlk olarak, Gamze ortak/özel anahtar çifti oluşturur. Bob, Alice'e şifreli bir mesaj göndermek isterse, ondan ortak anahtarını ister. Gamze, Genel Anahtarını güvenli olmayan bir ağ üzerinden Bob'a gönderir ve Bob bu anahtarı bir iletiyi şifrelemek için kullanır. Bob şifrelenmiş iletiyi Alice'e gönderir ve özel anahtarını kullanarak şifresini çözer. Bob, Genel Ağ gibi güvenli olmayan bir kanal üzerinden Gamze'nin anahtarını aldıysa, Bob ortadaki adam saldırısına açıktır. Bu nedenle, Bob'un Gamze ile ortak anahtarının doğru bir kopyasına sahip olduğunu doğrulaması gerekir.

Alice'in ortak anahtarının iletimi sırasında yetkisiz bir ajan anahtarı yakalamış olabilir. Ayrıca, aynı aracı Bob'dan gelen şifreli iletiyi ele geçirebilirsiniz. Ancak, aracı ortak anahtarla iletiyi çözemez. İletinin şifresi yalnızca Alice'in aktarılmayan özel anahtarıyla çözülebilir. Gamze, ortak anahtarı olan herkes iletiyi şifreleyebileceğinden, Gamze'ye gelen bir yanıt iletisini şifrelemek için özel anahtarını kullanmaz. Gamze, Bob'a bir ileti göndermek isterse, Bob'dan ortak anahtarını ister ve bu ortak anahtarı kullanarak iletisini şifreler. Bob daha sonra ilişkili özel anahtarını kullanarak iletinin şifresini çözer.

Bu senaryoda, Gamze ve Bob gizli (simetrik) bir anahtar aktarmak ve oturumlarının geri kalanı için gizli anahtar şifrelemesi kullanmak için ortak anahtar (asimetrik) şifreleme kullanır.

Aşağıdaki liste, ortak anahtar ve gizli anahtar şifreleme algoritmaları arasında karşılaştırmalar sunar:

- Ortak anahtar şifreleme algoritmaları sabit arabellek boyutu kullanırken, gizli anahtar şifreleme algoritmaları değişken uzunlukta arabellek kullanır.

- Yalnızca küçük miktarda veri şifrelenebileceğinden, ortak anahtar algoritmaları verileri gizli anahtar algoritmalarının çözebileceği şekilde akışlara zincirlemek için kullanılamaz. Bu nedenle, asimetrik işlemler simetrik işlemlerle aynı akış modelini kullanmaz.

- Ortak anahtar şifrelemesi, gizli anahtar şifrelemesinden çok daha büyük bir anahtar alanına (anahtar için olası değerler aralığına) sahiptir. Bu nedenle, public-key şifreleme mümkün olan her anahtarı denemek kapsamlı saldırılara daha az duyarlıdır.

- Gönderenin kimliğini doğrulamak için bir yol olması koşuluyla, güvenli olması gerekmedığından, ortak anahtarların dağıtılması kolaydır.

- Bazı ortak anahtar algoritmaları (RSA ve DSA gibi, ancak Diffie-Hellman değil) veri gönderenin kimliğini doğrulamak için dijital imzalar oluşturmak için kullanılabilir.

- Ortak anahtar algoritmaları gizli anahtar algoritmalarıyla karşılaştırıldığında çok yavaşdır ve büyük miktarda veriyi şifrelemek için tasarlanmaz. Ortak anahtar algoritmaları yalnızca çok küçük miktarda veri aktarmak için yararlıdır. Genellikle, ortak anahtar şifreleme bir anahtar ve IV gizli anahtar algoritması tarafından kullanılmak üzere şifrelemek için kullanılır. Anahtar ve IV aktarıldıktan sonra, oturumun geri kalanı için gizli anahtar şifrelemesi kullanılır.

.NET Framework, ortak anahtar şifreleme algoritmalarını uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman>(taban sınıf)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey>(taban sınıf)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction>(taban sınıf)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA hem şifreleme hem de imzalamaya izin verir, ancak DSA yalnızca imzalama için kullanılabilir ve Diffie-Hellman yalnızca anahtar oluşturma için kullanılabilir. Genel olarak, ortak anahtar algoritmaları özel anahtar algoritmalarına göre kullanımlarında daha sınırlıdır.

## <a name="digital-signatures"></a>Dijital İmzalar

Ortak anahtar algoritmaları dijital imzaoluşturmak için de kullanılabilir. Dijital imzalar gönderenin kimliğini doğrular (gönderenin ortak anahtarına güveniyorsanız) ve verilerin bütünlüğünükorumaya yardımcı olur. Alice tarafından oluşturulan ortak bir anahtarı kullanarak, Alice'in verilerinin alıcısı, dijital imzayı Alice'in verileriyle ve Alice'in ortak anahtarıyla karşılaştırarak Alice'in gönderdiğini doğrulayabilir.

Bir iletiyi dijital olarak imzalamak için ortak anahtar şifrelemesini kullanmak için, Gamze önce ileti özeti oluşturmak için iletiye karma algoritma uygular. İleti özeti, verilerin kompakt ve benzersiz bir temsilidir. Alice daha sonra kişisel imzasını oluşturmak için ileti özetini özel anahtarıyla şifreler. İletiyi ve imzayı aldıktan sonra, Bob ileti özetini kurtarmak için Gamze'nin ortak anahtarını kullanarak imzanın şifresini çözer ve Alice'in kullandığı karma algoritmayı kullanarak iletiyi karma olarak ele verir. Bob'un hesaplamasını sağlayan ileti, Gamze'den alınan ileti özetiyle tam olarak eşleşirse, Bob iletinin özel anahtarın sahibinden geldiğine ve verilerin değiştirilmediğinden emin olur. Bob, Alice'in özel anahtarın sahibi olduğuna güvenirse mesajın Alice'ten geldiğini bilir.

> [!NOTE]
> Gönderenin ortak anahtarı yaygın bir bilgi olduğundan ve genellikle dijital imza biçimine dahil olduğundan, imza herkes tarafından doğrulanabilir. Bu yöntem iletinin gizliliğini korumaz; İletinin gizli olması için, iletinin de şifrelenmiş olması gerekir.

.NET Framework, dijital imza algoritmalarını uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa>(taban sınıf)

- <xref:System.Security.Cryptography.ECDsaCng>

## <a name="hash-values"></a>Karma Değerler

Karma algoritmalar, rasgele bir uzunluğun ikili değerlerini, karma değerler olarak bilinen sabit uzunluktaki daha küçük ikili değerlerle eşler. Karma değer, bir veri parçasının sayısal gösterimidir. Düz metin bir paragraf karma ve paragrafın bile bir harfi değiştirirseniz, sonraki bir karma farklı bir değer üretecektir. Karma şifreleme olarak güçlüyse, değeri önemli ölçüde değişecektir. Örneğin, bir iletinin tek bir biti değiştirilirse, güçlü bir karma işlev yüzde 50'ye göre farklı bir çıktı üretebilir. Birçok giriş değeri aynı çıktı değerine karma olabilir. Ancak, aynı değere karma iki farklı giriş bulmak hesaplama açısından olanaksızdır.

İki taraf (Gamze ve Gamze) ileti bütünlüğünü sağlamak için karma işlevi kullanabilir. İletilerini imzalamak için bir karma algoritma seçerler. Alice bir ileti yazar ve sonra seçili algoritmayı kullanarak bu iletinin bir karma oluşturur. Daha sonra aşağıdaki yöntemlerden birini izleyeceklerdi:

- Gamze düz metin iletisini ve hashed iletiyi (dijital imza) Bob'a gönderir. Bob iletiyi alır ve haşlar ve karma değerini Alice'ten aldığı karma değerle karşılaştırır. Karma değerler aynıysa, ileti değiştirilmemiştir. Değerler aynı değilse, ileti Alice yazdıktan sonra değiştirilmiştir.

  Ne yazık ki, bu yöntem gönderenin orijinalliğini belirlemez. Herkes Alice'in kimliğine bürünebilir ve Bob'a mesaj gönderebilir. İletilerini imzalamak için aynı karma algoritmayı kullanabilirler ve Bob'un belirleyebileceği tek şey iletinin imzasıyla eşleştiğini belirleyebilir. Bu, ortadaki adam saldırısının bir şekli. Daha fazla bilgi için bkz: [Şifreleme Yeni Nesil (CNG) Güvenli İletişim Örneği.](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100))

- Gamze, güvenli olmayan bir genel kanal üzerinden Bob'a düz metin iletisi gönderir. O güvenli bir özel kanal üzerinden Bob için hashed mesajı gönderir. Bob düz metin iletisini alır, karma yı karşeyilaştırır ve karma ile özel olarak değiştirilen karma ile karşılaştırır. Eğer haşiyeler eşleşirse, Bob iki şey bilir:

  - İleti değiştirilmemiş.

  - İletiyi gönderen (Gamze) gerçektir.

  Bu sistemin çalışması için Alice'in orijinal karma değerini Bob dışındaki tüm taraflardan saklaması gerekir.

- Gamze, güvenli olmayan bir genel kanal üzerinden Bob'a düz metin iletisi gönderir ve hashed iletiyi genel olarak görüntülenebilir Web sitesine yerleştirir.

  Bu yöntem, herkesin karma değerini değiştirmesini engelleyerek iletinin kurcalanmasını önler. İleti ve karma herkes tarafından okunabilir olsa da, karma değeri yalnızca Alice tarafından değiştirilebilir. Alice'i taklit etmek isteyen bir saldırgan, Alice'in Web sitesine erişim gerektirir.

Önceki yöntemlerin hiçbiri, birinin Alice'in iletilerini okumasını engellemez, çünkü bunlar düz metin olarak iletilir. Tam güvenlik genellikle dijital imza (ileti imzalama) ve şifreleme gerektirir.

.NET Framework karma algoritmaları uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Tüm Güvenli Karma Algoritması (SHA), Message Digest 5 (MD5) ve RIPEMD-160 algoritmalarının HMAC varyantları.

- Tüm SHA algoritmalarının CryptoServiceProvider uygulamaları (yönetilen kod paketleyicileri).

- Tüm MD5 ve SHA algoritmalarının Şifreleme Yeni Nesil (CNG) uygulamaları.

> [!NOTE]
> MD5 tasarım kusurları 1996 yılında keşfedildi ve bunun yerine SHA-1 önerildi. 2004 yılında ek kusurlar keşfedildi ve MD5 algoritması artık güvenli olarak kabul edilmiştir. SHA-1 algoritması da güvensiz olduğu tespit edilmiştir ve SHA-2 şimdi bunun yerine tavsiye edilir.

## <a name="random-number-generation"></a>Rastgele Sayı Oluşturma

Rasgele sayı oluşturma birçok şifreleme işleminin ayrılmaz bir parçasıdır. Örneğin, şifreleme anahtarlarının çoğaltılabilmesi mümkün olmayan şekilde mümkün olduğunca rasgele olması gerekir. Kriptografik rasgele sayı üreteçleri hesaplamaaçısından mümkün olmayan bir olasılık ile tahmin etmek için bir yarısından daha iyi bir çıkış üretmek gerekir. Bu nedenle, bir sonraki çıktı bitini tahmin etme yöntemi rasgele tahminden daha iyi performans göstermemelidir. .NET Framework'deki sınıflar şifreleme anahtarları oluşturmak için rasgele sayı üreteçleri kullanır.

Sınıf <xref:System.Security.Cryptography.RNGCryptoServiceProvider> rasgele bir sayı üreteç algoritması bir uygulamadır.

## <a name="clickonce-manifests"></a>ClickOnce Manifestoları

.NET Framework 3.5'te, aşağıdaki şifreleme sınıfları [ClickOnce teknolojisini](/visualstudio/deployment/clickonce-security-and-deployment)kullanarak dağıtılan uygulamalar için bildirim imzaları hakkında bilgi edinmenizi ve doğrulamanızı sağlar:

- Sınıf, <xref:System.Security.Cryptography.ManifestSignatureInformation> yöntemini <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> aşırı yüklemeler kullandığınızda bir bildirim imzası hakkında bilgi alır.

- Doğrulamaiçin <xref:System.Security.ManifestKinds> hangi bildirimleri belirtecek numaralandırmayı kullanabilirsiniz. Doğrulamanın sonucu numaralandırma değerlerinden <xref:System.Security.Cryptography.SignatureVerificationResult> biridir.

- Sınıf, <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> doğrulanmış imzaların <xref:System.Security.Cryptography.ManifestSignatureInformation> nesnelerinin salt okunur koleksiyonunu sağlar.

 Buna ek olarak, aşağıdaki sınıflar belirli imza bilgileri sağlar:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation>bir bildirim için güçlü ad imza bilgilerini tutar.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation>bir bildirim için Authenticode imza bilgilerini temsil eder.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation>Authenticode imzasıüzerindeki zaman damgası hakkında bilgi içerir.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus>Authenticode imzasının güvenilir olup olmadığını denetlemenin basit bir yolunu sağlar.

## <a name="suite-b-support"></a>Suite B Desteği

.NET Framework 3.5, Ulusal Güvenlik Ajansı (NSA) tarafından yayınlanan Suite B şifreleme algoritmaları kümesini destekler. Suite B hakkında daha fazla bilgi için [NSA Suite B Şifreleme Bilgi Formu'na](https://www.nsa.gov/what-we-do/information-assurance/)bakın.

Aşağıdaki algoritmalar dahildir:

- Şifreleme için 128, 192 ve 256 bit anahtar boyutlarına sahip Gelişmiş Şifreleme Standardı (AES) algoritması.

- Güvenli Hash Algoritmaları SHA-1, SHA-256, SHA-384 ve SHA-512 karma için. (Son üç genellikle birlikte gruplanır ve SHA-2 olarak adlandırılır.)

- Eliptik Eğri Dijital İmza Algoritması (ECDSA), 256-bit, 384-bit ve 521-bit prime moduli eğrileri kullanarak imzalama. NSA belgeleri özellikle bu eğrileri tanımlar ve bunlara P-256, P-384 ve P-521 adını veririm. Bu algoritma <xref:System.Security.Cryptography.ECDsaCng> sınıf tarafından sağlanır. Özel bir anahtarla imzalamanızı ve imzayı ortak bir anahtarla doğrulamanızı sağlar.

- Eliptik Eğri Diffie-Hellman (ECDH) algoritması, anahtar değişimi ve gizli anlaşma için 256-bit, 384-bit ve 521-bit prime moduli eğrileri kullanarak. Bu algoritma <xref:System.Security.Cryptography.ECDiffieHellmanCng> sınıf tarafından sağlanır.

Federal Bilgi İşlem Standardı (FIPS) AES, SHA-256, SHA-384 ve SHA-512 uygulamalarının onaylı uygulamaları için yönetilen <xref:System.Security.Cryptography.AesCryptoServiceProvider> <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>kod <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>ambalajları yeni , , ve <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> sınıflarmevcuttur.

## <a name="cryptography-next-generation-cng-classes"></a>Kriptografi Yeni Nesil (CNG) Sınıfları

Şifreleme Yeni Nesil (CNG) sınıfları, yerel CNG işlevleri etrafında yönetilen bir sarıcı sağlar. (CNG CryptoAPI'nin yerini aldı.) Bu sınıfların isimlerinin bir parçası olarak "Cng" vardır. CNG sarıcı sınıflarının merkezinde, CNG tuşlarının depolanması ve kullanımı özetleyen <xref:System.Security.Cryptography.CngKey> anahtar kapsayıcı sınıfı yer almaktadır. Bu sınıf, bir anahtar çiftini veya ortak anahtarı güvenli bir şekilde saklamanızı ve basit bir dize adı kullanarak ona başvurmanızı sağlar. Eliptik eğri tabanlı <xref:System.Security.Cryptography.ECDsaCng> imza sınıfı <xref:System.Security.Cryptography.ECDiffieHellmanCng> ve şifreleme <xref:System.Security.Cryptography.CngKey> sınıfı nesneleri kullanabilir.

Sınıf, <xref:System.Security.Cryptography.CngKey> anahtarları açma, oluşturma, silme ve dışa aktarma dahil olmak üzere çeşitli ek işlemler için kullanılır. Ayrıca, yerel işlevleri doğrudan ararken kullanılacak temel anahtar koluna erişim sağlar.

.NET Framework 3.5, aşağıdakiler gibi çeşitli destekleyici CNG sınıflarını da içerir:

- <xref:System.Security.Cryptography.CngProvider>önemli bir depolama sağlayıcısı tutar.

- <xref:System.Security.Cryptography.CngAlgorithm>cng algoritması tutar.

- <xref:System.Security.Cryptography.CngProperty>sık kullanılan anahtar özelliklerini korur.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Şifreleme Modeli](../../../docs/standard/security/cryptography-model.md)|Temel sınıf kitaplığında şifrelemenin nasıl uygulandığını açıklar.|
|[İzlenecek Yol: Şifreleme Uygulaması Oluşturma](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Temel şifreleme ve şifre çözme görevlerini gösterir.|
|[Şifreleme Sınıflarını Yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Algoritma adlarının şifreleme sınıflarıyla nasıl eşlenebildiğini ve nesne tanımlayıcılarını şifreleme algoritmasıyla nasıl eşlenineceğimi açıklar.|
