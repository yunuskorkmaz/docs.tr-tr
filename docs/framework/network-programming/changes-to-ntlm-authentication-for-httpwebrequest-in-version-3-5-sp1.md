---
title: "NTLM kimlik doğrulaması için HttpWebRequest sürüm 3.5 SP1'deki değişiklikler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 239834a732fe3bc1cb3e8e7f1d126d26c210d1f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>NTLM kimlik doğrulaması için HttpWebRequest sürüm 3.5 SP1'deki değişiklikler
Güvenlik değişiklikleri, .NET Framework sürüm 3.5 SP1 yapıldı ve daha sonra bir etkisi nasıl tümleşik Windows kimlik doğrulaması tarafından işlenir <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream>, ve ilgili System.Net ad alanındaki sınıflar. Bu değişiklikler, NTLM tabanlı Tümleşik Windows kimlik doğrulaması kullanıldığı web isteği yapmak ve yanıtları almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik, web sunucuları ve tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılmış istemci uygulamaları etkileyebilir.  
  
## <a name="overview"></a>Genel Bakış  
 Tümleşik Windows kimlik doğrulaması tasarımını bazı kimlik bilgisi yanıtlarının bunlar yeniden kullanılan iletilen veya anlamı Evrensel olmasına izin verir. Ardından bu belirli tasarım özelliği gerekli değildir, kimlik doğrulama protokollerini hedef belirli bilgilerin yanı sıra kanal belirli bilgileri taşımak. Hizmetleri sonra kimlik bilgisi yanıtları hizmet belirli bilgileri gibi bir hizmet asıl adı (SPN) içerdiğinden emin olmak için genişletilmiş koruma sağlayabilir. Kimlik bilgisi alışverişleri bu bilgilerle, hizmetleri yanlış alındıktan kimlik bilgisi yanıtları kötü niyetli kullanımına karşı daha iyi koruyabilir.  
  
 Birden çok bileşeni <xref:System.Net> ve <xref:System.Net.Security> ad alanları çağıran bir uygulama adına tümleşik Windows kimlik doğrulaması gerçekleştirin. Bu bölümde, tümleşik Windows kimlik doğrulaması kullanımları genişletilmiş koruma eklenecek System.Net bileşenleri değişiklikler açıklanmaktadır.  
  
## <a name="changes"></a>Değişiklikler  
 Tümleşik Windows kimlik doğrulaması ile kullanılan NTLM kimlik doğrulama işlemi, hedef bilgisayar tarafından verilen ve istemci bilgisayarına geri gönderilen bir sınama içerir. Bir bilgisayarın kendisi oluşturulan bir sınama aldığında, bağlantıyı döngü geri bağlantı (127.0.0.1, örneğin IPv4 adresi) olmadıkça kimlik doğrulaması başarısız olur.  
  
 Bir iç Web sunucusunda çalışan bir hizmete erişirken http://contoso/service veya https://contoso/service benzer bir URL'yi kullanarak hizmete erişmek için yaygın bir sorundur. "contoso" adı genellikle hizmet dağıtıldığı bilgisayarın bilgisayar adı değil. <xref:System.Net> Ve ilgili ad alanlarını destek Active Directory, DNS, NetBIOS kullanarak, yerel bilgisayarın ana bilgisayar (genellikle WINDOWS\system32\drivers\etc\hosts, örneğin) dosyası veya (genellikle WINDOWS\system32\ yerel bilgisayarın lmhosts dosyası Örneğin drivers\etc\lmhosts) adreslerine adları çözümlemek için. Adı "contoso", "contoso" gönderilen istekleri uygun sunucu bilgisayarına gönderilen böylece çözümlenir.  
  
 Büyük dağıtımlar için yapılandırıldığında, ayrıca dağıtım için hiç istemci uygulamaları ve son kullanıcılar tarafından kullanılan temel makine adlarıyla verilecek bir tek bir sanal sunucu adı için yaygındır. Örneğin, sunucu www.contoso.com çağrı ancak iç ağda yalnızca "contoso" kullanın. Bu ad istemci web istek ana bilgisayar üstbilgisi adı verilir. Belirtildiği gibi HTTP protokolü tarafından ana bilgisayar istek üstbilgisi alanı istenen kaynak Internet ana bilgisayarı ve bağlantı noktası sayısını belirtir. Bu bilgiler kullanıcı veya başvuran kaynak (genellikle bir HTTP URL'si) tarafından verilen özgün uri'den elde edilir. .NET Framework sürüm 4, bu bilgiler ayrıca kullanarak yeni istemci tarafından ayarlanabilir <xref:System.Net.HttpWebRequest.Host%2A> özelliği.  
  
 <xref:System.Net.AuthenticationManager> Sınıfı tarafından kullanılan yönetilen kimlik doğrulaması bileşenleri ("modüller") denetler <xref:System.Net.WebRequest> türetilmiş sınıfları ve <xref:System.Net.WebClient> sınıfı. <xref:System.Net.AuthenticationManager> SAX kullanıma sunan bir özelliği bir <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> kimlik doğrulaması sırasında kullanılacak özel bir SPN dize sağlamak üzere uygulamalar için URI dizesini tarafından dizine nesnesi.  
  
 Sürüm 3.5 SP1'i varsayılan ana bilgisayar adını belirtmek için bir SPN NTLM (NT LAN Yöneticisi) kimlik doğrulaması, istek URL'SİNDE kullanılan artık exchange <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> özelliği ayarlı değil. İstek URL'SİNDE kullanılan ana bilgisayar adı belirtilen ana bilgisayar üstbilgisi alanından farklı <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> istemci isteğindeki. İstek URL'SİNDE kullanılan ana bilgisayar adı sunucunun gerçek ana bilgisayar adı, sunucu, bilgisayarın IP adresi ya da geri döngü adresine makine adını farklı olabilir. Bu durumlarda, Windows kimlik doğrulama isteği başarısız olur. Sorunu gidermek için kullanılan ana bilgisayar adı Windows bildirmek ihtiyacımız istemci istek URL'sindeki ("contoso", örneğin) gerçekte farklı bir ad yerel bilgisayar isteğidir.  
  
 Bu değişikliği geçici olarak çözmek bir sunucu uygulaması için olası birkaç yöntem vardır. İstek URL'sindeki kullanılan ana bilgisayar adı eşlemek için önerilen yaklaşımdır `BackConnectionHostNames` sunucunun kayıt defterinde anahtar. `BackConnectionHostNames` Kayıt defteri anahtarı bir ana bilgisayar adı bir geri döngü adresine eşlemek için normal olarak kullanılır. Adımlar aşağıda listelenmiştir.  
  
 Geri döngü adresine eşlenir ve yerel bir bilgisayarda Web sitelerine bağlanabilirsiniz, ana bilgisayar adını belirtmek için aşağıdaki adımları izleyin:  
  
 1. Başlat'ı tıklatın, Çalıştır'ı tıklatın, regedit yazın ve ardından Tamam'ı tıklatın.  
  
 2. Kayıt Defteri Düzenleyicisi'nde, bulun ve aşağıdaki kayıt defteri anahtarını tıklatın:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3. Msv1_0 sağ tıklatın, Yeni'yi ve çok dizeli değer'ye tıklayın.  
  
 4. Tür `BackConnectionHostNames`, ve ardından ENTER tuşuna basın.  
  
 5. Sağ `BackConnectionHostNames`, Değiştir'i tıklatın.  
  
 6. Değer verisi kutusuna ana bilgisayar adı veya yerel bilgisayarda ve Tamam'ı siteleri (istek URL'SİNDE kullanılan ana bilgisayar adı) ana bilgisayar adlarını yazın.  
  
 7. Kayıt Defteri Düzenleyicisi'nden çıkın ve IISAdmin hizmetini yeniden başlatın ve Iısreset'i çalıştırın.  
  
 Daha az güvenli çalışma yaklaşık döngü geri denetimi devre dışı bırakmak için açıklandığı gibi olan [http://support.microsoft.com/kb/896861](http://go.microsoft.com/fwlink/?LinkID=179657). Bu yansıma saldırılara karşı koruma devre dışı bırakır. Bu nedenle yalnızca gerçekten kullandığınız için makine beklediğiniz için diğer adlar kümesi sınırlamak iyidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>  
 <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>  
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
