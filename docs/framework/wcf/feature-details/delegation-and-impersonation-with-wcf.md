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
ms.openlocfilehash: 3fd90cde16afdfe32b9bd0533ba04e35928d2706
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920200"
---
# <a name="delegation-and-impersonation-with-wcf"></a>WCF ile Temsilcilik ve Kimliğe Bürünme
*Kimliğe bürünme* , hizmetlerin, istemci erişimini bir hizmet etki alanı kaynaklarına kısıtlamak için kullandığı yaygın bir tekniktir. Hizmet etki alanı kaynakları, yerel dosyalar (kimliğe bürünme) gibi makine kaynakları ya da başka bir makinedeki bir dosya paylaşma (temsili) gibi bir kaynak olabilir. Örnek bir uygulama için bkz. [Istemcinin kimliğine bürünme](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Kimliğe bürünme özelliğinin nasıl kullanılacağına ilişkin bir örnek için bkz. [nasıl yapılır: bir hizmette Istemcinin kimliğine bürünme](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
> Bir hizmetin bir hizmette kimliğe bürünerek hizmetin, sunucu işleminden daha yüksek ayrıcalıklara sahip olabilecek istemci kimlik bilgileriyle çalıştığını unutmayın.  
  
## <a name="overview"></a>Genel bakış  
 Genellikle istemciler, hizmetin istemci adına bazı işlemleri gerçekleştirmesini sağlamak için bir hizmet çağırır. Kimliğe bürünme hizmeti, eylemi gerçekleştirirken hizmetin istemci olarak davranmasını sağlar. Temsili, bir ön uç hizmetinin istemcinin isteğini arka uç hizmetinin da istemcinin kimliğine bürünebileceği şekilde bir arka uç hizmetine iletmesini sağlar. Kimliğe bürünme en yaygın olarak, istemcinin belirli bir eylemi gerçekleştirme yetkisine sahip olup olmadığını kontrol etmenin bir yolu olarak kullanılır, ancak temsil, kimliğe bürünme yeteneklerini, istemcinin kimliğiyle birlikte bir arka uç hizmetine akar. Temsili, Kerberos tabanlı kimlik doğrulaması gerçekleştirildiğinde kullanılabilecek bir Windows etki alanı özelliğidir. Yetkilendirme, kimlik akışından farklıdır ve yetkilendirme, istemcinin parolasını elinde bulunmadan istemci kimliğine bürünme özelliğini aktardığından, kimlik akışından çok daha yüksek ayrıcalıklı bir işlemdir.  
  
 Hem kimliğe bürünme hem de temsil, istemcinin bir Windows kimliğine sahip olmasını gerektirir. Bir istemci bir Windows kimliğine sahip değilse, kullanılabilir tek seçenek, istemcinin kimliğini ikinci hizmete Flow ' dır.  
  
## <a name="impersonation-basics"></a>Kimliğe bürünme temelleri  
 Windows Communication Foundation (WCF), çeşitli istemci kimlik bilgileri için kimliğe bürünmeyi destekler. Bu konuda, bir hizmet yönteminin uygulanması sırasında çağıranın kimliğe bürünmesi için hizmet modeli desteği açıklanmaktadır. Ayrıca, bu senaryolarda kimliğe bürünme ve SOAP Güvenliği ve WCF seçeneklerini içeren yaygın dağıtım senaryolarından de bahsedildi.  
  
 Bu konu, SOAP güvenliği kullanılırken WCF 'de kimliğe bürünme ve temsili ile odaklanır. Aktarım güvenliği [Ile kimliğe bürünme kullanma](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)bölümünde açıklandığı gibi, aktarım GÜVENLIĞI kullanılırken WCF ile kimliğe bürünme ve temsil özelliğini de kullanabilirsiniz.  
  
## <a name="two-methods"></a>İki yöntem  
 WCF SOAP güvenliğinin, kimliğe bürünme işlemini gerçekleştirmek için iki ayrı yöntemi vardır. Kullanılan yöntem bağlamaya bağlıdır. Bunlardan biri, güvenlik desteği sağlayıcısı arabirimi (SSPI) veya Kerberos kimlik doğrulamasından alınan bir Windows belirtecinden kimliğe bürünme yoluyla, daha sonra hizmette önbelleğe alınır. İkincisi, toplu olarak *Service-for-User* (S4U) olarak adlandırılan Kerberos uzantılarından alınan bir Windows belirtecinden kimliğe bürünme özelliğine sahiptir.  
  
### <a name="cached-token-impersonation"></a>Önbelleğe alınmış belirteç kimliğe bürünme  
 Önbelleğe alınmış belirteç kimliğe bürünme işlemini aşağıda bulabilirsiniz:  
  
- Windows istemci kimlik bilgileriyle <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>ve <xref:System.ServiceModel.NetTcpBinding>.  
  
- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> kimlik bilgileri veya istemcinin, hizmetin geçerli bir Windows hesabıyla eşlenebilmesi için bir Kullanıcı adı kimlik bilgisi sunan bir standart bağlama <xref:System.ServiceModel.BasicHttpSecurityMode> <xref:System.ServiceModel.BasicHttpBinding>.  
  
- `true``requireCancellation` ayarlanmış bir Windows istemci kimlik bilgisi kullanan <xref:System.ServiceModel.Channels.CustomBinding>. (Özelliği şu sınıflarda kullanılabilir: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>ve <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Bağlamada güvenli bir konuşma kullanılıyorsa, `requireCancellation` özelliği de `true`ayarlanmış olmalıdır.  
  
- İstemcinin Kullanıcı adı kimlik bilgisi sunan herhangi bir <xref:System.ServiceModel.Channels.CustomBinding>. Bağlamada güvenli konuşma kullanılıyorsa, `requireCancellation` özelliği de `true`ayarlanmış olmalıdır.  
  
### <a name="s4u-based-impersonation"></a>S4U tabanlı kimliğe bürünme  
 Aşağıdaki ile S4U tabanlı kimliğe bürünme gerçekleştirebilirsiniz:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>ve <xref:System.ServiceModel.NetTcpBinding> hizmetin geçerli bir Windows hesabıyla eşlenebilmesi için sertifika istemci kimlik bilgileri.  
  
- `requireCancellation` özelliği `false`olarak ayarlanmış bir Windows istemci kimlik bilgisi kullanan <xref:System.ServiceModel.Channels.CustomBinding>.  
  
- Bir Kullanıcı adı veya Windows istemci kimlik bilgisi ve `requireCancellation` özelliği `false`olarak ayarlanan güvenli konuşma kullanan <xref:System.ServiceModel.Channels.CustomBinding>.  
  
 Hizmetin, istemcinin kimliğine bürünebileceği kapsam, hizmet hesabının kimliğe bürünme girişiminde bulunduğu ayrıcalıklara, kullanılan kimliğe bürünme türüne ve istemcinin izin verdiği kimliğe bürünme kapsamına bağlıdır.  
  
> [!NOTE]
> İstemci ve hizmet aynı bilgisayarda çalışırken ve istemci bir sistem hesabı altında çalışıyorsa (örneğin, `Local System` veya `Network Service`), durum bilgisi olan güvenlik bağlamı belirteçleri ile güvenli bir oturum oluşturulduğunda istemci kimliğine bürünülemez. Bir Windows form veya konsol uygulaması genellikle şu anda oturum açmış olan hesap altında çalışır, bu sayede hesaba varsayılan olarak kimliğe bürünme yapılabilir. Ancak, istemci bir ASP.NET sayfası olduğunda ve Bu sayfa IIS 6,0 veya IIS 7,0 ' de barındırılıyorsa, istemci varsayılan olarak `Network Service` hesabı altında çalışır. Güvenli oturumları destekleyen sistem tarafından sağlanmış tüm bağlamalar, varsayılan olarak durum bilgisi olmayan bir güvenlik bağlamı belirteci (SCT) kullanır. Ancak, istemci bir ASP.NET sayfalararsa ve durum bilgisi olan güvenlik oturumları kullanılıyorsa, istemciye kimliğe bürünme yapılamaz. Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Hizmet yönteminde kimliğe bürünme: bildirime dayalı model  
 Çoğu kimliğe bürünme senaryosunda, çağıran bağlamda hizmet yönteminin yürütülmesi yer alabilir. WCF, kullanıcının <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliğinde kimliğe bürünme gereksinimini belirtmesini sağlayarak bunu kolay hale getiren bir kimliğe bürünme özelliği sağlar. Örneğin, aşağıdaki kodda, WCF altyapısı `Hello` yöntemini yürütmeden önce çağıranı taklit eder. `Hello` yöntemi içindeki yerel kaynaklara erişme girişimleri, yalnızca kaynağın erişim denetim listesi (ACL) çağıran erişim ayrıcalıklarına izin veriyorsa başarılı olur. Kimliğe bürünme özelliğini etkinleştirmek için, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliğini, aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> ya da <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType><xref:System.ServiceModel.ImpersonationOption> sabit listesi değerlerinden birine ayarlayın.  
  
> [!NOTE]
> Bir hizmet, uzak istemciden daha yüksek kimlik bilgilerine sahip olduğunda, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği <xref:System.ServiceModel.ImpersonationOption.Allowed>olarak ayarlanırsa hizmetin kimlik bilgileri kullanılır. Diğer bir deyişle, düşük ayrıcalıklı bir kullanıcı kimlik bilgilerini sağlıyorsa, daha yüksek ayrıcalıklı bir hizmet yöntemi hizmetin kimlik bilgileriyle yürütür ve düşük ayrıcalıklı kullanıcının başka bir şekilde kullanamayacak kaynakları kullanabilir.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 WCF altyapısı, yalnızca çağıran tarafından bir Windows kullanıcı hesabıyla eşleştirilecek kimlik bilgileriyle doğrulandıysa çağıranın kimliğine bürünebilir. Hizmet, bir Windows hesabına eşlenemeyen bir kimlik bilgisi kullanarak kimlik doğrulaması yapacak şekilde yapılandırıldıysa, hizmet yöntemi yürütülmez.  
  
> [!NOTE]
> Windows XP 'de, bir durum bilgisi olan bir SCT oluşturulduysa kimliğe bürünme başarısız olur ve <xref:System.InvalidOperationException>olur. Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Bir hizmet yönteminde kimliğe bürünme: kesinlik temelli model  
 Bazen bir çağıranın, işlev için tüm hizmet yöntemini taklit etmesine gerek yoktur, ancak yalnızca bir bölümü için. Bu durumda, çağıranın Windows kimliğini hizmet yöntemi içinde edinin ve imperatively kimliğe bürünme işlemini gerçekleştirin. Bunu, <xref:System.Security.Principal.WindowsIdentity> sınıfının bir örneğini döndürmek ve örneği kullanmadan önce <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metodunu çağırmak için <xref:System.ServiceModel.ServiceSecurityContext> <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliğini kullanarak yapın.  
  
> [!NOTE]
> Kimliğe bürünme eylemini otomatik olarak dönüştürmek için Visual Basic`Using` ifadesini C# veya `using` ifadesini kullandığınızdan emin olun. İfadesini kullanmazsanız veya Visual Basic veya C#dışında bir programlama dili kullanıyorsanız, kimliğe bürünme düzeyini döndürtığınızdan emin olun. Bunun yapılmaması, hizmet reddi ve ayrıcalık yükselmesi saldırıları için temel oluşturur.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Tüm hizmet yöntemleri için kimliğe bürünme  
 Bazı durumlarda, arayanın bağlamında bir hizmetin tüm yöntemlerini gerçekleştirmeniz gerekir. Bu özelliği Yöntem temelinde açıkça etkinleştirmek yerine <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>kullanın. Aşağıdaki kodda gösterildiği gibi, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> özelliğini `true`olarak ayarlayın. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>, <xref:System.ServiceModel.ServiceHost> sınıfının davranış koleksiyonlarından alınır. Ayrıca, her metoda uygulanan <xref:System.ServiceModel.OperationBehaviorAttribute> `Impersonation` özelliğinin ayrıca <xref:System.ServiceModel.ImpersonationOption.Allowed> ya da <xref:System.ServiceModel.ImpersonationOption.Required>olarak ayarlanması gerektiğini unutmayın.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Aşağıdaki tabloda, `ImpersonationOption` ve `ImpersonateCallerForAllServiceOperations`tüm olası birleşimleri için WCF davranışı açıklanmaktadır.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Davranış|  
|---------------------------|------------------------------------------------|--------------|  
|Gerekli|yok|WCF Çağrıyı taklit eder|  
|İzin Verildi|{1&gt;false&lt;1}|WCF, çağıranın kimliğine bürünemez|  
|İzin Verildi|true|WCF Çağrıyı taklit eder|  
|NotAllowed|{1&gt;false&lt;1}|WCF, çağıranın kimliğine bürünemez|  
|NotAllowed|true|Veril. (Bir <xref:System.InvalidOperationException> oluşturulur.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Windows kimlik bilgileri ve önbelleğe alınmış belirteç kimliğe bürünme ile edinilen kimliğe bürünme düzeyi  
 Bazı senaryolarda, istemci bir Windows istemci kimlik bilgisi kullanıldığında hizmetin gerçekleştirdiği kimliğe bürünme düzeyi üzerinde kısmi denetime sahiptir. İstemci anonim kimliğe bürünme düzeyi belirttiğinde bir senaryo meydana gelir. Diğer bir deyişle, önbelleğe alınmış bir belirteçle kimliğe bürünme işlemi gerçekleştirilirken meydana gelir. Bu, genel <xref:System.ServiceModel.ChannelFactory%601> sınıfının bir özelliği olarak erişilen <xref:System.ServiceModel.Security.WindowsClientCredential> sınıfının <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği ayarlanarak yapılır.  
  
> [!NOTE]
> Kimliğe bürünme düzeyi belirtilmesi, istemcinin hizmette anonim olarak oturum açmasına neden olur. Bu nedenle, kimliğe bürünme işleminin gerçekleştirilip gerçekleştirilmediğine bakılmaksızın hizmetin anonim oturum açmalarına izin vermelidir.  
  
 İstemci kimliğe bürünme düzeyini <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>veya <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>olarak belirtebilir. Aşağıdaki kodda gösterildiği gibi, yalnızca belirtilen düzeydeki bir belirteç oluşturulur.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Aşağıdaki tablo, önbelleğe alınmış bir belirteçle kimliğe bürünme sırasında hizmetin aldığı kimliğe bürünme düzeyini belirtir.  
  
|`AllowedImpersonationLevel` değeri|Hizmette `SeImpersonatePrivilege`|Hizmet ve istemci, temsilciliğini alabilir|Önbelleğe alınmış belirteç `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Deðeri|Evet|yok|Kimliğe bürünme|  
|Deðeri|Hayır|yok|Kimlik|  
|Kimlik|yok|yok|Kimlik|  
|Kimliğe bürünme|Evet|yok|Kimliğe bürünme|  
|Kimliğe bürünme|Hayır|yok|Kimlik|  
|Verilmesini|Evet|Evet|Verilmesini|  
|Verilmesini|Evet|Hayır|Kimliğe bürünme|  
|Verilmesini|Hayır|yok|Kimlik|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Kullanıcı adı kimlik bilgilerinden alınan kimliğe bürünme düzeyi ve önbelleğe alınmış belirteç kimliğe bürünme  
 İstemci, hizmetin Kullanıcı adını ve parolasını geçirerek, WCF 'nin Kullanıcı olarak oturum açmasına olanak sağlar ve bu da `AllowedImpersonationLevel` özelliğini <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>olarak ayarlamaya eşdeğerdir. (`AllowedImpersonationLevel` <xref:System.ServiceModel.Security.WindowsClientCredential> ve <xref:System.ServiceModel.Security.HttpDigestClientCredential> sınıflarında kullanılabilir.) Aşağıdaki tablo, hizmet Kullanıcı adı kimlik bilgilerini aldığında elde edilen kimliğe bürünme düzeyini sağlar.  
  
|`AllowedImpersonationLevel`|Hizmette `SeImpersonatePrivilege`|Hizmet ve istemci, temsilciliğini alabilir|Önbelleğe alınmış belirteç `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|yok|Evet|Evet|Verilmesini|  
|yok|Evet|Hayır|Kimliğe bürünme|  
|yok|Hayır|yok|Kimlik|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>S4U tabanlı kimliğe bürünme 'den edinilen kimliğe bürünme düzeyi  
  
|Hizmette `SeTcbPrivilege`|Hizmette `SeImpersonatePrivilege`|Hizmet ve istemci, temsilciliğini alabilir|Önbelleğe alınmış belirteç `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Evet|Evet|yok|Kimliğe bürünme|  
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
  
## <a name="delegation"></a>Verilmesini  
 Bir arka uç hizmetine temsilci seçmek için, bir hizmet, istemcinin Windows kimliğini kullanarak Kerberos Multi-BAI (NTLM geri dönüşü olmadan SSPI) veya arka uç hizmetine Kerberos doğrudan kimlik doğrulaması gerçekleştirmelidir. Bir arka uç hizmetine temsilci seçmek için bir <xref:System.ServiceModel.ChannelFactory%601> ve kanal oluşturun ve sonra istemciyi taklit ederken kanal üzerinden iletişim kurun. Bu tür bir temsilciyle, arka uç hizmetinin ön uç hizmetinden konumlandırıldığı mesafe ön uç hizmeti tarafından elde edilen kimliğe bürünme düzeyine bağlıdır. Kimliğe bürünme düzeyi <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>olduğunda, ön uç ve arka uç hizmetlerinin aynı makinede çalışıyor olması gerekir. Kimliğe bürünme düzeyi <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>olduğunda, ön uç ve arka uç hizmetleri ayrı makinelerde veya aynı makinede olabilir. Temsili düzeyi kimliğe bürünme özelliğinin etkinleştirilmesi için Windows etki alanı ilkesinin temsilciliğe izin verecek şekilde yapılandırılması gerekir. Temsilci desteği için Active Directory yapılandırma hakkında daha fazla bilgi için bkz. [temsilci kimlik doğrulamasını etkinleştirme](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc780217(v=ws.10)).  
  
> [!NOTE]
> İstemci, arka uç hizmetindeki bir Windows hesabına karşılık gelen bir Kullanıcı adı ve parola kullanarak ön uç hizmetinde kimlik doğrulaması gerçekleştiriyorsa, ön uç hizmeti istemcinin kullanıcı adını ve parolasını yeniden kullanarak arka uç hizmetinde kimlik doğrulaması yapabilir. Bu özellikle güçlü bir kimlik akışı biçimidir, çünkü arka uç hizmetine Kullanıcı adı ve parola geçirme, arka uç hizmetinin kimliğe bürünme işlemini gerçekleştirmesini sağlar ancak Kerberos kullanılmadığından, temsilciyi oluşturmaz. Active Directory denetimleri, Kullanıcı adı ve parola kimlik doğrulaması için geçerlidir.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Kimliğe bürünme düzeyi Işlevi olarak temsil yeteneği  
  
|Kimliğe bürünme düzeyi|Hizmet, işlemler arası temsili gerçekleştirebilir|Hizmet, makineler arası temsili gerçekleştirebilir|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Hayır|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Evet|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Evet|Evet|  
  
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
- [Aktarım Güvenliği ile Kimliğe Bürünme Kullanma](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)
- [İstemci Kimliğine Bürünme](../../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
