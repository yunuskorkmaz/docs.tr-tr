---
title: Şifreleme Hizmetleri
description: .NET tarafından desteklenen şifreleme yöntemlerine ve uygulamalarına genel bakış.
ms.date: 07/14/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryption [.NET]
- private keys
- MAC algorithms
- cryptographic algorithms
- private keys, overview
- encryption [.NET]
- security [.NET], encryption
- cryptographic services
- symmetric cryptographic algorithms
- hash
- message authentication codes
- derived class inheritance
- cryptography [.NET], about
- random number generation
ms.assetid: f96284bc-7b73-44b5-ac59-fac613ad09f8
ms.openlocfilehash: 4cd4e493e0e7d159b2749dac78b9a560e20fd75c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557027"
---
# <a name="cryptographic-services"></a>Şifreleme Hizmetleri

Internet gibi genel ağlar, varlıklar arasında güvenli bir iletişim yöntemi sağlamaz. Bu tür ağlarla iletişim, yetkisiz üçüncü taraflar tarafından okunmakta ve hatta değiştirilmezler. Şifreleme, verilerin görüntülenmesini önlemeye yardımcı olur, verilerin değiştirilip değiştirilmediğini algılamaya yönelik yollar sağlar ve aksi takdirde güvenli olmayan kanallar üzerinden güvenli bir iletişim sağlanmasına yardımcı olur. Örneğin, veriler bir şifreleme algoritması kullanılarak şifrelenebilir, şifreli bir durumda iletilir ve daha sonra hedeflenen tarafın şifresini çözülür. Üçüncü bir taraf şifrelenmiş verileri karşılar, şifre çöz zor olur.

.NET ' te, <xref:System.Security.Cryptography> ad alanındaki sınıflar sizin için şifreleme ayrıntılarının çoğunu yönetir. Bazıları yalnızca işletim sistemi uygulamaları için sarmalayıcılardır, diğerleri ise yalnızca yönetilen uygulamalardır. Bu sınıfları kullanmak için şifrede uzman olmanız gerekmez. Şifreleme algoritması sınıflarından birinin yeni bir örneğini oluşturduğunuzda, anahtarlar kullanım kolaylığı için otomatik olarak oluşturulur ve varsayılan özellikler mümkün olduğunca güvenli ve güvenlidir.

Bu genel bakış, ClickOnce bildirimleri de dahil olmak üzere .NET tarafından desteklenen şifreleme yöntemleri ve uygulamaları Özeti sağlar.

## <a name="cryptographic-primitives"></a>Şifreleme temelleri

Şifrelemenin kullanıldığı tipik bir durumda, iki taraf (Gamze ve Bob) güvenli olmayan bir kanaldan iletişim kurar. Gamze ve Bob, iletişiminin dinlenebilir herkes tarafından erişilebilir olmasını sağlamak istiyor. Ayrıca, Gamze ve Bob uzak konumlarda olduğundan, Gamze 'den aldığı bilgilerin iletim sırasında herhangi bir kişi tarafından değiştirilmediğinden emin olmalıdır. Ayrıca, bilgilerin gerçekten Bob 'dan geldiğinden ve Bob 'u taklit eden birisinden kaynaklanmadığından emin olması gerekir.

Şifreleme, aşağıdaki hedeflere ulaşmak için kullanılır:

- Gizlilik: bir kullanıcının kimliğini veya verilerinin okunmasını sağlamaya yardımcı olmak Için.

- Veri bütünlüğü: verilerin değiştirilmesini korumanıza yardımcı olmak Için.

- Kimlik doğrulaması: verilerin belirli bir taraftan kaynaklanmadığını doğrulamak Için.

- Red olmayan: belirli bir tarafın bir ileti gönderdiğini reddetmekten kaçınmak Için.

Bu hedeflere ulaşmak için şifreleme düzeni oluşturmak üzere şifreleme temel işlemleri olarak bilinen algoritmaların ve uygulamaların bir bileşimini kullanabilirsiniz. Aşağıdaki tabloda şifreleme temelleri ve kullanımları listelenmektedir.

|Şifreleme temel|Kullanın|
|-----------------------------|---------|
|Gizli anahtar şifreleme (simetrik şifreleme)|Verilerin üçüncü taraflar tarafından okunmasını önlemek için bir dönüştürme gerçekleştirir. Bu tür bir şifreleme, verileri şifrelemek ve şifrelerini çözmek için tek bir paylaşılan gizli anahtar kullanır.|
|Ortak anahtar şifrelemesi (asimetrik şifreleme)|Verilerin üçüncü taraflar tarafından okunmasını önlemek için bir dönüştürme gerçekleştirir. Bu tür bir şifreleme, verileri şifrelemek ve şifrelerini çözmek için ortak/özel anahtar çifti kullanır.|
|Şifreleme imzalama|Bu tarafa özgü bir dijital imza oluşturarak verilerin belirli bir taraftan kaynaklandığını doğrulamaya yardımcı olur. Bu işlem karma işlevleri de kullanır.|
|Şifreleme karmaları|Herhangi bir uzunluktaki verileri sabit uzunluklu bir bayt dizisine eşler. Karmalar istatistiksel olarak benzersizdir; farklı bir iki baytlık dizi aynı değere karma olmayacak.|

## <a name="secret-key-encryption"></a>Gizli anahtar şifreleme

Gizli anahtar şifreleme algoritmaları, verileri şifrelemek ve şifrelerini çözmek için tek bir gizli anahtar kullanır. Anahtara sahip olan herhangi bir taraf verilerinizin şifresini çözmek ya da kendi verilerini şifrelemek veya kendi verilerini şifrelemek için bu anahtarı kullanabilir.

Şifreleme ve şifre çözme için aynı anahtar kullanıldığından, gizli anahtar şifrelemesi de simetrik şifreleme olarak adlandırılır. Gizli anahtar şifreleme algoritmaları çok hızlıdır (ortak anahtar algoritmalarıyla karşılaştırılır) ve büyük veri akışlarında şifreleme dönüştürmeleri gerçekleştirmek için uygundur. RSA gibi asimetrik şifreleme algoritmaları, şifreleyebilecekleri veri miktarına göre sınırlı matematiksel olarak sınırlanmıştır. Simetrik şifreleme algoritmaları genellikle bu sorunlara sahip değildir.

Tek seferde bir veri bloğunu şifrelemek için bir blok şifresi olarak adlandırılan bir gizli anahtar algoritması türü kullanılır. Veri şifreleme standardı (DES), TripleDES ve Gelişmiş Şifreleme Standardı (AES) gibi şifrelemeleri blok olarak, *n* baytlık bir giriş bloğunu şifreli baytların çıkış bloğuna dönüştürür. Bir bayt dizisini şifrelemek veya şifresini çözmek istiyorsanız blok olarak blok yapmanız gerekir. *N* , des ve TripleDES için 8 bayt; 16 bayt [varsayılan], 24 bayt veya AES için 32 bayt) olduğundan, *n* 'den büyük veri değerlerinin tek seferde tek bir blok şifrelenebilmesi gerekir. *N* ' den küçük veri değerleri işlenmek üzere *n* olarak genişletilmelidir.

Bir basit blok şifresi formu elektronik codebook (ECB) modu olarak adlandırılır. ECB modu, ilk düz metin bloğunu başlatmak için bir başlatma vektörü kullanmadığı için güvenli olarak kabul edilmez. Belirli bir gizli anahtar *k*anahtarı için, bir başlatma vektörü kullanmayan basit bir blok şifresi, aynı düz metin giriş bloğunu şifreli olmayan aynı çıkış bloğuna şifreler. Bu nedenle, giriş düz metin akışındaki yinelenen bloklarınız varsa, çıktı şifreli metin akışındaki yinelenen bloklara sahip olursunuz. Bu yinelenen çıktı, yetkisiz kullanıcıların, kullanıma açık olabilecek algoritmaları ve olası saldırı modlarını kullanan zayıf şifrelemeye karşı uyarır. Bu nedenle ECB şifre modu Analize ve son olarak anahtar bulmaya açıktır.

Temel sınıf kitaplığında verilen blok şifre sınıfları, şifreleme bloğu zinciri (CBC) adlı varsayılan bir zincirleme modu kullanır, ancak isterseniz bu varsayılan değeri değiştirebilirsiniz.

CBC şifresi, düz metin bloğunu şifrelemek için bir başlatma vektörü (IV) kullanarak ECB şifrelemeleri ile ilişkili sorunları ortadan kaldırmak. Düz düz metin blokları, şifrelenmeden önce önceki şifreli olmayan bir bit düzeyinde dışlamalı veya ( `XOR` ) işleme geçer. Bu nedenle, her bir şifreli blok, önceki tüm bloklara bağımlıdır. Bu sistem kullanıldığında, yetkisiz bir kullanıcı tarafından bilinen ortak ileti üstbilgileri, bir anahtara ters mühendislik uygulamak için kullanılamaz.

Bir CBC şifresi ile şifrelenen verileri tehlikeye almanın bir yolu, olası her anahtar için kapsamlı bir arama gerçekleştirmelidir. Şifrelemeyi gerçekleştirmek için kullanılan anahtarın boyutuna bağlı olarak, bu tür bir arama en hızlı bilgisayarlar bile çok zaman alır ve bu nedenle uygulanabilir olur. Daha büyük anahtar boyutlarının şifre daha kolay olması daha zordur. Şifreleme, şifreli verileri almak üzere bir saldırgan için teorik olarak olanaksız hale gelse de, bunu yapmanın maliyetini yükseltir. Yalnızca birkaç gün için anlamlı olan verileri almak üzere üç ay sürüyorsa, ayrıntılı arama yöntemi pratik değildir.

Gizli anahtar şifrelemenin dezavantajı, iki tarafın bir anahtar ve IV üzerinde anlaştığı ve değerlerini iletildiği bir dezavantajdır. IV gizli kabul edilmez ve iletiyle birlikte düz metin olarak iletilebilir. Ancak, anahtarın yetkisiz kullanıcılardan gizli tutulması gerekir. Bu sorunlar nedeniyle, gizli anahtar şifrelemesi genellikle anahtar ve IV değerlerini özel olarak iletmek için ortak anahtar şifrelemesi ile birlikte kullanılır.

Gamze ve Bob 'un güvenli olmayan bir kanal üzerinden iletişim kurmak isteyen iki taraf olduğu varsayılırsa, gizli anahtar şifrelemesini şu şekilde kullanabilir: Gamze ve Bob, belirli bir anahtar ve IV ile belirli bir algoritmayı (örneğin, AES) kullanmayı kabul eder. Çiğdem bir ileti oluşturur ve iletiyi göndermek için bir ağ akışı (Belki de adlandırılmış kanal veya ağ e-postası) oluşturur. Ardından, anahtarı ve IV 'yi kullanarak metni şifreler ve Intranet üzerinden emre 'ye şifreli iletiyi ve IV 'yi gönderir. Bob şifreli metni alır ve IV 'yi kullanarak ve daha önce anahtar üzerinde anlaşarak şifresini çözer. İletim yakalandıktan sonra, bu anahtarı bilmez çünkü bu, anahtarı bilmez. Bu senaryoda, yalnızca anahtarın gizli kalması gerekir. Gerçek bir Dünya senaryosunda, Gamze veya Bob bir gizli anahtar oluşturur ve gizli (simetrik) anahtarı diğer tarafa aktarmak için ortak anahtar (asimetrik) şifrelemeyi kullanır. Ortak anahtar şifreleme hakkında daha fazla bilgi için sonraki bölüme bakın.

.NET, gizli anahtar şifreleme algoritmaları uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.Aes>

- <xref:System.Security.Cryptography.HMACSHA256>, <xref:System.Security.Cryptography.HMACSHA384> ve <xref:System.Security.Cryptography.HMACSHA512> . (Bu teknik açıdan gizli anahtar algoritmalarda, gizli anahtar ile Birleşik bir şifreleme karması işlevi kullanılarak hesaplanan ileti kimlik doğrulama kodları temsil etmektedir. Bu makalenin ilerleyen kısımlarında bulunan [karma değerleri](#hash-values)bölümüne bakın.)

## <a name="public-key-encryption"></a>Ortak anahtar şifrelemesi

Ortak anahtar şifrelemesi, yetkisiz kullanıcılardan ve herkese açık hale getirilen bir ortak anahtardan gizli tutulması gereken özel bir anahtar kullanır. Ortak anahtar ve özel anahtar, matematiksel olarak bağlanır; ortak anahtarla şifrelenen verilerin şifresi yalnızca özel anahtarla çözülebilecek ve özel anahtarla imzalanmış veriler yalnızca ortak anahtarla doğrulanabilir. Ortak anahtar herkes tarafından kullanılabilir hale getirilebilir; Bu, özel anahtarın adına gönderilecek verileri şifrelemek için kullanılır. Verileri şifrelemek için bir anahtar gerekli olduğundan ve verilerin şifresini çözmek için başka bir anahtar gerektiğinden, ortak anahtar şifreleme algoritmaları Asimetrik algoritmalar olarak da bilinir. Temel bir şifreleme kuralı, anahtar yeniden kullanımını yasaklar ve her iki anahtar da her iletişim oturumu için benzersiz olmalıdır. Ancak, pratikte asimetrik anahtarlar genellikle uzun ömürlü.

İki taraf (Gamze ve Bob) ortak anahtar şifrelemeyi şu şekilde kullanabilir: Ilk olarak, Gamze ortak/özel anahtar çifti oluşturur. Bob, Gamze 'yi şifreli bir ileti göndermek isterse kendi ortak anahtarını ister. Gamze, Bob 'un ortak anahtarını güvenli olmayan bir ağ üzerinden gönderir ve Bob bu anahtarı bir iletiyi şifrelemek için kullanır. Bob, şifreli iletiyi çiğdem 'e gönderir ve özel anahtarını kullanarak onun şifresini çözer. Bob, bir genel ağ gibi güvenli olmayan bir kanal üzerinden gamze 'nin anahtarını aldıysa, Bob bir ortadaki adam saldırısında açıktır. Bu nedenle, Bob 'un ortak anahtarının doğru bir kopyasına sahip olduğu çiğdem ile doğrulanması gerekir.

Çiğdem 'in ortak anahtarının iletimi sırasında, yetkisiz bir aracı anahtarı engelleyebilir. Ayrıca, aynı aracı Bob 'dan şifrelenmiş iletiyi de engelleyebilir. Ancak, aracı iletinin şifresini ortak anahtarla çözemez. İleti, yalnızca gamze 'nin gönderilmemiş özel anahtarıyla şifresi çözülür. Çiğdem, ortak anahtara sahip herkes iletinin şifresini çözebileceğinden, can 'a bir yanıt iletisi şifrelemek için özel anahtarını kullanmaz. Gamze, emre 'ye bir ileti göndermek isterse, emre 'yi ortak anahtarı için sorar ve iletiyi bu ortak anahtarı kullanarak şifreler. Bob, ilişkili özel anahtarını kullanarak iletinin şifresini çözer.

Bu senaryoda, Gamze ve Bob bir gizli anahtar (simetrik) anahtar aktarmak ve oturumunun geri kalanı için gizli anahtar şifrelemeyi kullanmak için ortak anahtar (asimetrik) şifrelemeyi kullanır.

Aşağıdaki listede, ortak anahtar ve gizli anahtar şifreleme algoritmaları arasında karşılaştırmalar sunulmaktadır:

- Ortak anahtar şifreleme algoritmaları sabit bir arabellek boyutu kullanır, ancak gizli anahtar şifreleme algoritmaları değişken uzunlukta bir arabellek kullanır.

- Ortak anahtar algoritmaları, gizli anahtar algoritmalarının yanı sıra yalnızca küçük miktarlarda veri şifrelenebilmesi nedeniyle verileri akışlara eklemek için kullanılamaz. Bu nedenle, asimetrik işlemler simetrik işlemler ile aynı akış modelini kullanmaz.

- Ortak anahtar şifrelemesi, gizli anahtar şifrelemeden daha büyük bir anahtar alanı (anahtar için olası değerler aralığı) sahiptir. Bu nedenle, ortak anahtar şifrelemesi, olası her anahtarı deneyen kapsamlı saldırılara karşı daha düşüktür.

- Ortak anahtarların dağıtılması, bu kişilerin güvenli olması gerekmez, çünkü gönderenin kimliğini doğrulamak için bir başka yol vardır.

- Bazı ortak anahtar algoritmaları (RSA ve DSA gibi), veri göndericisinin kimliğini doğrulamak için dijital imzalar oluşturmak üzere kullanılabilir.

- Ortak anahtar algoritmaları gizli anahtar algoritmalarıyla karşılaştırıldığında çok yavaştır ve büyük miktarlarda verileri şifrelemek üzere tasarlanmamıştır. Ortak anahtar algoritmaları yalnızca çok az miktardaki verileri aktarmak için yararlıdır. Genellikle ortak anahtar şifrelemesi, bir anahtarı ve IV 'yi bir gizli anahtar algoritması tarafından kullanılmak üzere şifrelemek için kullanılır. Anahtar ve IV aktarıldıktan sonra, oturumun geri kalanı için gizli anahtar şifreleme kullanılır.

.NET, ortak anahtar algoritmaları uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.RSA>

- <xref:System.Security.Cryptography.ECDsa>

- <xref:System.Security.Cryptography.ECDiffieHellman>

- <xref:System.Security.Cryptography.DSA>

RSA hem şifrelemeye hem de imzalamaya izin verir, ancak DSA yalnızca imzalama için kullanılabilir. DSA, RSA olarak güvenli değildir ve RSA önerilir. Diffie-Hellman yalnızca anahtar üretimi için kullanılabilir. Genel olarak, ortak anahtar algoritmaları, kullanımları özel anahtar algoritmalarından daha sınırlıdır.

## <a name="digital-signatures"></a>Dijital İmzalar

Ortak anahtar algoritmaları, dijital imzaları biçimlendirmek için de kullanılabilir. Dijital imzalar gönderici kimliğini doğrular (gönderenin ortak anahtarına güveniyorsanız) ve verilerin bütünlüğünü korumaya yardımcı olur. Gamze tarafından oluşturulan bir ortak anahtar kullanarak, Gamze 'nin verilerinin alıcısı, dijital imzayı gamze 'nin verilerine ve Gamze 'nin ortak anahtarına göre karşılaştırarak gamze 'nin gönderdiğini doğrulayabilirler.

Bir iletiyi dijital olarak imzalamak için ortak anahtar şifrelemeyi kullanmak üzere, bir ileti özeti oluşturmak için önce çiğdem, iletiye bir karma algoritması uygular. İleti özeti, verilerin kompakt ve benzersiz bir gösterimidir. Çiğdem daha sonra kişisel imzasını oluşturmak için özel anahtarıyla birlikte ileti özetini şifreler. Can ileti ve imza alındıktan sonra, ileti özetini kurtarmak için Ayla 'nın ortak anahtarını kullanarak imzanın şifresini çözer ve iletiyi çiğdem 'in kullandığı karma algoritmayı kullanarak karma hale getirir. Bob 'un bir ileti özeti gamze 'den alınan ileti özetine tam olarak eşleşiyorsa, Bob iletinin özel anahtarın bulunduğu yerden veya verilerin değiştirilmediğinden emin olur. Emre bu çiğdem 'e güveniyorsa, iletinin gamze 'den geldiğini bilir.

> [!NOTE]
> Gönderenin ortak anahtarı ortak bilgi olduğundan ve genellikle dijital imza biçiminde yer aldığı için imza, herkes tarafından doğrulanabilir. Bu yöntem iletinin gizliliğini korumaz; iletinin gizli olması için de şifrelenmelidir.

.NET, dijital imza algoritmaları uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.RSA>

- <xref:System.Security.Cryptography.ECDsa>

- <xref:System.Security.Cryptography.DSA>

## <a name="hash-values"></a>Karma değerleri

Karma algoritmalar rastgele uzunluktaki ikili değerleri, karma değerler olarak bilinen sabit uzunlukta daha küçük ikili değerlerle eşler. Karma değeri, bir veri parçasının sayısal gösterimidir. Düz metin paragrafını ve paragrafın bir harfine eşit bir şekilde karma yaparsanız, sonraki bir karma, farklı bir değer oluşturur. Karma şifreli olarak güçlü ise, değeri önemli ölçüde değişir. Örneğin, bir iletinin tek bir biti değiştirilirse, güçlü bir karma işlevi yüzde 50 ' ye göre farklılık gösteren bir çıktı üretebilir. Birçok giriş değeri aynı çıkış değerine karma olabilir. Ancak, aynı değere karma olarak iki ayrı giriş bulmak için hesaplama yapılabilir.

İki taraf (Gamze ve Bob) ileti bütünlüğünü sağlamak için bir karma işlevi kullanabilir. İletileri imzalamak için bir karma algoritması seçer. Çiğdem bir ileti yazabilir ve ardından seçilen algoritmayı kullanarak bu iletinin karmasını oluşturur. Bunlar daha sonra aşağıdaki yöntemlerden birini izlemelidir:

- Çiğdem, can 'a düz metin iletisi ve karma ileti (dijital imza) gönderir. Bob iletiyi alır ve karma hale getirir ve karma değerini gamze 'den aldığı karma değerle karşılaştırır. Karma değerleri aynıysa ileti değiştirilmez. Değerler özdeş değilse, ileti çiğdem tarafından yazıldıktan sonra değiştirilir.

  Ne yazık ki bu yöntem, gönderenin orijinalliğini oluşturmaz. Birisi gamze 'yi taklit edebilir ve emre 'ye bir ileti gönderebilir. İletileri imzalamak için aynı karma algoritmayı kullanabilir ve tüm Bob, iletinin imzasıyla eşleşip eşleşmediğini tespit edebilir. Bu, ortadaki adam saldırısının bir biçimidir. Daha fazla bilgi için bkz. [Yeni nesil şifreleme (CNG) güvenli Iletişim örneği](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Çiğdem, güvenli olmayan bir genel kanal üzerinden emre 'ye düz metin iletisi gönderir. Karma iletiyi güvenli bir özel kanal üzerinden emre 'ye gönderir. Bob, düz metin iletisini alır, onu karma hale getirir ve karmayı özel olarak değiştirilen karmayla karşılaştırır. Karmalar eşleşiyorsa, Bob iki şeyi bilir:

  - İleti değiştirilmedi.

  - İletiyi gönderen (Gamze), gerçek.

  Bu sistemin çalışması için Çiğdem, Bob hariç tüm taraflardan orijinal karma değerini gizlemeniz gerekir.

- Çiğdem, düz metin iletisini güvenli olmayan bir genel kanal üzerinden emre 'ye gönderir ve karma iletiyi genel olarak görüntülenebilen bir Web sitesine koyar.

  Bu yöntem, herhangi bir kişinin karma değeri değiştirmesini engelleyerek iletiyi izinsiz değişikliklere engel olur. İleti ve karması herkes tarafından okunabilse de, karma değeri yalnızca gamze tarafından değiştirilebilir. Çiğdem 'i taklit etmek isteyen bir saldırgan, Çiğdem 'in Web sitesine erişim gerektirir.

Önceki yöntemlerin hiçbiri düz metin olarak aktarıldıklarından, birisinin çiğdem iletilerini okumasını engellemez. Tam güvenlik genellikle dijital imzaları (ileti imzalama) ve şifrelemeyi gerektirir.

.NET, karma algoritmaları uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.SHA256>.

- <xref:System.Security.Cryptography.SHA384>.

- <xref:System.Security.Cryptography.SHA512>.

.NET ayrıca <xref:System.Security.Cryptography.MD5> ve sağlar <xref:System.Security.Cryptography.SHA1> . Ancak MD5 ve SHA-1 algoritmalarının güvenli olmadığı algılandı ve bunun yerine SHA-2 önerilir. SHA-2 SHA256, SHA384 ve SHA512 olur içerir.

## <a name="random-number-generation"></a>Rastgele sayı oluşturma

Rastgele sayı oluşturma çok sayıda şifreleme işlemine integral. Örneğin, şifreleme anahtarlarının mümkün olduğunca rastgele olması gerekir, böylece bunları yeniden oluşturmak uygulanabilir hale gelir. Şifreleme rastgele sayı oluşturucuları, bir günden daha iyi bir olasılık ile tahmin edilmesi açısından uygun olmayan çıktıyı üretmelidir. Bu nedenle, bir sonraki çıkış bitini tahmin etmek için herhangi bir yöntem rastgele tahmin gerçekleştirmemelidir. .NET Framework sınıflar, şifreleme anahtarları oluşturmak için rastgele sayı oluşturucuları kullanır.

<xref:System.Security.Cryptography.RandomNumberGenerator>Sınıfı, rastgele sayı Oluşturucu algoritmasının bir uygulamasıdır.

## <a name="clickonce-manifests"></a>ClickOnce bildirimleri

.NET Framework 3,5 ' de, aşağıdaki şifreleme sınıfları [ClickOnce teknolojisi](/visualstudio/deployment/clickonce-security-and-deployment)kullanılarak dağıtılan uygulamalar için bildirim imzaları hakkında bilgi edinmenizi ve doğrulamanıza olanak sağlar:

- <xref:System.Security.Cryptography.ManifestSignatureInformation>Sınıfı, yöntem aşırı yüklerini kullandığınızda bir bildirim imzası hakkında bilgi edinir <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> .

- <xref:System.Security.ManifestKinds>Hangi bildirimlerin doğrulanacak olduğunu belirtmek için sabit listesini kullanabilirsiniz. Doğrulamanın sonucu, <xref:System.Security.Cryptography.SignatureVerificationResult> sabit listesi değerlerinden biridir.

- <xref:System.Security.Cryptography.ManifestSignatureInformationCollection>Sınıfı, doğrulanmış imzaların nesnelerinin salt okunurdur bir koleksiyonunu sağlar <xref:System.Security.Cryptography.ManifestSignatureInformation> .

 Ayrıca, aşağıdaki sınıflar belirli imza bilgilerini sağlar:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation>bir bildirimin tanımlayıcı ad imzası bilgilerini tutar.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation>bir bildirimin Authenticode imza bilgilerini temsil eder.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation>bir Authenticode imzasında zaman damgasıyla ilgili bilgileri içerir.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus>Authenticode imzasının güvenilir olup olmadığını denetlemek için basit bir yol sağlar.

## <a name="cryptography-next-generation-cng-classes"></a>Yeni nesil şifreleme (CNG) sınıfları

.NET Framework 3,5 ve sonraki sürümlerde, yeni nesil şifreleme (CNG) sınıfları, yerel CNG işlevlerinin etrafında yönetilen bir sarmalayıcı sağlar. (CNG, CryptoAPI 'nin yerini alır.) Bu sınıfların adlarının bir parçası olarak "CNG" vardır. CNG sarmalayıcı sınıflarına merkezi olarak <xref:System.Security.Cryptography.CngKey> , CNG anahtarlarının depolanmasını ve kullanımını soyutlayan anahtar kapsayıcı sınıfıdır. Bu sınıf, bir anahtar çiftini veya ortak anahtarı güvenli bir şekilde depolamanıza ve basit bir dize adı kullanarak buna başvurmanıza olanak sağlar. Eliptik Eğri tabanlı <xref:System.Security.Cryptography.ECDsaCng> imza sınıfı ve <xref:System.Security.Cryptography.ECDiffieHellmanCng> şifreleme sınıfı <xref:System.Security.Cryptography.CngKey> nesneleri kullanabilir.

<xref:System.Security.Cryptography.CngKey>Sınıfı, anahtarları açma, oluşturma, silme ve dışarı aktarma dahil olmak üzere çeşitli ek işlemler için kullanılır. Ayrıca, yerel işlevleri doğrudan çağırırken kullanılacak temel anahtar tanıtıcısına erişim sağlar.

.NET Framework 3,5 ayrıca aşağıdakiler gibi çeşitli destek CNG sınıfları içerir:

- <xref:System.Security.Cryptography.CngProvider>anahtar depolama sağlayıcısını korur.

- <xref:System.Security.Cryptography.CngAlgorithm>CNG algoritmasını korur.

- <xref:System.Security.Cryptography.CngProperty>sık kullanılan anahtar özelliklerini korur.

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme modeli](cryptography-model.md) -şifrelemenin temel sınıf kitaplığında nasıl uygulandığını açıklar.
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları](vulnerabilities-cbc-mode.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)
