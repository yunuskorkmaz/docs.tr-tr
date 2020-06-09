---
title: WCF ile Temsilcilik ve Kimliğe Bürünme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
ms.openlocfilehash: e491925fdbe8d44df8e0c64b563eb92569453e35
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599262"
---
# <a name="delegation-and-impersonation-with-wcf"></a>WCF ile Temsilcilik ve Kimliğe Bürünme
*Kimliğe bürünme* , hizmetlerin, istemci erişimini bir hizmet etki alanı kaynaklarına kısıtlamak için kullandığı yaygın bir tekniktir. Hizmet etki alanı kaynakları, yerel dosyalar (kimliğe bürünme) gibi makine kaynakları ya da başka bir makinedeki bir dosya paylaşma (temsili) gibi bir kaynak olabilir. Örnek bir uygulama için bkz. [Istemcinin kimliğine bürünme](../samples/impersonating-the-client.md). Kimliğe bürünme özelliğinin nasıl kullanılacağına ilişkin bir örnek için bkz. [nasıl yapılır: bir hizmette Istemcinin kimliğine bürünme](../how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
> Bir hizmetin bir hizmette kimliğe bürünerek hizmetin, sunucu işleminden daha yüksek ayrıcalıklara sahip olabilecek istemci kimlik bilgileriyle çalıştığını unutmayın.  
  
## <a name="overview"></a>Genel Bakış  
 Genellikle istemciler, hizmetin istemci adına bazı işlemleri gerçekleştirmesini sağlamak için bir hizmet çağırır. Kimliğe bürünme hizmeti, eylemi gerçekleştirirken hizmetin istemci olarak davranmasını sağlar. Temsili, bir ön uç hizmetinin istemcinin isteğini arka uç hizmetinin da istemcinin kimliğine bürünebileceği şekilde bir arka uç hizmetine iletmesini sağlar. Kimliğe bürünme en yaygın olarak, istemcinin belirli bir eylemi gerçekleştirme yetkisine sahip olup olmadığını kontrol etmenin bir yolu olarak kullanılır, ancak temsil, kimliğe bürünme yeteneklerini, istemcinin kimliğiyle birlikte bir arka uç hizmetine akar. Temsili, Kerberos tabanlı kimlik doğrulaması gerçekleştirildiğinde kullanılabilecek bir Windows etki alanı özelliğidir. Yetkilendirme, kimlik akışından farklıdır ve yetkilendirme, istemcinin parolasını elinde bulunmadan istemci kimliğine bürünme özelliğini aktardığından, kimlik akışından çok daha yüksek ayrıcalıklı bir işlemdir.  
  
 Hem kimliğe bürünme hem de temsil, istemcinin bir Windows kimliğine sahip olmasını gerektirir. Bir istemci bir Windows kimliğine sahip değilse, kullanılabilir tek seçenek, istemcinin kimliğini ikinci hizmete Flow ' dır.  
  
## <a name="impersonation-basics"></a>Kimliğe bürünme temelleri  
 Windows Communication Foundation (WCF), çeşitli istemci kimlik bilgileri için kimliğe bürünmeyi destekler. Bu konuda, bir hizmet yönteminin uygulanması sırasında çağıranın kimliğe bürünmesi için hizmet modeli desteği açıklanmaktadır. Ayrıca, bu senaryolarda kimliğe bürünme ve SOAP Güvenliği ve WCF seçeneklerini içeren yaygın dağıtım senaryolarından de bahsedildi.  
  
 Bu konu, SOAP güvenliği kullanılırken WCF 'de kimliğe bürünme ve temsili ile odaklanır. Aktarım güvenliği [Ile kimliğe bürünme kullanma](using-impersonation-with-transport-security.md)bölümünde açıklandığı gibi, aktarım GÜVENLIĞI kullanılırken WCF ile kimliğe bürünme ve temsil özelliğini de kullanabilirsiniz.  
  
## <a name="two-methods"></a>İki yöntem  
 WCF SOAP güvenliğinin, kimliğe bürünme işlemini gerçekleştirmek için iki ayrı yöntemi vardır. Kullanılan yöntem bağlamaya bağlıdır. Bunlardan biri, güvenlik desteği sağlayıcısı arabirimi (SSPI) veya Kerberos kimlik doğrulamasından alınan bir Windows belirtecinden kimliğe bürünme yoluyla, daha sonra hizmette önbelleğe alınır. İkincisi, toplu olarak *Service-for-User* (S4U) olarak adlandırılan Kerberos uzantılarından alınan bir Windows belirtecinden kimliğe bürünme özelliğine sahiptir.  
  
### <a name="cached-token-impersonation"></a>Önbelleğe alınmış belirteç kimliğe bürünme  
 Önbelleğe alınmış belirteç kimliğe bürünme işlemini aşağıda bulabilirsiniz:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding> , ve <xref:System.ServiceModel.NetTcpBinding> bir Windows istemci kimlik bilgileri ile.  
  
- <xref:System.ServiceModel.BasicHttpBinding><xref:System.ServiceModel.BasicHttpSecurityMode> <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> kimlik bilgisi veya istemcinin, hizmetin geçerli bir Windows hesabıyla eşlenebilmesi için bir Kullanıcı adı kimlik bilgisi sunan herhangi bir standart bağlama ile bir kümesi vardır.  
  
- Herhangi biri <xref:System.ServiceModel.Channels.CustomBinding> , olarak ayarlanmış bir Windows istemci kimlik bilgisi kullanır `requireCancellation` `true` . (Özelliği şu sınıflarda kullanılabilir: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> , <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters> , ve <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters> .) Bağlamada güvenli bir konuşma kullanılıyorsa, `requireCancellation` özelliği de olarak ayarlanmalıdır `true` .  
  
- <xref:System.ServiceModel.Channels.CustomBinding>İstemci, Kullanıcı adı kimlik bilgisini sunan her yerde. Bağlamada güvenli konuşma kullanılıyorsa, `requireCancellation` özelliği de olarak ayarlanmalıdır `true` .  
  
### <a name="s4u-based-impersonation"></a>S4U tabanlı kimliğe bürünme  
 Aşağıdaki ile S4U tabanlı kimliğe bürünme gerçekleştirebilirsiniz:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding> , ve <xref:System.ServiceModel.NetTcpBinding> hizmetin geçerli bir Windows hesabıyla eşlenebilmesi için sertifika istemci kimlik bilgileri ile.  
  
- Herhangi biri <xref:System.ServiceModel.Channels.CustomBinding> , `requireCancellation` özelliği olarak ayarlanmış bir Windows istemci kimlik bilgisi kullanır `false` .  
  
- Herhangi biri <xref:System.ServiceModel.Channels.CustomBinding> , `requireCancellation` özelliği olarak ayarlanmış bir Kullanıcı adı veya Windows istemci kimlik bilgisi ve güvenli konuşma kullanır `false` .  
  
 Hizmetin, istemcinin kimliğine bürünebileceği kapsam, hizmet hesabının kimliğe bürünme girişiminde bulunduğu ayrıcalıklara, kullanılan kimliğe bürünme türüne ve istemcinin izin verdiği kimliğe bürünme kapsamına bağlıdır.  
  
> [!NOTE]
> İstemci ve hizmet aynı bilgisayar üzerinde çalışırken ve istemci bir sistem hesabı (örneğin, `Local System` veya) altında çalışıyorsa `Network Service` , durum bilgisi olan güvenlik bağlamı belirteçleri ile güvenli bir oturum oluşturulduğunda istemciye kimliğe bürünme yapılamaz. Bir Windows form veya konsol uygulaması genellikle şu anda oturum açmış olan hesap altında çalışır, bu sayede hesaba varsayılan olarak kimliğe bürünme yapılabilir. Ancak, istemci bir ASP.NET sayfası olduğunda ve Bu sayfa IIS 6,0 veya IIS 7,0 ' de barındırılıyorsa, istemci `Network Service` Varsayılan olarak hesap altında çalışır. Güvenli oturumları destekleyen sistem tarafından sağlanmış tüm bağlamalar, varsayılan olarak durum bilgisi olmayan bir güvenlik bağlamı belirteci (SCT) kullanır. Ancak, istemci bir ASP.NET sayfalararsa ve durum bilgisi olan güvenlik oturumları kullanılıyorsa, istemciye kimliğe bürünme yapılamaz. Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Hizmet yönteminde kimliğe bürünme: bildirime dayalı model  
 Çoğu kimliğe bürünme senaryosunda, çağıran bağlamda hizmet yönteminin yürütülmesi yer alabilir. WCF, kullanıcının özniteliğinde kimliğe bürünme gereksinimini belirtmesini sağlayarak bunu kolay hale getiren bir kimliğe bürünme özelliği sağlar <xref:System.ServiceModel.OperationBehaviorAttribute> . Örneğin, aşağıdaki kodda, WCF altyapısı yöntemini yürütmeden önce çağıranı taklit eder `Hello` . Yöntemi içindeki yerel kaynaklara erişme girişimleri, `Hello` yalnızca kaynağın erişim denetim listesi (ACL) arayan erişim ayrıcalıklarına izin veriyorsa başarılı olur. Kimliğe bürünme özelliğini etkinleştirmek için, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği, <xref:System.ServiceModel.ImpersonationOption> <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, ya da bir numaralandırma değerlerinden birine ayarlayın.  
  
> [!NOTE]
> Bir hizmet, uzak istemciden daha yüksek kimlik bilgilerine sahip olduğunda, özelliği olarak ayarlandıysa hizmetin kimlik bilgileri kullanılır <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.ImpersonationOption.Allowed> . Diğer bir deyişle, düşük ayrıcalıklı bir kullanıcı kimlik bilgilerini sağlıyorsa, daha yüksek ayrıcalıklı bir hizmet yöntemi hizmetin kimlik bilgileriyle yürütür ve düşük ayrıcalıklı kullanıcının başka bir şekilde kullanamayacak kaynakları kullanabilir.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 WCF altyapısı, yalnızca çağıran tarafından bir Windows kullanıcı hesabıyla eşleştirilecek kimlik bilgileriyle doğrulandıysa çağıranın kimliğine bürünebilir. Hizmet, bir Windows hesabına eşlenemeyen bir kimlik bilgisi kullanarak kimlik doğrulaması yapacak şekilde yapılandırıldıysa, hizmet yöntemi yürütülmez.  
  
> [!NOTE]
> Windows XP 'de, bir durum bilgisi olan bir SCT oluşturulduysa kimliğe bürünme başarısız olur ve buna yol açar <xref:System.InvalidOperationException> . Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Bir hizmet yönteminde kimliğe bürünme: kesinlik temelli model  
 Bazen bir çağıranın, işlev için tüm hizmet yöntemini taklit etmesine gerek yoktur, ancak yalnızca bir bölümü için. Bu durumda, çağıranın Windows kimliğini hizmet yöntemi içinde edinin ve imperatively kimliğe bürünme işlemini gerçekleştirin. Bunu <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> , <xref:System.ServiceModel.ServiceSecurityContext> sınıfının bir örneğini döndürmek <xref:System.Security.Principal.WindowsIdentity> ve <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> örneği kullanmadan önce metodunu çağırmak için özelliğini kullanarak yapın.  
  
> [!NOTE]
> `Using` `using` Kimliğe bürünme eylemini otomatik olarak dönüştürmek için Visual Basic ifadesini veya C# ifadesini kullandığınızdan emin olun. İfadesini kullanmazsanız veya Visual Basic veya C# dışında bir programlama dili kullanıyorsanız, kimliğe bürünme düzeyini döndürtığınızdan emin olun. Bunun yapılmaması, hizmet reddi ve ayrıcalık yükselmesi saldırıları için temel oluşturur.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Tüm hizmet yöntemleri için kimliğe bürünme  
 Bazı durumlarda, arayanın bağlamında bir hizmetin tüm yöntemlerini gerçekleştirmeniz gerekir. Bu özelliği Yöntem temelinde açıkça etkinleştirmek yerine öğesini kullanın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> . Aşağıdaki kodda gösterildiği gibi, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> özelliğini olarak ayarlayın `true` . , <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Sınıfının davranış koleksiyonlarından alınır <xref:System.ServiceModel.ServiceHost> . Ayrıca `Impersonation` , <xref:System.ServiceModel.OperationBehaviorAttribute> her metoda uygulanan özelliğinin ya da olarak ayarlanması gerektiğini unutmayın <xref:System.ServiceModel.ImpersonationOption.Allowed> <xref:System.ServiceModel.ImpersonationOption.Required> .  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Aşağıdaki tabloda, ve ' nin tüm olası birleşimleri için WCF davranışı açıklanmaktadır `ImpersonationOption` `ImpersonateCallerForAllServiceOperations` .  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Davranış|  
|---------------------------|------------------------------------------------|--------------|  
|Gerekli|yok|WCF Çağrıyı taklit eder|  
|İzin Verildi|yanlış|WCF, çağıranın kimliğine bürünemez|  
|İzin Verildi|true|WCF Çağrıyı taklit eder|  
|NotAllowed|yanlış|WCF, çağıranın kimliğine bürünemez|  
|NotAllowed|true|Veril. (Bir oluşturulur <xref:System.InvalidOperationException> .)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Windows kimlik bilgileri ve önbelleğe alınmış belirteç kimliğe bürünme ile edinilen kimliğe bürünme düzeyi  
 Bazı senaryolarda, istemci bir Windows istemci kimlik bilgisi kullanıldığında hizmetin gerçekleştirdiği kimliğe bürünme düzeyi üzerinde kısmi denetime sahiptir. İstemci anonim kimliğe bürünme düzeyi belirttiğinde bir senaryo meydana gelir. Diğer bir deyişle, önbelleğe alınmış bir belirteçle kimliğe bürünme işlemi gerçekleştirilirken meydana gelir. Bu, <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> <xref:System.ServiceModel.Security.WindowsClientCredential> genel sınıfın bir özelliği olarak erişilen sınıfının özelliği ayarlanarak yapılır <xref:System.ServiceModel.ChannelFactory%601> .  
  
> [!NOTE]
> Kimliğe bürünme düzeyi belirtilmesi, istemcinin hizmette anonim olarak oturum açmasına neden olur. Bu nedenle, kimliğe bürünme işleminin gerçekleştirilip gerçekleştirilmediğine bakılmaksızın hizmetin anonim oturum açmalarına izin vermelidir.  
  
 İstemci kimliğe bürünme düzeyini,, veya olarak <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> belirtebilir <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> . Aşağıdaki kodda gösterildiği gibi, yalnızca belirtilen düzeydeki bir belirteç oluşturulur.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Aşağıdaki tablo, önbelleğe alınmış bir belirteçle kimliğe bürünme sırasında hizmetin aldığı kimliğe bürünme düzeyini belirtir.  
  
|`AllowedImpersonationLevel`deeri|Hizmet,`SeImpersonatePrivilege`|Hizmet ve istemci, temsilciliğini alabilir|Önbelleğe alınmış belirteç`ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonim|Yes|yok|Kimliğe bürünme|  
|Anonim|Hayır|yok|Kimlik|  
|Kimlik|yok|yok|Kimlik|  
|Kimliğe bürünme|Yes|yok|Kimliğe bürünme|  
|Kimliğe bürünme|Hayır|yok|Kimlik|  
|Temsilci|Yes|Yes|Temsilci|  
|Temsilci|Evet|Hayır|Kimliğe bürünme|  
|Temsilci|Hayır|yok|Kimlik|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Kullanıcı adı kimlik bilgilerinden alınan kimliğe bürünme düzeyi ve önbelleğe alınmış belirteç kimliğe bürünme  
 Bir istemci, hizmetin Kullanıcı adı ve parolasını geçirerek, özelliğin özelliği olarak ayarlanmasına eşdeğer olan kullanıcının bu kullanıcı olarak oturum açmasına olanak sağlar `AllowedImpersonationLevel` <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> . ( `AllowedImpersonationLevel` <xref:System.ServiceModel.Security.WindowsClientCredential> Ve <xref:System.ServiceModel.Security.HttpDigestClientCredential> sınıflarında kullanılabilir.) Aşağıdaki tablo, hizmet Kullanıcı adı kimlik bilgilerini aldığında elde edilen kimliğe bürünme düzeyini sağlar.  
  
|`AllowedImpersonationLevel`|Hizmet,`SeImpersonatePrivilege`|Hizmet ve istemci, temsilciliğini alabilir|Önbelleğe alınmış belirteç`ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|yok|Yes|Yes|Temsilci|  
|yok|Evet|Hayır|Kimliğe bürünme|  
|yok|Hayır|yok|Kimlik|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>S4U tabanlı kimliğe bürünme 'den edinilen kimliğe bürünme düzeyi  
  
|Hizmet,`SeTcbPrivilege`|Hizmet,`SeImpersonatePrivilege`|Hizmet ve istemci, temsilciliğini alabilir|Önbelleğe alınmış belirteç`ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Yes|Yes|yok|Kimliğe bürünme|  
|Evet|Hayır|yok|Kimlik|  
|Hayır|yok|yok|Kimlik|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Bir Istemci sertifikasını bir Windows hesabıyla eşleme  
 Bir istemcinin sertifikayı kullanarak bir hizmette kimliğini doğrulaması ve hizmetin istemciyi Active Directory aracılığıyla mevcut bir hesapla eşlemesini sağlamak mümkündür. Aşağıdaki XML, sertifikayı eşlemek için hizmetin nasıl yapılandırılacağını gösterir.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="MapToWindowsAccount">  
      <serviceCredentials>  
        <clientCertificate>  
          <authentication mapClientCertificateToWindowsAccount="true" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Aşağıdaki kod, hizmetin nasıl yapılandırılacağını gösterir.  
  
```csharp
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>Temsilci  
 Bir arka uç hizmetine temsilci seçmek için, bir hizmet, istemcinin Windows kimliğini kullanarak Kerberos Multi-BAI (NTLM geri dönüşü olmadan SSPI) veya arka uç hizmetine Kerberos doğrudan kimlik doğrulaması gerçekleştirmelidir. Bir arka uç hizmetine temsilci seçmek için bir <xref:System.ServiceModel.ChannelFactory%601> ve bir kanal oluşturun ve sonra istemciyi taklit ederken kanal üzerinden iletişim kurun. Bu tür bir temsilciyle, arka uç hizmetinin ön uç hizmetinden konumlandırıldığı mesafe ön uç hizmeti tarafından elde edilen kimliğe bürünme düzeyine bağlıdır. Kimliğe bürünme düzeyi olduğunda <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> , ön uç ve arka uç hizmetlerinin aynı makinede çalışıyor olması gerekir. Kimliğe bürünme düzeyi olduğunda <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> , ön uç ve arka uç hizmetleri ayrı makinelerde veya aynı makinede olabilir. Temsili düzeyi kimliğe bürünme özelliğinin etkinleştirilmesi için Windows etki alanı ilkesinin temsilciliğe izin verecek şekilde yapılandırılması gerekir. Temsilci desteği için Active Directory yapılandırma hakkında daha fazla bilgi için bkz. [temsilci kimlik doğrulamasını etkinleştirme](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc780217(v=ws.10)).  
  
> [!NOTE]
> İstemci, arka uç hizmetindeki bir Windows hesabına karşılık gelen bir Kullanıcı adı ve parola kullanarak ön uç hizmetinde kimlik doğrulaması gerçekleştiriyorsa, ön uç hizmeti istemcinin kullanıcı adını ve parolasını yeniden kullanarak arka uç hizmetinde kimlik doğrulaması yapabilir. Bu özellikle güçlü bir kimlik akışı biçimidir, çünkü arka uç hizmetine Kullanıcı adı ve parola geçirme, arka uç hizmetinin kimliğe bürünme işlemini gerçekleştirmesini sağlar ancak Kerberos kullanılmadığından, temsilciyi oluşturmaz. Active Directory denetimleri, Kullanıcı adı ve parola kimlik doğrulaması için geçerlidir.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Kimliğe bürünme düzeyi Işlevi olarak temsil yeteneği  
  
|Kimliğe bürünme düzeyi|Hizmet, işlemler arası temsili gerçekleştirebilir|Hizmet, makineler arası temsili gerçekleştirebilir|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Hayır|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Evet|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Yes|Yes|  
  
 Aşağıdaki kod örneği, temsilciyi nasıl kullanacağınızı gösterir.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Bir uygulamayı kısıtlanmış temsilciyi kullanacak şekilde yapılandırma  
 Kısıtlanmış temsilciyi kullanabilmeniz için, gönderenin, alıcının ve etki alanı denetleyicisinin bu şekilde yapılandırılması gerekir. Aşağıdaki yordamda, kısıtlanmış temsilciyi etkinleştiren adımlar listelenmektedir. Yetkilendirme ve kısıtlanmış yetkilendirme arasındaki farklılıklar hakkında daha fazla bilgi için, kısıtlanmış tartışmayı ele alan [Windows Server 2003 Kerberos uzantılarının](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738207(v=ws.10)) bölümüne bakın.  
  
1. Etki alanı denetleyicisinde, **Hesap duyarlıdır ve** istemci uygulamasının çalıştığı hesap için temsilci seçilemez onay kutusunu temizleyin.  
  
2. Etki alanı denetleyicisinde, istemci uygulamasının çalıştığı hesap için **hesap için güvenilir** onay kutusunu seçin.  
  
3. Etki alanı denetleyicisinde, orta katman bilgisayarı, yetkilendirme **Için güven bilgisayar** seçeneğine tıklayarak, yetkilendirme için güvenilecek şekilde yapılandırın.  
  
4. Etki alanı denetleyicisinde, **Bu bilgisayara yalnızca belirtilen hizmetlere yetkilendirme Için güven** seçeneğini tıklayarak orta katman bilgisayarı Kısıtlı temsilciyi kullanacak şekilde yapılandırın.  
  
 Kısıtlanmış temsilciyi yapılandırma hakkında daha ayrıntılı yönergeler için bkz. [Kerberos protokol geçişi ve kısıtlanmış temsili](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc739587(v=ws.10)).
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>
- <xref:System.ServiceModel.ImpersonationOption>
- <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>
- <xref:System.ServiceModel.ServiceSecurityContext>
- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ChannelFactory%601>
- <xref:System.Security.Principal.TokenImpersonationLevel.Identification>
- [Taşıma Güvenliği ile Kimliğe Bürünme Kullanma](using-impersonation-with-transport-security.md)
- [İstemci Kimliğine Bürünme](../samples/impersonating-the-client.md)
- [Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme](../how-to-impersonate-a-client-on-a-service.md)
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
