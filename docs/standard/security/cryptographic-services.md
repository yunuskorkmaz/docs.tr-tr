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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa05fe1e170a0285df73d179ef39db6301059ac8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490954"
---
# <a name="cryptographic-services"></a>Şifreleme Hizmetleri

<a name="top"></a> Ortak ağlara Internet gibi varlıklar arasında güvenli iletişim bir yol sağlamaz. Böyle ağlar üzerinden iletişimi için okuma veya hatta yetkisiz üçüncü taraflarca değiştirilebilir saldırılara açıktır. Şifreleme, görüntülenmekte olan verilerin korunmasına yardımcı olur, veri değiştirilmiş ve aksi takdirde güvenli kanal iletişimi için güvenli bir yol sağlanır olup olmadığını algılamak için yöntemler sağlar. Örneğin, veri bir şifreleme algoritması kullanılarak şifrelenmiş, şifrelenmiş bir durum gönderilmesini ve daha sonra hedeflenen bir şirket tarafından şifresi. Bir üçüncü taraf, şifrelenmiş veriler durdurur, çözmek zor olacaktır.

.NET Framework'teki sınıflarda <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı sizin için birçok şifreleme ayrıntılarını yönetme. Diğerleri yalnızca yönetilen uygulamalar bazı sarmalayıcıları yönetilmeyen Microsoft Şifreleme API'si (CryptoAPI) bağlıdır. Bu sınıfların kullanılacak şifreleme konusunda uzman olmanız gerekmez. Algoritma sınıfları şifreleme birini yeni bir örneğini oluşturduğunuzda, kullanım kolaylığı için otomatik olarak oluşturulan anahtarları olan ve varsayılan olarak güvenli ve mümkün olduğunca güvenli özellikleridir.

Bu genel bir özeti ClickOnce bildirimlerini, Suite B ve .NET Framework 3. 5 ' tanıtılan şifreleme yeni nesil (CNG) desteği gibi .NET Framework tarafından desteklenen uygulamalar ve şifreleme yöntemleri sağlar.

Bu genel bakış aşağıdaki bölümleri içerir:

- [Şifreleme temelleri](#primitives)

- [Gizli anahtar şifreleme](#secret_key)

- [Ortak anahtar şifreleme](#public_key)

- [Dijital imzalar](#digital_signatures)

- [Karma değerleri](#hash_values)

- [Rastgele sayı oluşturma](#random_numbers)

- [ClickOnce bildirimlerini](#clickonce)

- [Suite B desteği](#suite_b)

- [İlgili Konular](#related_topics)

Ek şifreleme ve hakkında bilgi için Microsoft Hizmetleri, bileşenler ve şifreleme güvenlik uygulamalarınıza eklemenize olanak sağlayan araçları, Win32 ve COM geliştirme, bu belgede güvenlik bölümüne bakın.

<a name="primitives"></a>

## <a name="cryptographic-primitives"></a>Şifreleme temelleri

Şifreleme kullanıldığı tipik bir durumda, iki taraf (Alice ve Bob), güvenli bir kanal üzerinden iletişim kurar. Alice ve Bob iletişimin dinleniyor olması herkes tarafından anlaşılmaz kalmasını istiyorsunuz. Ayrıca, uzak konumlarda Alice ve Bob olduğundan, Alice Filiz Bob ' aldığı bilgileri herkes tarafından aktarım sırasında değiştirilmediğinden emin emin olmanız gerekir. Ayrıca, o bilgi gerçekten ndan Bob bürünülüyor birisi ve Bob gelmelerini emin olmanız gerekir.

Aşağıdaki hedeflere ulaşmak için kullanılan bir şifreleme:

- Gizlilik: Bir kullanıcının kimliği veya veri okunmaya karşı korumaya yardımcı olmak için.

- Veri bütünlüğü: Değiştirilmesini verilerini korumaya yardımcı olmak için.

- Kimlik doğrulaması: Bu verileri emin olmak için belirli bir taraftan kaynaklanır.

- İnkar: Belirli bir taraf bir mesajı gönderdik reddetmesini önlemek için.

Bu hedeflere ulaşmak için bir şifreleme düzeni oluşturma algoritmalarını ve şifreleme temel olarak bilinen yöntemler bir birleşimini kullanabilirsiniz. Aşağıdaki tabloda şifreleme temelleri ve kullanımları listeler.

|Şifreleme temel|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|-----------------------------|---------|
|Gizli anahtar şifreleme (simetrik şifreleme)|Üçüncü taraflarca okuma kalmasını sağlamak için veriler üzerinde dönüşüm gerçekleştirir. Paylaşılan tek bir gizli anahtar şifreleme ve verilerin şifresini çözmek için bu tür şifrelemeyi kullanır.|
|Ortak anahtar şifreleme (asimetrik şifreleme)|Üçüncü taraflarca okuma kalmasını sağlamak için veriler üzerinde dönüşüm gerçekleştirir. Bu tür bir şifreleme, şifrelemek ve verilerin şifresini çözmek için bir ortak/özel anahtar çifti kullanır.|
|Şifreleme imzası|Yardımcı olur, bu taraf için benzersiz olan bir dijital imza oluşturarak veri belirli bir taraftan kaynağının olduğunu doğrulayın. Bu işlem, ayrıca karma işlevlerini kullanır.|
|Şifreleme karmalarını|Herhangi bir uzunluktaki verileri bir sabit uzunluklu Bayt dizisine eşler. Karma değerleri istatistiksel olarak benzersiz, farklı bir iki baytlık diziyi aynı değere karma değil.|

[Başa dön](#top)

<a name="secret_key"></a>

## <a name="secret-key-encryption"></a>Gizli anahtar şifreleme

Gizli anahtar şifreleme algoritmaları, şifreleme ve verilerin şifresini çözmek için tek bir gizli anahtar kullanın. Anahtara sahip herhangi bir tarafa verilerinizin şifresini çözmesine veya sizden kaynaklanan beyanda kendi verilerini şifrelemek için kullanabileceğiniz yetkisiz Aracılar tarafından erişim anahtarı güvenlik altına almanız gerekir.

Şifreleme ve şifre çözme için aynı anahtar kullanılır çünkü gizli anahtar şifreleme da simetrik şifreleme adlandırılır. Gizli anahtar şifreleme algoritmalarını (ortak anahtar algoritmaları ile karşılaştırıldığında) çok hızlıdır ve üzerinde büyük veri akışlarını şifreleme dönüştürmelerine gerçekleştirmek için uygundur. Asimetrik şifreleme algoritmaları gibi RSA matematiksel olarak bunlar içinde ne kadar veri şifreleyebilirsiniz sınırlıdır. Simetrik şifreleme algoritmaları genellikle bu sorunları yok.

Gizli anahtar algoritma adı verilen bir blok şifreleme türünü bir kerede bir veri bloğu şifrelemek için kullanılır. Veri Şifreleme Standardı (DES gibi), TripleDES, blok şifreleme ve Gelişmiş Şifreleme Standardı (AES) şifreleme açısından bir giriş bloğunu dönüştürme *n* bir çıktı bloğuna şifrelenmiş bayt bayt. Şifreleme veya şifrelerini çözme bayt dizisi istiyorsanız, bunu blok blok sahip. Çünkü *n* küçük (DES ve TripleDES; için 8 bayt 16 bayt [Varsayılan], 24 bayt veya 32 bayt AES için), büyük veri değeri *n* aynı anda bir blok şifrelenmesi gerekir. Daha küçük olan veri değerleri *n* için genişletilmesi gerekir *n* işlenebilmesi için.

Basit bir blok şifreleme biçimini elektronik kod çizelgesi (ECB) modu olarak adlandırılır. Bir başlatma vektörü ilk düz metin bloğu başlatmak için kullanmadığından ECB modu güvenli olarak kabul edilmez. Belirli bir gizli anahtarın için *k*, bir başlatma vektörü kullanmayan basit bir blok şifreleme aynı düz metin giriş bloğunu aynı çıktı bloğuna şifreler şifreler. Bu nedenle, yinelenen bloğu giriş düz metin akışınız varsa, çıkış ciphertext akışınız yinelenen bloğu olacaktır. Zayıf şifreleme için uyarı yetkisiz kullanıcıların kullanılan çalışan algoritmalar bu yinelenen bir çıkış blokları ve olası saldırı modları. ECB şifreleme modu, bu nedenle analiz oldukça savunmasız durumdadır ve bulma, anahtar.

İsterseniz bu varsayılan değiştirebilirsiniz ancak Şifre blok zincirleme (CBC) adlı modu zincirleme varsayılan bir temel sınıf kitaplığı'nda sağlanan blok şifreleme sınıflarını kullanın.

Düz metin ilk bloğu şifrelemek için bir başlatma vektörü (IV) kullanarak ECB şifrelemeleri ile ilgili sorunlar CBC şifrelemeleri aşın. Bir bit düzeyinde dışlamalı OR sonraki her düz metin bloğu uğradığında (`XOR`) şifreli önce önceki ciphertext bloğunu işlemi. Bu nedenle, tüm önceki blok ciphertext blokların bağlıdır. Bu sistem, yetkisiz bir kullanıcı tarafından bilinen kullanılan, ortak ileti üstbilgileri olduğunda olamaz ters mühendislik için kullanılan bir anahtar.

Bir CBC şifreleme ile şifrelenir verilerini tehlikeye yollarından biri, her olası anahtarının kapsamlı bir arama gerçekleştirmektir. Şifreleme gerçekleştirmek için kullanılan anahtar boyutuna bağlı olarak bu tür bir arama hızlı bilgisayarları bile kullanarak çok zaman alır ve bu nedenle uygulanamaz. Daha büyük bir anahtar boyutu şifre çözme daha zordur. Şifreleme, teorik olarak şifrelenmiş verileri almak bir saldırgan imkansız hale getirmez olsa da, bunu yapmanın maliyeti yükseltin. Ayrıntılı arama yöntemi, yalnızca birkaç gün için anlamlı olan verileri almak için kapsamlı bir arama gerçekleştirmek için üç ay aldığı durumlarda zordur.

Gizli anahtar şifreleme bir dezavantajı, iki taraf bir anahtar ve IV anlaşılan ve bunların değerlerini iletilen varsayar olmasıdır. IV'nin gizli olarak kabul edilmez ve düz metin iletisi iletilebilir. Ancak, anahtar yetkisiz kullanıcılardan gizli tutulmalıdır. Bu sorunları nedeniyle gizli anahtar şifreleme genellikle birlikte ortak anahtar şifreleme anahtarı ve IV'yi değerlerini birbiriyle iletişim kurmasına olanak kullanılır.

Alice ve Bob güvenli bir kanal üzerinden iletişim kurmak isteyen iki tarafın olduğu varsayılırsa, bunlar gizli anahtar şifreleme gibi kullanabilirsiniz: Alice ve Bob belirli bir algoritma (örneğin, AES) bir özel anahtar ve IV ile kullanmayı kabul etmiş olursunuz. Alice, bir ileti oluşturur ve ileti göndermek, ağ akışı (belki de bir adlandırılmış kanal veya ağ e-posta) oluşturur. Ardından, Filiz anahtar ve IV kullanarak metni şifreler ve IV ve şifreli ileti Bob için intranet üzerinden gönderir. Bob, şifrelenmiş metni alır ve IV kullanarak şifresini çözer ve daha önce anahtarı üzerinde anlaşılan. İletim yakalanırsa kendisinin anahtar bilmediğinden, dinleyiciyi özgün iletinin kurtaramazsınız. Bu senaryoda, yalnızca anahtar gizli kalmalıdır. Bir gerçek dünya senaryosunda, Alice veya Bob gizli bir anahtar oluşturur ve gizli (simetrik) anahtar diğer tarafa devretmek için (asimetrik) ortak anahtar şifrelemesi kullanır. Ortak anahtar şifrelemesi hakkında daha fazla bilgi için sonraki bölüme bakın.

.NET Framework, gizli anahtar şifreleme algoritmalarını uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.AesManaged> (.NET Framework 3. 5 ' sunulmuştur).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1> (Bir gizli anahtar ile birleştirilmiş bir şifreleme karması işlevi kullanılarak hesaplanır ileti kimlik doğrulama kodu temsil ettiğinden teknik bir gizli anahtar algoritması budur. Bkz: [karma değerlerini](#hash_values), bu konunun devamındaki.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

[Başa dön](#top)

<a name="public_key"></a>

## <a name="public-key-encryption"></a>Ortak anahtar şifreleme

Ortak anahtar şifrelemesi yetkisiz kullanıcılardan gizli tutulması gereken özel bir anahtar ve herkesin genel hale getirilebilir bir ortak anahtar kullanır. Ortak anahtar ve özel anahtarı matematiksel olarak bağlı; yalnızca özel anahtara sahip ortak anahtar ile şifrelenen verilerin şifresi çözülemez ve özel anahtarla imzalanır veri yalnızca ortak anahtar ile doğrulanabilir. Ortak anahtar herkes için kullanılabilir hale getirilebilir; özel anahtarın keeper için gönderilecek verileri şifrelemek için kullanılır. Ortak anahtar şifreleme algoritmaları, verileri şifrelemek için bir anahtar gereklidir ve verilerin şifresini çözmek için başka bir anahtar gereklidir çünkü Asimetrik algoritmalar olarak da bilinen olurlar. Temel bir şifreleme kural anahtar yeniden engeller ve her iki anahtarı her iletişim oturumu için benzersiz olmalıdır. Ancak, uygulamada, asimetrik anahtarlar genellikle uzun ömürlü değildir.

İki taraf (Alice ve Bob) ortak anahtar şifreleme gibi kullanabilirsiniz: İlk olarak, Esra'nın bir ortak/özel anahtar çifti oluşturur. Bob Alice şifreli ileti göndermek isterse, kendisi kendisi için kendi ortak anahtar ister. Alice Bob kendi ortak anahtarı güvenli bir ağ üzerinden gönderir ve Bob, iletiyi şifrelemek için bu anahtarı kullanır. Bob için Alice şifreli ileti gönderir ve Filiz, kendi özel anahtarı kullanarak çözer. Bob, genel bir ağı gibi güvenli bir kanal üzerinden Alice'in anahtar aldıysanız Bob bir adam-de-ortadaki adam saldırısı için açıktır. Bu nedenle, Bob Alice ile kendi ortak anahtarı doğru bir kopyasını olduğunu doğrulamalısınız.

Alice ortak anahtar aktarım sırasında yetkisiz bir aracı anahtarı ıntercept. Ayrıca, aynı aracı Bob şifreli ileti ıntercept. Ancak, aracı ileti ortak anahtarla şifresi çözülemiyor. İleti hangi değil iletilen yalnızca Alice'in özel anahtarla şifresi çözülebilir. Ortak anahtarı olan herkes iletinin şifresini çünkü Alice kendi özel anahtarı bir yanıt iletisi BOB'a şifrelemek için kullanır. Alice, Bob için yeniden bir ileti göndermek isterse, Filiz Bob ister kendi ortak anahtarı ve o ortak anahtarı kullanarak kendi ileti şifreler. Bob, ardından kendi ilişkili özel anahtarı kullanarak mesajın şifresini çözer.

Bu senaryoda, Alice ve Bob, gizli (simetrik) anahtar aktarmak ve oturumunun kalanı için gizli anahtar şifrelemesi'ni kullanmak için ortak anahtar (asimetrik) şifrelemesini kullanın.

Aşağıdaki listede, ortak anahtar ve gizli anahtar şifreleme algoritmaları arasında karşılaştırma sunar:

- Gizli anahtar şifreleme algoritmaları değişken uzunluklu arabellek kullanmasa ortak anahtar şifreleme algoritmaları, bir sabit arabellek boyutu kullanır.

- Yalnızca küçük miktarlarda veri şifrelenebilir ortak anahtar algoritmaları zinciri verilerine birlikte akışlara gizli anahtar algoritmaları kullanabileceği şekilde kullanılamaz. Bu nedenle, asimetrik işlemleri aynı akış modelinde simetrik işlem olarak kullanmayın.

- Ortak anahtar şifreleme gizli anahtar şifreleme değerinden daha büyük bir anahtar alanı (anahtar için olası değerler aralığı) sahiptir. Bu nedenle, ortak anahtar şifreleme mümkün olan her anahtar kapsamlı saldırılar için daha az saldırılara açıktır.

- Gönderenin kimliğini doğrulamak için bir yol var olması koşuluyla korunması, sahip oldukları değil dağıtmak ortak anahtarları kolaydır.

- Bazı ortak anahtar algoritmaları (örneğin, RSA ve DSA, ancak Diffie-Hellman), veri gönderen kimliğini doğrulamak için dijital imzalar oluşturmak için kullanılabilir.

- Ortak anahtar algoritmaları gizli anahtar algoritmaları ile karşılaştırıldığında çok yavaş ve büyük miktarlarda verileri şifrelemek için tasarlanmamıştır. Ortak anahtar algoritmaları, yalnızca çok küçük miktarlarda veri aktarmak için kullanışlıdır. Genellikle, ortak anahtar şifreleme anahtarı ve gizli anahtar algoritması tarafından kullanılacak IV şifrelemek için kullanılır. Anahtar ve IV aktarıldıktan sonra gizli anahtar şifreleme oturumunun kalanı için kullanılır.

.NET Framework, ortak anahtar şifreleme algoritmalarını uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman> (temel sınıfı)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey> (temel sınıfı)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction> (temel sınıfı)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA şifreleme ve imzalama sağlar ancak DSA, yalnızca imzalamak için kullanılabilir ve Diffie-Hellman anahtar oluşturma için kullanılabilir. Genel olarak, ortak anahtar algoritmaları özel anahtar algoritmaları daha fazla kullanımları içinde sınırlıdır.

[Başa dön](#top)

<a name="digital_signatures"></a>

## <a name="digital-signatures"></a>Dijital imzalar

Ortak anahtar algoritmaları, dijital imzalar oluşturmak için de kullanılabilir. Dijital imzalar (gönderenin ortak anahtar güveniyorsanız) bir gönderen Kimliği kimlik doğrulaması ve veri bütünlüğü korunmasına yardımcı olabilirsiniz. Alice tarafından oluşturulmuş bir ortak anahtar kullanarak, Alice'in veri alıcısı Alice, Alice'in verilere ve Alice'in ortak anahtar dijital imza karşılaştırarak gönderdiğini doğrulayabilirsiniz.

Bir iletinin dijital olarak imzalamak için ortak anahtar şifrelemesi'ni kullanmak için Alice ilk iletinin ileti özeti oluşturmak için bir karma algoritması uygular. İleti özeti veri kompakt ve benzersiz bir gösterimidir. Alice, ardından kendi kişisel imza oluşturmak için kendi özel anahtara sahip ileti özeti şifreler. İmza ve ileti alındıktan sonra Alice kullanılan karma algoritması kullanarak ileti karmaları ve ileti özeti kurtarmak için Alice'in ortak anahtar kullanarak imzayı Bob şifresini çözer. Bob'ı tam olarak hesaplar ileti özeti Alice alınan ileti özeti eşleşirse, Bob iletinin özel anahtarı kaynağı geldiğini ve veriler değiştirilmemiş sağlanmıştır. Bob Alice özel anahtarın kaynağı olduğunu güveniyorsa, o ileti Alice geldiğini bilir.

> [!NOTE]
> Gönderenin ortak anahtar genel bilgi ve genellikle dijital imza biçiminde dahil olduğundan bir imza herkes tarafından doğrulanabilir. Bu yöntem, ileti gizliliği saklamaz; İletinin gizli olması de şifrelenmelidir.

.NET Framework, dijital imza algoritmalarını uygulayan aşağıdaki sınıfları sağlar:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa> (temel sınıfı)

- <xref:System.Security.Cryptography.ECDsaCng>

 [Başa dön](#top)

<a name="hash_values"></a>

## <a name="hash-values"></a>Karma değerleri

Karma algoritmaları küçük ikili değerler karma değerleri olarak bilinen bir sabit uzunlukta bir rastgele uzunlukta ikili değerler eşleyin. Bir karma değer, bir veri parçasını sayısal bir gösterimidir. Düz metin paragrafı karma paragrafın bile bir harf değiştirirseniz, bir sonraki karma farklı bir değer oluşturur. Değerini, şifreleme açısından güçlü bir karma ise, önemli ölçüde değişir. Örneğin, bir ileti tek bir bit değiştirilirse, güçlü bir karma işlevi yüzde 50 farklı bir çıktı üretebilir. Birçok giriş değerleri için aynı çıkış değeri karma. Ancak, iki farklı girişe aynı değere karmayı bulmak için uyuşmazlığa neden olur.

İki taraf (Alice ve Bob), ileti bütünlüğünü sağlamak için bir karma işlevi kullanabilirsiniz. Bunlar, iletileri imzalamak için bir karma algoritması seçersiniz. Alice bir ileti yazın ve ardından söz konusu iletinin bir karma seçili algoritmasını kullanarak oluşturun. Bunlar daha sonra aşağıdaki yöntemlerden birini izlemeniz gerekir:

- Alice, Bob için düz metin iletisi ve karma iletisi (dijital imza) gönderir. Bob alır ve ileti karma hale getirir ve he Alice alınan karma değeri, karma değerini karşılaştırır. Karma değerleri aynıysa, ileti değiştirilmiş değil. Değerler aynı değilse, ileti Alice yazdığı sonra değiştirildi.

    Ne yazık ki, bu yöntem, Gönderenin özgünlüğünü oluşturmaz. Herkes Alice kimliğine bürünmek ve bir ileti göndermek. Bob belirleyebilirsiniz olan ileti imzası eşleştiğini ve bunların iletiyi imzalamak için aynı karma algoritması kullanabilirsiniz. Bu bir adam-de-ortadaki adam saldırısı, bir biçimidir. Daha fazla bilgi için [şifreleme yeni nesil (CNG) güvenli iletişim örnek](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alice, Bob için genel güvenli bir kanal üzerinden düz metin iletisi gönderir. Filiz karma ileti güvenli özel bir kanal üzerinden gönderir. Bob düz metin iletisini alır, bu karma hale getirir ve karmayı özel olarak alışverişi olur karma karşılaştırır. Karmalar eşleşiyorsa, iki şeyi Bob bilir:

    - İleti değiştirilemez.

    - (Alice) iletiyi gönderenin gerçektir.

    Bu sistem çalışmaya Alice, Bob dışındaki tüm tarafları kendi özgün karma değeri gizlemeniz gerekir.

- Alice, güvenli olmayan genel bir kanal üzerinden düz metin ileti gönderir ve herkes tarafından izlenen her Web sitesi üzerinde karma ileti yerleştirir.

    Bu yöntem, karma değerini değiştirmesini herkes engelleyerek ileti oynama engeller. İleti ve karma herkes tarafından okunabilir ancak karma değeri yalnızca Alice tarafından değiştirilebilir. Alice bürünülecek isteyen bir saldırganın Alice'in Web sitesine erişimi olması gerekir.

Düz metin olarak aktarılan olduğundan Alice'in iletileri okumasını önceki yöntemlerden hiçbiri birisi engeller. Tam güvenlik genellikle (İleti imzalama) dijital imzalar ve şifreleme gerektirir.

.NET Framework, karma algoritmaları uygulayan aşağıdaki sınıflar sağlar:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Tüm güvenli karma algoritması (SHA) ve İleti Özeti 5 (MD5) RIPEMD 160 algoritmaları HMAC çeşitleri.

- Tüm SHA algoritmaları CryptoServiceProvider uygulamaları (yönetilen kod sarmalayıcıları).

- Şifreleme yeni nesil (CNG) uygulamaları tüm MD5 ve SHA algoritmaları.

> [!NOTE]
> MD5 tasarım standartlarımızı 1996 yılında bulunan ve bunun yerine SHA-1 önerilir. 2004 ' ek standartlarımızı bulunan ve MD5 algoritması artık güvenli olarak kabul edilir. SHA-1 algoritmasını da güvenli olmasını bulundu ve SHA-2 yerine artık önerilir.

[Başa dön](#top)

<a name="random_numbers"></a>

## <a name="random-number-generation"></a>Rastgele sayı oluşturma

Rastgele sayı oluşturma birçok şifreleme işlemleri için tam sayı. Örneğin, şifreleme anahtarlarını, böylece bunları yeniden uygulanamaz olarak rastgele olmanız gerekir. Şifreleme rastgele sayı üreteçlerinin ile daha iyi bir olasılığını tahmin etmek için uyuşmazlığa neden çıktı oluşturmak gerekir yarısı. Bu nedenle, sonraki çıktı bit tahmin etme, herhangi bir yöntemi rasgele tahmin daha iyi gerçekleştirmemelisiniz. .NET Framework içindeki sınıflar, rastgele sayı üreteçlerinin şifreleme anahtarları oluşturmak için kullanın.

<xref:System.Security.Cryptography.RNGCryptoServiceProvider> Bir rasgele sayı üreteci algoritması uygulaması bir sınıftır.

[Başa dön](#top)

<a name="clickonce"></a>

## <a name="clickonce-manifests"></a>ClickOnce Manifests

İçinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], aşağıdaki şifreleme sınıflarını almak ve bildirim imzalar kullanılarak dağıtılan uygulamalar için bilgi doğrulayın izin [ClickOnce teknoloji](/visualstudio/deployment/clickonce-security-and-deployment):

- <xref:System.Security.Cryptography.ManifestSignatureInformation> Sınıfı kullandığınızda bir bildirim imza hakkında bilgi edinir, <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> yöntemi aşırı yüklemeleri.

- Kullanabileceğiniz <xref:System.Security.ManifestKinds> doğrulamak için hangi bildirimleri belirtmek için sabit listesi. Doğrulama sonucu biridir <xref:System.Security.Cryptography.SignatureVerificationResult> sabit listesi değerleri.

- <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> SAX salt okunur koleksiyonu <xref:System.Security.Cryptography.ManifestSignatureInformation> doğrulanmış imzaları nesneleri.

 Ayrıca, aşağıdaki sınıflar, belirli bir imza bilgileri sağlayın:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation> Bir bildirimi için tanımlayıcı ad imzası bilgileri tutar.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> bir bildirim Authenticode imza bilgilerini temsil eder.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> Authenticode imzası zaman damgasını hakkında bilgi içerir.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus> Authenticode imzası güvenilir olup olmadığını denetlemek için basit bir yol sağlar.

[Başa dön](#top)

<a name="suite_b"></a>

## <a name="suite-b-support"></a>Suite B desteği

[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Suite B şifreleme algoritmaları Ulusal Güvenlik Agency (NSA) tarafından yayınlanan kümesini destekler. Suite B hakkında daha fazla bilgi için bkz: [NSA Suite B şifreleme bilgi sayfası](https://www.nsa.gov/what-we-do/information-assurance/).

Aşağıdaki algoritmaları dahil edilir:

- Gelişmiş Şifreleme Standardı (AES) algoritması, anahtar boyutları 128, 192 ve 256 bit şifreleme için.

- Karma algoritma SHA-1, SHA-256, SHA-384 ve SHA-512 karma oluşturma için güvenli hale getirin. (Son üç genellikle gruplanan ve SHA-2 ' başvurulan.)

- Eliptik Eğri Dijital imza algoritması (imzalama için 256 bit, 384 bit ve 521 bit prime moduli, eğriler kullanarak ECDSA). NSA belgeleri özellikle bu eğrileri tanımlar ve onları çağıran p-256, p-384 ve p-521. Bu algoritma tarafından sağlanan <xref:System.Security.Cryptography.ECDsaCng> sınıfı. Özel bir anahtar ile oturum açma ve ortak anahtara sahip imzasını olanak tanır.

- Gizli sözleşmesi ve anahtar değişimi için 256 bit, 384 bit ve 521 bit prime moduli, eğriler kullanarak Eliptik Eğri Diffie-Hellman (ECDH) algoritması. Bu algoritma tarafından sağlanan <xref:System.Security.Cryptography.ECDiffieHellmanCng> sınıfı.

Yönetilen kod sarmalayıcıları için Federal Bilgi İşleme Standardı (FIPS) sertifikalı AES, SHA-256, SHA-384 ve SHA-512 uygulamaları uygulamalarıdır yeni kullanılabilir <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, ve <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> sınıflar.

[Başa dön](#top)

<a name="cng"></a>

## <a name="cryptography-next-generation-cng-classes"></a>Şifreleme İleri nesil (CNG) sınıfları

Şifreleme yeni nesil (CNG) sınıfları, yerel CNG işlevleri çevresinde yönetilen sarmalayıcı sağlar. (CNG CryptoAPI yerini alır.) Bu sınıfların adlarını bir parçası olarak "Cng" vardır. CNG sarmalayıcı sınıflar için Central, <xref:System.Security.Cryptography.CngKey> anahtar, CNG anahtarları kullanma ve depolama soyutlar kapsayıcı sınıfı. Bu sınıf, bir anahtar çifti ya da ortak anahtarı güvenli bir şekilde saklayın ve basit bir dize adı kullanarak başvurduğu sağlar. Eliptik Eğri tabanlı <xref:System.Security.Cryptography.ECDsaCng> imza sınıfı ve <xref:System.Security.Cryptography.ECDiffieHellmanCng> şifreleme sınıfı kullanabilir <xref:System.Security.Cryptography.CngKey> nesneleri.

<xref:System.Security.Cryptography.CngKey> Sınıfı, çeşitli açma, oluşturma, silme ve anahtarlarının dışa aktarılması gibi ek işlemleri için kullanılır. Ayrıca, doğrudan yerel işlevleri çağırma sırasında kullanılacak temel alınan anahtar tanıtıcısı erişim sağlar.

[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Destek CNG sınıfları, aşağıdaki gibi çeşitli de içerir:

- <xref:System.Security.Cryptography.CngProvider> anahtar depolama sağlayıcısı tutar.

- <xref:System.Security.Cryptography.CngAlgorithm> CNG algoritması kullanır.

- <xref:System.Security.Cryptography.CngProperty> Sık kullanılan anahtar özellikleri tutar.

[Başa dön](#top)

<a name="related_topics"></a>

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Şifreleme Modeli](../../../docs/standard/security/cryptography-model.md)|Şifreleme temel sınıf kitaplığı'nda nasıl uygulandığı açıklanmaktadır.|
|[İzlenecek yol: Şifreleme uygulaması oluşturma](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Temel şifreleme ve şifre çözme görevlerini gösterir.|
|[Şifreleme Sınıflarını Yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Algoritma adlarını şifreleme sınıflarıyla eşleme ve bir şifreleme algoritması için nesne tanımlayıcılarını eşleme açıklar.|
