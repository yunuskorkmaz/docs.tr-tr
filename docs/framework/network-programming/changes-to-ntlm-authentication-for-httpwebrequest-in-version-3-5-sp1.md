---
title: İçin sürüm 3.5 SP1'de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
ms.openlocfilehash: 40e041f17a07e17aad3d5f10f7920b0466e2b1b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589564"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>İçin sürüm 3.5 SP1'de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler
Güvenlik değişiklikleri, .NET Framework sürüm 3.5 SP1 yapıldı ve tümleşik Windows kimlik doğrulaması tarafından işlenir, etkileyen daha sonra <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream>, ve System.Net ad alanındaki ilgili sınıflar. Bu değişiklikler, NTLM tabanlı Tümleşik Windows kimlik doğrulaması kullanıldığı web isteklerinde bulunmak ve yanıt almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik, web sunucuları ve tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılmış istemci uygulamaları etkileyebilir.  
  
## <a name="overview"></a>Genel Bakış  
 Tümleşik Windows kimlik doğrulaması tasarımını bazı kimlik bilgisi yanıtlarının bunlar yeniden kullanılan veya iletilmesi yani evrensel olmasına izin verir. Ardından bu belirli tasarım özelliği gerekmiyorsa, kimlik doğrulama protokolleri kanal özgü bilgilerin yanı sıra hedef belirli bilgileri taşıyan. Hizmetleri, ardından kimlik bilgisi yanıtlarının hizmet belirli bilgileri gibi bir hizmet asıl adı (SPN) içerdiğinden emin olmak için genişletilmiş koruma sağlayabilir. Kimlik bilgisi değişimleri bu bilgilere sahip olarak Hizmetleri hatalı alındıktan kimlik bilgisi yanıtlarının kötü niyetli kullanımına karşı daha iyi koruma olanağına sahip olursunuz.  
  
 Birden çok bileşeni <xref:System.Net> ve <xref:System.Net.Security> ad alanları, çağıran bir uygulama adına tümleşik Windows kimlik doğrulaması gerçekleştirin. Bu bölümde, değişiklikleri genişletilmiş koruma, tümleşik Windows kimlik doğrulaması kullanımını eklemek için System.Net bileşenlerine açıklanmaktadır.  
  
## <a name="changes"></a>Değişiklikler  
 Tümleşik Windows kimlik doğrulamasıyla NTLM kimlik doğrulama işlemi, hedef bilgisayar tarafından verilen ve istemci bilgisayarına geri gönderilen bir sınama içerir. Bir bilgisayarı kendi oluşturulan bir sınama aldığında, döngü geri bağlantının (127.0.0.1, örneğin IPv4 adresi) olmadığı sürece kimlik doğrulaması başarısız olur.  
  
 Bir iç Web sunucusunda çalışan bir hizmetin erişirken, benzer bir URL kullanarak hizmete erişmek için ortak `http://contoso/service` veya `https://contoso/service`. "contoso" adı genellikle hizmet dağıtıldığı bilgisayarın bilgisayar adını değil. <xref:System.Net> Ve ilgili ad alanlarını destekleyen kullanarak Active Directory, DNS, NetBIOS, yerel bilgisayarın hosts dosyasını (genellikle WINDOWS\system32\drivers\etc\hosts, örneğin) veya (genellikle WINDOWS\system32\ yerel bilgisayarın lmhosts dosyası Örneğin drivers\etc\lmhosts) adları adreslerine çözümleyebilir. Adı "contoso", "contoso" için gönderilen istekleri uygun sunucu bilgisayara gönderilir, böylece çözümlenir.  
  
 Büyük dağıtımlar için yapılandırıldığında, ayrıca bir tek bir sanal sunucu adı dağıtıma hiç istemci uygulamaları ve son kullanıcılar tarafından kullanılan temel alınan makine adları ile verilmesi yaygındır. Örneğin, sunucunun çağırabilirsiniz `www.contoso.com`, ancak bir iç ağdaki yalnızca kullanabilirsiniz "contoso". Bu ad istemci web isteğinde ana bilgisayar üstbilgisi adı verilir. Belirtildiği gibi HTTP protokolü tarafından ana bilgisayar adı istek üstbilgisi alanı istenen kaynak Internet konak ve bağlantı noktası sayısını belirtir. Bu bilgiler kullanıcı veya başvurulan kaynak (genellikle bir HTTP URL'si) tarafından verilen ve özgün bir URI elde edilir. .NET Framework sürüm 4, bu bilgileri ayrıca kullanarak yeni istemci tarafından ayarlanabilir <xref:System.Net.HttpWebRequest.Host%2A> özelliği.  
  
 <xref:System.Net.AuthenticationManager> Sınıfı tarafından kullanılan yönetilen kimlik doğrulama bileşenleri ("modülleri") denetler <xref:System.Net.WebRequest> türetilmiş sınıfları ve <xref:System.Net.WebClient> sınıfı. <xref:System.Net.AuthenticationManager> SAX kullanıma sunan bir özellik bir <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> sağlamak üzere kimlik doğrulaması sırasında kullanılmak üzere özel bir SPN dizesi uygulamalar için URI dizesi tarafından dizine nesnesi.  
  
 Sürüm 3.5 SP1'i varsayılan ana bilgisayar adını belirtmek için bir SPN NTLM (NT LAN Yöneticisi) kimlik doğrulaması, istek URL'SİNDE kullanılan artık exchange <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> özelliği ayarlı değil. İstek URL'SİNDE kullanılan ana bilgisayar adı belirtilen ana bilgisayar üst bilgisinden farklı <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> istemci isteğindeki. İstek URL'SİNDE kullanılan ana bilgisayar adı, sunucunun gerçek ana bilgisayar adını, sunucu, bilgisayarın IP adresini veya geri döngü adresine makine adını farklı olabilir. Bu durumlarda, Windows kimlik doğrulama isteği başarısız olur. Sorunu gidermek için kullanılan ana bilgisayar adı Windows bildirmek gerekir, istemci istek URL'SİNDE ("contoso", örneğin) gerçekte yerel bilgisayar için farklı bir ad isteğidir.  
  
 Bu değişikliği geçici çalışmak bir sunucu uygulaması için birkaç olası yöntem vardır. İstek URL'si için kullanılan konak adını eşleştirmek için önerilen yaklaşımdır `BackConnectionHostNames` sunucunun kayıt defterinde anahtar. `BackConnectionHostNames` Kayıt defteri anahtarı normalde bir ana bilgisayar adı için bir geri döngü adresine eşlemek için kullanılır. Adımları aşağıda listelenmiştir.  
  
 Geri döngü adresine eşlenir ve Web siteleri için yerel bir bilgisayara bağlanabilir, ana bilgisayar adlarını belirtmek için bu adımları izleyin:  
  
 1. Başlat'a tıklayın, Çalıştır'ı tıklatın, regedit yazın ve Tamam'a tıklayın.  
  
 2. Kayıt Defteri Düzenleyicisi'nde bulun ve aşağıdaki kayıt defteri anahtarı'ye tıklayın:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3. Msv1_0 sağ tıklayın, yeni'yi işaretleyin ve çok dizeli değer'ye tıklayın.  
  
 4. Tür `BackConnectionHostNames`, ve ardından ENTER tuşuna basın.  
  
 5. Sağ `BackConnectionHostNames`, Değiştir'i tıklatın.  
  
 6. Ana bilgisayar adı veya ana bilgisayar adlarını, yerel bilgisayarda ve Tamam'ı (istek URL'SİNDE kullanılan ana bilgisayar adı) siteler için değeri veri kutusuna yazın.  
  
 7. Kayıt Defteri Düzenleyicisi'nden çıkın ve ardından IISADMIN hizmetini yeniden başlatın ve Iısreset'i çalıştırın.  
  
 Daha az güvenli bir iş yaklaşık döngü geri denetimi devre dışı bırakmak için açıklandığı olan <https://support.microsoft.com/kb/896861>. Bu yansıma saldırılara karşı koruma devre dışı bırakır. Bu nedenle yalnızca gerçekten kullandığınız makinenin beklediğiniz için alternatif adlar kümesini sınırlandırmak iyidir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>
- <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
