---
title: "Şifreleme Hizmetleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cryptography [.NET Framework]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryptioin [.NET Framework]
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
caps.latest.revision: "34"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1fd0df0e12149371b3403782056982784c0ca3cd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="cryptographic-services"></a>Şifreleme Hizmetleri
<a name="top"></a>Internet gibi ortak ağlara varlıklar arasında güvenli iletişim için bir araç sağlamaz. Böyle ağlar üzerinden iletişimi okumak veya hatta yetkisiz üçüncü taraflar tarafından değiştirilebilir açıktır. Şifreleme görüntülenmesini verilerin korunmasına yardımcı olur, veri değiştirildi ve aksi durumda güvenli kanal iletişimi için güvenli bir yol sağlanır olup olmadığını algılamak için yöntemler sağlar. Örneğin, veri bir şifreleme algoritması kullanılarak şifrelenmiş, şifrelenmiş bir duruma gönderilmesini ve daha sonra hedeflenen taraf tarafından şifresi. Bir üçüncü taraf şifrelenmiş veriler kesişirse geçirilirse zor olacaktır.  
  
 .NET Framework'teki sınıflarda <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı sizin için birçok şifreleme ayrıntılarını yönetme. Başkalarının tamamen yönetilen uygulamaları durumdayken yönetilmeyen Microsoft Şifreleme API (CryptoAPI) için sarmalayıcıları bazılarıdır. Bu sınıfların kullanmak için bir uzman şifreleme olması gerekmez. Yeni bir örneğini bir şifreleme algoritması sınıfları oluşturduğunuzda, kullanım kolaylığı için otomatik olarak oluşturulur anahtarları şunlardır ve varsayılan olarak güvenli ve mümkün olduğunca güvenli özellikleridir.  
  
 ClickOnce bildirimleri, Suite B dahil olan .NET Framework tarafından desteklenen uygulamalar ve şifreleme yöntemleri doğrulanır bu genel bakış sağlar ve yeni nesil şifreleme (CNG) desteği sunmuştur [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  
  
 Bu genel bakışta aşağıdaki bölümleri içerir:  
  
-   [Şifreleme temelleri](#primitives)  
  
-   [Gizli anahtar şifreleme](#secret_key)  
  
-   [Ortak anahtar şifrelemesi](#public_key)  
  
-   [Dijital imzalar](#digital_signatures)  
  
-   [Karma değerleri](#hash_values)  
  
-   [Rastgele sayı oluşturma](#random_numbers)  
  
-   [ClickOnce bildirimleri](#clickonce)  
  
-   [Suite B desteği](#suite_b)  
  
-   [İlgili Konular](#related_topics)  
  
 Ek şifreleme hakkında ve hakkında bilgi için Microsoft Hizmetleri, bileşenleri ve uygulamalarınız için şifreleme güvenlik eklemenizi sağlayan araçlar, Win32 ve COM geliştirme, bu belgelerin güvenlik bölümüne bakın.  
  
<a name="primitives"></a>   
## <a name="cryptographic-primitives"></a>Şifreleme temelleri  
 Şifreleme kullanıldığı tipik bir durumda, iki taraf (Alice ve Bob) güvenli bir kanal üzerinden iletişim kurar. Alice ve Bob iletişimin dinleme herkes tarafından incomprehensible kalmasını sağlamak istiyorsunuz. Ayrıca, uzak konumlarda Alice ve Bob olduğundan, Alice aynen Bob aldığı bilgileri herkes tarafından iletim sırasında değiştirilmediğinden emin emin olmanız gerekir. Ayrıca, aynen bilgileri gerçekten Bob'ndan Bob bürünüyor birisi ve kaynaklandığını emin olmanız gerekir.  
  
 Şifreleme, aşağıdaki hedeflere ulaşmak için kullanılır:  
  
-   Gizlilik: kullanıcının kimliği veya veri okunmaya karşı korumaya yardımcı olmak için.  
  
-   Veri bütünlüğü: değiştirilmesini verilerinin korunmasına yardımcı olur.  
  
-   Kimlik doğrulaması: Bu verilere emin olmak için belirli bir tarafın kaynaklanır.  
  
-   İnkar: iletiye gönderilen reddetmesini belirli bir taraf önlemek için.  
  
 Bu hedeflere ulaşmak için şifreleme şeması oluşturmak için algoritmalarını ve şifreleme temel olarak bilinen yöntemler bileşimini kullanabilirsiniz. Aşağıdaki tabloda şifreleme temelleri ve kullanımları listeler.  
  
|Şifreleme ilkel|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------------------|---------|  
|Gizli anahtar şifreleme (simetrik şifreleme)|Üçüncü taraflar tarafından okunan kalmasını sağlamak için veri dönüştürme gerçekleştirir. Bu tür şifreleme paylaşılan, tek bir şifrelemek ve verilerin şifresini çözmek için gizli anahtarı kullanır.|  
|Ortak anahtar şifreleme (asimetrik şifreleme)|Üçüncü taraflar tarafından okunan kalmasını sağlamak için veri dönüştürme gerçekleştirir. Şifreleme bu tür bir genel/özel anahtar çifti şifrelemek ve verilerin şifresini çözmek için kullanır.|  
|Şifreleme imzalama|Veriler o tarafa benzersiz olan bir dijital imza oluşturarak belirli bir tarafın gelmektedir yardımcı doğrulayın. Bu işlem ayrıca karma işlevlerini kullanır.|  
|Şifreleme karmalarını|Herhangi bir uzunlukta bir verilerden sabit uzunluklu Bayt dizisine eşler. Karmaları istatistiksel olarak benzersiz; farklı bir iki bayt dizisi aynı değere karma değil.|  
  
 [Başa dön](#top)  
  
<a name="secret_key"></a>   
## <a name="secret-key-encryption"></a>Gizli anahtar şifreleme  
 Gizli anahtar şifreleme algoritmaları, şifrelemek ve verilerin şifresini çözmek için tek bir gizli anahtar kullanın. Yetkisiz Aracılar tarafından erişim anahtarından güvenli gerekir, çünkü anahtara sahip herhangi bir taraf, verilerin şifresini çözmek veya sizden kaynaklanan istenmesini kullanıcıların kendi verilerini şifrelemek için kullanabilirsiniz.  
  
 Şifreleme ve şifre çözme için aynı anahtar kullanılır çünkü gizli anahtar şifreleme da simetrik şifreleme bilinir. Gizli anahtar şifreleme algoritmalarını (ortak anahtar algoritmaları ile karşılaştırıldığında) çok hızlı ve büyük veri akışlarını üzerinde şifreleme dönüştürme gerçekleştirmek için uygundur. Asimetrik şifreleme algoritmaları RSA gibi matematiksel olarak birbiriyle ne kadar veri bunlar şifreleyebilirsiniz sınırlıdır. Simetrik şifreleme algoritması bu sorunları genellikle gerekmez.  
  
 Bir blok şifreleme adlı gizli anahtar algoritması türü, aynı anda bir veri bloğu şifrelemek için kullanılır. Veri Şifreleme Standardı (DES gibi), TripleDES, şifreleri engelleme ve Gelişmiş Şifreleme Standardı (AES) şifreleme açısından bir giriş bloğunu dönüştürme  *n*  çıkış bloğuna şifrelenmiş bayt bayt. Şifreleme veya şifrelerini çözme bayt dizisi istiyorsanız, bunu blok blok yapmanın sahip. Çünkü  *n*  küçük (DES ve TripleDES; için 8 bayt 16 bayt [Varsayılan], 24 baytı veya AES için 32 bayt), büyük veri değerleri  *n*  bir blok şifrelenmesi gerekir aynı anda. Daha küçük veri değerleri  *n*  üzere genişletilmesi zorunda  *n*  işlenebilmesi için.  
  
 Blok şifre, bir Basit form elektronik codebook (ECB) modu adı verilir. Bunu bir başlatma vektörü ilk düz metin bloğu başlatmak için kullanmadığından ECB modu güvenli olarak kabul edilmez. Belirli bir gizli anahtar için *k*, bir başlatma vektörü kullanmayan Basit Blok şifre ciphertext aynı çıktı bloğu içine düz metin aynı giriş bloğu şifreler. Bu nedenle giriş düz metin akışınızı yinelenen bloğu varsa, çıktı ciphertext akışınızı yinelenen bloğu olacaktır. Zayıf şifreleme uyarı yetkisiz kullanıcılara işe algoritmaları kullanılan bu yinelenen çıkış blokları ve saldırı olası modlarını. ECB şifreleme modu, bu nedenle analiz için oldukça savunmasızdır ve nihayetinde bulma anahtar.  
  
 Taban Sınıf Kitaplığı'nda sağlanan blok şifreleme sınıflarını istiyorsanız, bu varsayılan ayarı değiştirebilirsiniz ancak Şifre blok zincirleme (CBC), bilinen modu zincirleme varsayılan kullanın.  
  
 CBC şifrelemeleri düz metin ilk bloğu şifrelemek için bir başlatma vektörü (IV) kullanarak ECB şifrelemeleri ile ilgili sorunları gidermek. Bit düzeyinde XOR düz metin sonraki her bir bloğunda uğradığında (`XOR`) şifreli önce önceki ciphertext blok işlemi. Her ciphertext bloğu, bu nedenle tüm önceki blok bağlıdır. Bu sistem yetkisiz bir kullanıcı tarafından bilinen kullanılan, ortak ileti üstbilgilerini olduğunda olamaz ters mühendislik için kullanılan bir anahtar.  
  
 CBC şifre ile şifrelenmiş veri tehlikeye yollarından biri her olası anahtarının ayrıntılı aramasını gerçekleştirmektir. Şifreleme gerçekleştirmek için kullanılan anahtar boyutu, bağlı olarak bu tür bir arama daha hızlı bilgisayarları kullanarak çok zaman alır ve bu nedenle uygulanamaz. Daha büyük anahtar boyutları geçirilirse daha zordur. Şifreleme, şifrelenmiş verileri almak üzere bir saldırganın teorik olarak olanaksız yapmaz rağmen Bunun yapılması maliyetini yükseltin. Yalnızca birkaç gün için anlamlı olan verileri almak için kapsamlı bir arama yapmak için üç ay aldığı durumlarda kapsamlı arama yöntemi zordur.  
  
 Gizli anahtar şifreleme dezavantajı, iki taraf bir anahtar ve IV üzerinde anlaşılan ve değerlerine iletilen varsayar olmasıdır. IV gizli olarak kabul edilmez ve düz metin iletisi iletilebilir. Ancak, anahtar yetkisiz kullanıcılardan gizli tutulması gerekir. Bu sorunları nedeniyle gizli anahtar şifreleme genellikle ortak anahtar şifrelemesi ile birlikte özel olarak IV ve anahtar değerlerini iletişim kurmak için kullanılır.  
  
 Alice ve Bob güvenli bir kanal üzerinden iletişim kurmak isteyen iki taraf olduğu varsayımıyla, gizli anahtar şifreleme gibi kullanabilecekleri: Gamze ve Bob kabul IV ve bir özel anahtar ile bir belirli algoritma (örneğin, AES) kullanmak üzere. Alice bir ileti oluşturur ve ileti göndermek, ağ akışı (belki de bir adlandırılmış kanal veya ağ e-posta) oluşturur. Ardından, aynen IV ve anahtarı kullanarak metin şifreler ve şifrelenmiş ileti ve IV Bob için intranet üzerinden gönderir. Bob şifrelenmiş metni alır ve IV kullanarak şifresini çözer ve daha önce anahtar üzerinde anlaşılan. İletim yakalanırsa, kendisinin anahtar bilmediğinden dinleyiciyi özgün ileti kurtaramazsınız. Bu senaryoda, yalnızca anahtar gizli kalması gerekir. Gerçek dünya senaryosu Alice veya Bob gizli bir anahtar oluşturur ve gizli (simetrik) anahtar diğer tarafa aktarmak için ortak anahtar (asimetrik) şifreleme kullanır. Ortak anahtar şifreleme hakkında daha fazla bilgi için sonraki bölüme bakın.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Gizli anahtar şifreleme algoritmaları uygulayan aşağıdaki sınıflar sağlar:  
  
-   <xref:System.Security.Cryptography.AesManaged>(sunulan [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]).  
  
-   <xref:System.Security.Cryptography.DESCryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.HMACSHA1>(Gizli bir anahtar ile birleştirilmiş bir şifreleme karması işlevi kullanılarak hesaplanır ileti kimlik doğrulama kodu temsil eden teknik bir gizli anahtar algoritması olmasıdır. Bkz: [karma değerlerini](#hash_values), bu konunun devamındaki.)  
  
-   <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RijndaelManaged>.  
  
-   <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.  
  
 [Başa dön](#top)  
  
<a name="public_key"></a>   
## <a name="public-key-encryption"></a>Ortak anahtar şifrelemesi  
 Ortak anahtar şifrelemesi yetkisiz kullanıcılardan gizli tutulması gereken özel bir anahtar ve herkese ortak yapılabilmesi için ortak bir anahtar kullanır. Ortak anahtar ve özel anahtarı matematiksel olarak birbiriyle bağlantılı; Ortak anahtar ile şifrelenmiş veri yalnızca özel anahtarla şifresi çözülebilir ve özel anahtarı ile imzalanmış veri yalnızca ortak anahtar ile doğrulanabilir. Ortak anahtar herkes için kullanılabilir hale getirilebilir; özel anahtarı keeper için gönderilecek verileri şifrelemek için kullanılır. Ortak anahtar şifreleme algoritmaları olarak da bilinen asimetrik algoritmaları verileri şifrelemek için bir anahtar gereklidir ve başka bir anahtar verilerin şifresini çözmek için gerekli olduğu. Temel bir şifreleme kural anahtar yeniden kullanılmasını engeller ve her iki anahtarı her iletişimi oturum için benzersiz olmalıdır. Bununla birlikte, pratikte, asimetrik anahtarlar genellikle uzun süreli.  
  
 İki taraf (Alice ve Bob) kullanabilecekleri ortak anahtar şifreleme gibi: ilk olarak, bir ortak/özel anahtar çifti Alice oluşturur. Bob Alice şifreli ileti göndermek isterse, kendisi her kendi ortak anahtarı ister. Alice Bob kendi ortak anahtar güvenli olmayan bir ağ üzerinden gönderir ve Bob bir iletiyi şifrelemek için bu anahtarı kullanır. Bob Alice'e şifreli ileti gönderir ve kendisi, kendi özel anahtarı kullanarak şifresini çözer. Bob genel bir ağı gibi güvenli bir kanal üzerinden Alice'in anahtarı aldıysanız Bob man-in--middle saldırısını açıktır. Bu nedenle, Bob kendi ortak anahtar doğru bir kopyasını olduğunu Alice ile doğrulamanız gerekir.  
  
 Alice'in ortak anahtar iletim sırasında yetkisiz bir aracı anahtarı müdahale. Ayrıca, aynı aracı Bob şifrelenmiş iletiden müdahale. Ancak, aracı ileti ortak anahtarla şifresi çözülemiyor. İleti değil iletilmiş yalnızca Alice'in özel anahtarla şifresi çözülebilir. Ortak anahtar kimseyle iletinin şifresini çünkü Alice kendi özel anahtarı bir yanıt iletisi için Bob, şifrelemek için kullanmaz. Alice geri Bob için bir ileti göndermek isterse, kendisinin Bob için kendi ortak anahtar ister ve o ortak anahtarı kullanarak kendi ileti şifreler. Bob, daha sonra kendi ilişkili özel anahtarı kullanarak ileti şifresini çözer.  
  
 Bu senaryoda, gizli bir (simetrik) anahtar aktarmak ve bunların oturumunun kalanı için gizli anahtar şifrelemesi'ni kullanmak için ortak anahtar (asimetrik) şifreleme Alice ve Bob kullanın.  
  
 Aşağıdaki liste, ortak anahtar ve gizli anahtar şifreleme algoritmaları arasındaki karşılaştırmaları sunar:  
  
-   Gizli anahtar şifreleme algoritmaları değişken uzunlukta arabellek kullanmasa sabit arabellek boyutu, ortak anahtar şifreleme algoritmaları kullanır.  
  
-   Yalnızca küçük miktarda veri şifrelenebilir ortak anahtar algoritmaları zinciri verileri birlikte akışlara gizli anahtar algoritmaları olabilir, yolu kullanılamıyor. Bu nedenle, asimetrik işlemleri aynı akış modeli simetrik işlemleri olarak kullanmayın.  
  
-   Ortak anahtar şifreleme gizli anahtar şifreleme daha çok daha büyük keyspace (anahtarı için olası değerler aralığı) sahiptir. Bu nedenle, ortak anahtar şifrelemesi, her olası anahtarı deneyin kapsamlı daha az saldırılarına açık.  
  
-   Gönderenin kimliğini doğrulamak için bazı yolu var olması koşuluyla, korunması olmadığı çünkü dağıtmak ortak anahtarları kolaydır.  
  
-   Bazı ortak anahtar algoritmaları (örneğin, RSA ve DSA ancak Diffie-Hellman), veri gönderen kimliğini doğrulamak için dijital imzalar oluşturmak için kullanılabilir.  
  
-   Ortak anahtar algoritmaları çok yavaş gizli anahtar algoritmaları ile karşılaştırılan ve büyük miktarlarda verinin şifrelemek için tasarlanmamıştır. Ortak anahtar algoritmaları, yalnızca çok küçük miktarda veri aktarmak için yararlıdır. Genellikle, ortak anahtar şifreleme anahtarı ve gizli anahtar algoritması tarafından kullanılacak IV şifrelemek için kullanılır. Anahtar ve IV aktarıldıktan sonra gizli anahtar şifreleme oturumunun kalanı için kullanılır.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ortak anahtar şifreleme algoritmaları uygulayan aşağıdaki sınıflar sağlar:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellman>(temel sınıfı)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCng>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey>(temel sınıfı)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction>(temel sınıfı)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 Hem şifreleme hem de imzalama, RSA sağlar ancak DSA yalnızca imzalamak için kullanılabilir ve Diffie-Hellman anahtar oluşturma için kullanılabilir. Genel olarak, ortak anahtar algoritmaları kullanımları daha özel anahtar algoritmaları sınırlıdır.  
  
 [Başa dön](#top)  
  
<a name="digital_signatures"></a>   
## <a name="digital-signatures"></a>Dijital imzalar  
 Ortak anahtar algoritmaları, dijital imzalar oluşturmak için de kullanılabilir. Dijital imzalar (gönderenin ortak anahtar güveniyorsanız) bir gönderen Kimliği kimlik doğrulaması ve veri bütünlüğünü korunmasına yardımcı olabilirsiniz. Alice tarafından oluşturulan bir ortak anahtar kullanarak, Alice'in veri alıcı Alice, Alice'in veri ve Alice'in ortak anahtar dijital imza karşılaştırarak gönderdiğini doğrulayabilirsiniz.  
  
 Bir ileti dijital olarak imzalamak için ortak anahtar şifrelemesi kullanmak için Alice ilk ileti özeti oluşturmak için ileti için karma algoritma geçerlidir. İleti özeti, verilerin compact ve benzersiz bir gösterimidir. Alice ileti özeti sonra kendi kişisel imza oluşturmak için kendi özel anahtarla şifreler. İleti ve imza alındıktan sonra Bob Alice kullanılan aynı karma algoritmayı kullanarak ileti karmaları ve ileti özeti kurtarmak için Alice'in ortak anahtar kullanarak imzayı şifresini çözer. Bob tam olarak hesaplar ileti özeti Alice alınan ileti özeti eşleşirse, Bob gelen özel anahtar sahibi ileti ve verilerin değiştirilmediğinden emin olur. Alice özel anahtarın sahibi olduğunu Bob güveniyorsa bu durumda, kendisinin Alice gelen ileti bilir.  
  
> [!NOTE]
>  Gönderenin ortak anahtar ortak bilgi olduğundan ve dijital imza biçiminde genellikle dahil herkes tarafından imza doğrulanabilir. Bu yöntem, ileti gizliliği korumuyor; İletinin gizli olmasını da şifrelenmelidir.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Dijital imza algoritmaları uygulayan aşağıdaki sınıflar sağlar:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDsa>(temel sınıfı)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 [Başa dön](#top)  
  
<a name="hash_values"></a>   
## <a name="hash-values"></a>Karma değerleri  
 Karma algoritmaları küçük ikili değerler karma değerleri olarak bilinen bir sabit uzunlukta rastgele uzunlukta ikili değerler eşlenir. Bir karma değer veri parçası sayısal bir gösterimi ' dir. Düz metin paragrafın karma paragrafın bile bir harf değiştirirseniz, bir sonraki karma farklı bir değer oluşturur. Karma şifreleme açısından güçlü ise, değerini önemli ölçüde değiştirir. Örneğin, bir iletinin tek bir bit değiştirdiyseniz, güçlü karma işlevi yüzde 50 farklı bir çıkış üretebilir. Çok sayıda giriş değerleri aynı çıkış değerini karma. Ancak, bu karma aynı değer için iki ayrı giriş bulmak için uyuşmazlığa neden olur.  
  
 İki taraf (Alice ve Bob) karma işlevi ileti bütünlüğünü sağlamak için kullanabilirsiniz. Bunlar kendi iletileri imzalamak için bir karma algoritmasını seçersiniz. Alice bir ileti yazın ve ardından seçili algoritması kullanılarak bu iletiyi karmasını oluşturun. Ardından aşağıdaki yöntemlerden birini takip etmeleri:  
  
-   Alice, Bob için düz metin iletisi ve karma iletisi (dijital imzası) gönderir. Bob alır ve ileti karmaları ve kendisine Alice alınan karma değeri, karma değerini karşılaştırır. Karma değerleri aynıysa, ileti değiştirilmiş değil. Değerler aynı değilse, ileti Alice yazdığı sonra değiştirildi.  
  
     Ne yazık ki, bu yöntem, Gönderenin özgünlüğünü oluşturmaz. Herkes Alice kimliğine bürünmek ve bir ileti göndermek. Bob belirleyebilirsiniz şey ileti imzası ile eşleşirse ve bunların iletiyi imzalamak için aynı karma algoritmayı kullanabilirsiniz. Bir adam-in--middle saldırı bir form budur. Bkz: [NIB: yeni nesil şifreleme (CNG) güvenli iletişim örnek](http://msdn.microsoft.com/en-us/8048e94e-054a-417b-87c6-4f5e26710e6e) daha fazla bilgi için.  
  
-   Alice, güvenli olmayan ortak bir kanal üzerinden Bob için düz metin iletisi gönderir. Aynen karma ileti özel güvenli bir kanal üzerinden gönderir. Bob düz metin iletisi alır, onu karıştırır ve karma özel olarak alışverişi karmayla karşılaştırır. Karmalar eşleşiyorsa Bob iki şey bilir:  
  
    -   İleti değiştirilmiş değil.  
  
    -   (Alice) iletiyi gönderenin gerçek ' dir.  
  
     Bu sistem çalışmaya Alice kendi özgün karma değeri Bob dışındaki tüm taraflardan Gizle gerekir.  
  
-   Alice, güvenli olmayan ortak bir kanal üzerinden düz metin ileti gönderir ve karma ileti herkes tarafından izlenen her Web sitesinde yerleştirir.  
  
     Bu yöntem, ileti herkes karma değer değiştirmesini engelleyerek oynama engeller. İleti ve onun karma herkes tarafından okunabilir olsa da, karma değeri yalnızca Alice tarafından değiştirilebilir. Alice taklit isteyen bir saldırganın Alice'in Web sitesine erişimi olması gerekir.  
  
 Düz metin olarak iletilir çünkü Alice'in iletileri okunurken önceki yöntemlerden hiçbiri birisi engeller. Tam güvenlik genellikle (İleti imzalama) dijital imzalar ve şifreleme gerektirir.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Karma algoritmaları uygulayan aşağıdaki sınıflar sağlar:  
  
-   <xref:System.Security.Cryptography.HMACSHA1>.  
  
-   <xref:System.Security.Cryptography.MACTripleDES>.  
  
-   <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RIPEMD160>.  
  
-   <xref:System.Security.Cryptography.SHA1Managed>.  
  
-   <xref:System.Security.Cryptography.SHA256Managed>.  
  
-   <xref:System.Security.Cryptography.SHA384Managed>.  
  
-   <xref:System.Security.Cryptography.SHA512Managed>.  
  
-   Tüm güvenli karma algoritması (SHA), İleti Özeti 5 (MD5) ve RIPEMD 160 algoritmalarının HMAC çeşitleri.  
  
-   Tüm SHA algoritmalarının CryptoServiceProvider uygulamaları (yönetilen kod sarmalayıcıları).  
  
-   Tüm MD5 ve SHA algoritmaları, şifreleme yeni nesil (CNG) uygulamalarını.  
  
> [!NOTE]
>  MD5 tasarım açıkları 1996 bulunan ve SHA-1 yerine önerilir. 2004, ek açıkları bulunan ve MD5 algoritması artık güvenli olarak kabul edilir. SHA-1 algoritmasını güvenli olması için de bulundu ve SHA-2 şimdi bunun yerine önerilir.  
  
 [Başa dön](#top)  
  
<a name="random_numbers"></a>   
## <a name="random-number-generation"></a>Rastgele sayı oluşturma  
 Rastgele sayı oluşturma birçok şifreleme işlemlerini tam sayı. Örneğin, şifreleme anahtarları, böylece bunları yeniden uyuşmazlığa olarak rastgele olmanız gerekir. Şifreleme rastgele sayı oluşturucuları daha iyi bir olasılık ile tahmin etmek için uyuşmazlığa neden çıktı oluşturmak gerekir yarısı. Bu nedenle, sonraki çıktı bit tahmin, herhangi bir yöntemini rastgele tahmin daha iyi işlemini gerekir. Sınıflarda [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] rastgele sayı oluşturucuları şifreleme anahtarları oluşturmak için kullanın.  
  
 <xref:System.Security.Cryptography.RNGCryptoServiceProvider> Bir rastgele sayı oluşturucu algoritması uygulaması bir sınıftır.  
  
 [Başa dön](#top)  
  
<a name="clickonce"></a>   
## <a name="clickonce-manifests"></a>ClickOnce bildirimleri  
 İçinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], aşağıdaki şifreleme sınıflarını almak ve bildirim imzaları kullanılarak dağıtılan uygulamalar hakkında bilgi doğrulayın izin [ClickOnce teknolojisini](/visualstudio/deployment/clickonce-security-and-deployment):  
  
-   <xref:System.Security.Cryptography.ManifestSignatureInformation> Sınıfı kullandığınızda bildirim imza hakkında bilgi edinir kendi <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> yöntemi aşırı.  
  
-   Kullanabileceğiniz <xref:System.Security.ManifestKinds> doğrulamak için hangi bildirimleri belirtmek için numaralandırması. Doğrulama sonucu biri <xref:System.Security.Cryptography.SignatureVerificationResult> numaralandırma değerleri.  
  
-   <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> SAX salt okunur koleksiyonu <xref:System.Security.Cryptography.ManifestSignatureInformation> doğrulanmış imzaları nesnelerin.  
  
 Ayrıca, aşağıdaki sınıflar belirli imza bilgileri sağlayın:  
  
-   <xref:System.Security.Cryptography.StrongNameSignatureInformation>bildirim için tanımlayıcı ad imzası bilgileri tutar.  
  
-   <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation>bir bildirim Authenticode imza bilgilerini temsil eder.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TimestampInformation>Authenticode imzası zaman damgasını hakkında bilgi içerir.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TrustStatus>Authenticode imzası güvenilir olup olmadığını denetlemek için basit bir yol sağlar.  
  
 [Başa dön](#top)  
  
<a name="suite_b"></a>   
## <a name="suite-b-support"></a>Suite B desteği  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Ulusal Güvenlik Teşkilatı (NSA) tarafından yayımlanan şifreleme algoritmaları Suite B kümesini destekler. Suite B hakkında daha fazla bilgi için bkz: [NSA Suite B şifreleme olgu sayfası](http://go.microsoft.com/fwlink/?LinkId=100111).  
  
 Aşağıdaki algoritmaları eklenmiştir:  
  
-   Gelişmiş Şifreleme Standardı (AES) algoritması anahtar boyutu 128, 192 ve 256 bit şifreleme.  
  
-   Karma algoritması SHA-1, SHA-256, SHA-384 ve SHA-512 kodlama için güvenli hale getirin. (Son üç genellikle gruplanan ve için SHA-2 olarak adlandırılır.)  
  
-   Eliptik Eğri Dijital imza algoritması (imzalamak için 256 bit, 384 bit ve 521 bit prime moduli Eğriler kullanarak ECDSA). NSA belgeleri özellikle bu Eğriler tanımlar ve p-256, çağıran p-384 ve p-521. Bu algoritma tarafından sağlanan <xref:System.Security.Cryptography.ECDsaCng> sınıfı. Bir özel anahtar ile oturum açma ve ortak anahtar ile imzayı doğrulamak sağlar.  
  
-   Anahtar değişimi ve gizli anlaşma için 256 bit, 384 bit ve 521 bit prime moduli Eğriler kullanarak Eliptik Eğri Diffie-Hellman (ECDH) algoritması. Bu algoritma tarafından sağlanan <xref:System.Security.Cryptography.ECDiffieHellmanCng> sınıfı.  
  
 Yönetilen kod sarmalayıcıları için Federal Bilgi İşleme Standardı (FIPS) sertifikalı AES, SHA-256, SHA-384 ve SHA-512 uygulamaları uygulamalarıdır yeni kullanılabilir <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, ve <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> sınıflar.  
  
 [Başa dön](#top)  
  
<a name="cng"></a>   
## <a name="cryptography-next-generation-cng-classes"></a>Şifreleme İleri nesil (CNG) sınıfları  
 Yeni nesil şifreleme (CNG) sınıfları yerel CNG işlevleri geçici yönetilen sarmalayıcı sağlar. (CNG CryptoAPI yerini alır.) Bu sınıf adları bir parçası olarak "Cng" sahip. Orta CNG sarmalayıcı sınıflar için olan <xref:System.Security.Cryptography.CngKey> anahtar CNG anahtarları kullanımını ve depolama soyutlar kapsayıcı sınıfı. Bu sınıf, bir anahtar çifti ya da bir ortak anahtar güvenli şekilde depolayın ve basit bir dize adı kullanarak başvurduğu sağlar. Eliptik Eğri tabanlı <xref:System.Security.Cryptography.ECDsaCng> imza sınıfı ve <xref:System.Security.Cryptography.ECDiffieHellmanCng> şifreleme sınıfı kullanabileceğiniz <xref:System.Security.Cryptography.CngKey> nesneleri.  
  
 <xref:System.Security.Cryptography.CngKey> Sınıfı, çeşitli açma, oluşturma, silme ve anahtarlarının dışa aktarılması dahil olmak üzere ek işlemleri için kullanılır. Ayrıca, doğrudan yerel işlevleri çağırma sırasında kullanmak için temel alınan anahtar tanıtıcısı erişim sağlar.  
  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Da aşağıdaki gibi CNG sınıfları destekleme çeşitli içerir:  
  
-   <xref:System.Security.Cryptography.CngProvider>bir anahtar depolama sağlayıcısı tutar.  
  
-   <xref:System.Security.Cryptography.CngAlgorithm>CNG algoritması tutar.  
  
-   <xref:System.Security.Cryptography.CngProperty>Sık kullanılan anahtar özellikleri korur.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Şifreleme Modeli](../../../docs/standard/security/cryptography-model.md)|Şifreleme temel sınıf kitaplığı'nda nasıl uygulandığı açıklanmaktadır.|  
|[İzlenecek Yol: Şifreleme Uygulaması Oluşturma](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Temel şifreleme ve şifre çözme görevleri gösterir.|  
|[Şifreleme Sınıflarını Yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Algoritma adlarını şifreleme sınıflarıyla eşleme ve bir şifreleme algoritması nesne tanımlayıcılarını eşleme açıklar.|
