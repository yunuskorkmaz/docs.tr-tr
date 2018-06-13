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
ms.openlocfilehash: 811ab308b881b5209d44612b29fb51d1c79e8bf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496925"
---
# <a name="delegation-and-impersonation-with-wcf"></a>WCF ile Temsilcilik ve Kimliğe Bürünme
*Kimliğe bürünme* bir hizmeti etki alanı kaynaklarına istemci erişimini kısıtlamak için hizmetlerini kullanan ortak bir tekniktir. Hizmeti etki alanı kaynaklarına ya da yerel dosyaları (kimliğe bürünme) gibi makine kaynakları veya bir dosya paylaşımı (temsilci) gibi başka bir makinede bir kaynak olabilir. Örnek bir uygulama için bkz: [istemci kimliğine bürünme](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Kimliğe bürünme kullanma örneği için bkz: [nasıl yapılır: bir hizmete bir istemcinin kimliğine bürünmek](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
>  Bir hizmet bir istemcide belirlerken hizmet sunucu işlemi daha yüksek ayrıcalıkları olabilir istemcinin kimlik bilgileriyle çalıştığını unutmayın.  
  
## <a name="overview"></a>Genel Bakış  
 Genellikle, istemciler istemci adına bazı eylemler gerçekleştirme hizmet sağlamak için bir hizmet çağırın. Kimliğe bürünme hizmetinin eylem gerçekleştirilirken istemcisi gibi davranmasını sağlar. Temsilci istemcinin isteği arka uç hizmeti istemci bürünebilir şekilde arka uç hizmetine iletmek bir ön uç hizmeti sağlar. Kimliğe bürünme bir istemci temsilci şekilde bir arka uç hizmeti istemcinin kimliğini, birlikte boyunca kimliğe bürünme yetenekleri olsa da, belirli bir eylemi gerçekleştirmek için yetkili olup olmadığını denetleme bir yolu olarak en yaygın olarak kullanılır. Temsilci Kerberos tabanlı kimlik doğrulaması yapıldığında, kullanılabilir bir Windows etki alanı özelliğidir. Temsilci kimlik akışından farklıdır ve temsilci istemcinin parola elinde olmadan istemci kimliğine bürünme özelliğini aktardığından, bir çok daha yüksek ayrıcalıklı kimlik akış daha işlemdir.  
  
 Kimliğe bürünme ve temsilci istemci Windows kimliğe sahip olmasını gerektirir. Bir istemci bir Windows kimliğine sahip değil, kullanılabilir tek seçenek, istemcinin kimliğini ikinci hizmetine akması şeklindedir.  
  
## <a name="impersonation-basics"></a>Kimliğe bürünme temelleri  
 Windows Communication Foundation (WCF), bir dizi istemci kimlik bilgileri için kimliğe bürünme özelliğini destekler. Bu konu hizmet modeli desteği, bir hizmet yöntemin kullanımı sırasında arayan taklit açıklar. Ayrıca ele alınan olan kimliğe bürünme ve SOAP Güvenliği ve bu senaryolarda WCF seçenekleri içeren ortak dağıtım senaryoları.  
  
 Bu konuda kimliğe bürünme ve temsilci olarak WCF SOAP Güvenliği kullanırken odaklanır. Kimliğe bürünme ve temsilci WCF ile taşıma güvenliği kullanırken açıklandığı gibi kullanabilirsiniz [taşıma güvenliği ile kimliğe bürünme kullanarak](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>İki yöntemi  
 WCF SOAP Güvenliği kimliğe bürünme gerçekleştirmek için iki farklı yöntem vardır. Kullanılan yöntem bağlamada bağlıdır. Kimliğe bürünme hizmette sonra önbelleğe Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI) veya Kerberos kimlik doğrulaması alınan bir Windows belirtecine gelen biridir. Kimliğe bürünme topluca adlı Kerberos uzantılardan elde Windows belirteci gelen saniyedir *Service-for-User* (S4U).  
  
### <a name="cached-token-impersonation"></a>Önbelleğe alınan belirteç kimliğe bürünme  
 Aşağıdaki ile önbelleğe alınmış belirteci kimliğe bürünme gerçekleştirebilirsiniz:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, ve <xref:System.ServiceModel.NetTcpBinding> bir Windows istemcisi kimlik bilgisi.  
  
-   <xref:System.ServiceModel.BasicHttpBinding> ile bir <xref:System.ServiceModel.BasicHttpSecurityMode> kümesine <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> kimlik bilgisi veya istemci hizmeti için geçerli bir Windows hesabı eşleyebilirsiniz bir kullanıcı adı kimlik bilgisi nerede sunar diğer standart bağlama.  
  
-   Tüm <xref:System.ServiceModel.Channels.CustomBinding> sahip bir Windows istemcisi kimlik bilgisi kullanan `requireCancellation` kümesine `true`. (Aşağıdaki sınıflarında özelliği kullanılabilir: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, ve <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Güvenli Konuşmayla bağlamada kullanılırsa, ayrıca olmalıdır `requireCancellation` özelliğini `true`.  
  
-   Tüm <xref:System.ServiceModel.Channels.CustomBinding> istemci bir kullanıcı adı kimlik bilgisi nerede sayısını gösterir. Güvenli Konuşmayla bağlamada kullanılırsa, ayrıca olmalıdır `requireCancellation` özelliğini `true`.  
  
### <a name="s4u-based-impersonation"></a>S4U tabanlı kimliğe bürünme  
 Şu kimliğe bürünme S4U tabanlı gerçekleştirebilirsiniz:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, ve <xref:System.ServiceModel.NetTcpBinding> hizmet için geçerli bir Windows hesabı eşleyebilirsiniz bir sertifika istemci kimlik bilgisi.  
  
-   Tüm <xref:System.ServiceModel.Channels.CustomBinding> sahip bir Windows istemcisi kimlik bilgisi kullanan `requireCancellation` özelliğini `false`.  
  
-   Tüm <xref:System.ServiceModel.Channels.CustomBinding> kullanan bir kullanıcı adı veya Windows istemcisi kimlik bilgisi ve güvenli Konuşmayla `requireCancellation` özelliğini `false`.  
  
 Hizmet istemci bürünebilir ölçüde hizmet hesabı kimliğe bürünme, tür kullanılan kimliğe bürünme ve büyük olasılıkla istemcinin verir kimliğe bürünme kapsamını çalıştığında tutan ayrıcalıklarını bağlıdır.  
  
> [!NOTE]
>  Ne zaman istemci hem de hizmet aynı bilgisayarda çalışan ve istemci bir sistem hesabı altında çalışan (örneğin, `Local System` veya `Network Service`), güvenli bir oturum ile durum bilgisi olan güvenlik bağlamı kurulduğunda istemci bürünülemez belirteçleri. Böylece hesap varsayılan olarak taklit edilebileceğini bir Windows Form veya konsol uygulaması genellikle geçerli oturum açma hesabı altında çalışır. Ancak, istemci olduğunda bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sayfa ve bu sayfa barındırılan [!INCLUDE[iis601](../../../../includes/iis601-md.md)] veya [!INCLUDE[iisver](../../../../includes/iisver-md.md)], istemci altında çalıştırın. ardından, `Network Service` varsayılan hesabı. Güvenli oturumlar destek sistem tarafından sağlanan bağlamalar tümünün varsayılan olarak bir durum bilgisi olmayan güvenlik bağlamı belirteci (SCT) kullanın. Ancak, istemci ise bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sayfası ve durum bilgisi olan SCTs ile güvenli oturumlar kullanılıyorsa, istemci bürünülemez. Durum bilgisi olan SCTs güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Bir hizmet yöntemi, kimliğe bürünme: bildirim temelli modeli  
 Çoğu kimliğe bürünme senaryoları hizmet yöntemini çağıran bağlamda yürütmenin içerir. WCF sağlar, bu kullanıcının kimliğe bürünme gereksinimini belirtmesine olanak tanıyarak yapılacağı kolaylaştırır bir kimliğe bürünme özelliği <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği. Örneğin, aşağıdaki kodda, WCF altyapı çağıran yürütmeden önce taklit `Hello` yöntemi. Herhangi bir deneyin içinde yerel kaynaklara erişmek `Hello` yöntemi başarılı yalnızca kaynağın erişim denetim listesi (ACL) arayan veriyorsa erişim ayrıcalıkları. Kimliğe bürünme özelliğini etkinleştirmek için ayarlanmış <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliğini birine <xref:System.ServiceModel.ImpersonationOption> numaralandırma değerleri, ya da <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> veya <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, aşağıdaki örnekte gösterildiği gibi.  
  
> [!NOTE]
>  Bir hizmeti uzak istemci daha yüksek kimlik bilgileri olduğunda, hizmetin kimlik bilgileri kullanılır <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği ayarlanmış <xref:System.ServiceModel.ImpersonationOption.Allowed>. Diğer bir deyişle, düşük ayrıcalıklı bir kullanıcının kimlik bilgilerini sağlıyorsa, daha yüksek ayrıcalıklı hizmeti hizmetin kimlik bilgileri yöntemiyle yürütür ve düşük ayrıcalıklı kullanıcı aksi kullanmanız mümkün olmayacaktır kaynakları kullanabilir.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 Çağrıyı yapan bir Windows kullanıcı hesabıyla eşlenir kimlik bilgileri ile doğrulanırsa WCF altyapı çağıran kimliğine bürünebilir. Hizmet, bir Windows hesabı eşlenemiyor kimlik bilgilerini kullanarak kimlik doğrulaması için yapılandırılmışsa, hizmet yöntemi yürütülemiyor.  
  
> [!NOTE]
>  Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)], kimliğe bürünme başarısız olursa SCT oluşturulur, sonuçta bir durum bilgisi olan bir <xref:System.InvalidOperationException>. Daha fazla bilgi için bkz: [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Bir hizmet yöntemi, kimliğe bürünme: kesinlik temelli modeli  
 Bazen çağıran işlevi, ancak yalnızca bir kısmının tüm hizmet yöntemi taklit gerekmez. Bu durumda, çağıran hizmet yöntemi içinde Windows kimliğini almak ve kimliğe bürünme imperatively gerçekleştirin. Kullanarak bunu <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği <xref:System.ServiceModel.ServiceSecurityContext> bir örneğini döndürmek için <xref:System.Security.Principal.WindowsIdentity> sınıfı ve arama <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> örneğini kullanmadan önce yöntemi.  
  
> [!NOTE]
>  Visual Basic kullandığınızdan emin olun`Using` deyimi veya C# `using` deyimi kimliğe bürünme eylemi otomatik olarak geri döndürüyoruz. Deyim kullanmayın veya Visual Basic veya C# dışında bir programlama dili kullanıyorsanız, kimliğe bürünme düzeyi dönmek emin olun. Bunu yapmak için hata hizmet reddi ve ayrıcalıkların yükseltilmesi saldırılarını temelini.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Tüm hizmet yöntemleri için kimliğe bürünme  
 Bazı durumlarda, bir hizmetin arayanın bağlamında tüm yöntemleri gerçekleştirmeniz gerekir. Bu özellik yöntemi başına temelinde açıkça etkinleştirmek yerine kullanmak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Aşağıdaki kodda gösterildiği gibi ayarlamak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> özelliğine `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Davranışlarını koleksiyonlarından alınan <xref:System.ServiceModel.ServiceHost> sınıfı. Ayrıca `Impersonation` özelliği <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanan kadar her yöntemi de ayarlanması gerekir ya da çok <xref:System.ServiceModel.ImpersonationOption.Allowed> veya <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Aşağıdaki tabloda tüm olası kombinasyonu için WCF davranışını tanımlar `ImpersonationOption` ve `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Davranış|  
|---------------------------|------------------------------------------------|--------------|  
|Gerekli|yok|WCF çağıran temsil eder|  
|İzin verilen|false|WCF çağıran kimliğine bürünmek değil|  
|İzin verilen|true|WCF çağıran temsil eder|  
|QueuedDeliveryRequirements|false|WCF çağıran kimliğine bürünmek değil|  
|QueuedDeliveryRequirements|true|İzin verilmiyor. (Bir <xref:System.InvalidOperationException> atılır.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Kimliğe bürünme düzeyi'Windows kimlik bilgileri elde ve belirteç kimliğe bürünme önbelleğe  
 Bazı senaryolarda istemci hizmeti bir Windows istemcisi kimlik bilgisi kullanıldığında gerçekleştirir kimliğe bürünme düzeyini kısmi denetime sahiptir. Bir senaryo oluşur. istemcinin anonim kimliğe bürünme düzeyini belirtir. Diğer bir önbelleğe alınan belirteci ile kimliğe bürünme gerçekleştirirken oluşur. Bu ayarlayarak yapılır <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> genel bir özellik olarak erişilen sınıfı <xref:System.ServiceModel.ChannelFactory%601> sınıfı.  
  
> [!NOTE]
>  Kimliğe bürünme düzeyi anonim belirtilmesi hizmetine anonim olarak oturum açmak istemci neden olur. Hizmet, bu nedenle kimliğe bürünme gerçekleştirilip bağımsız olarak anonim oturumları izin vermelidir.  
  
 İstemcinin kimliğe bürünme düzeyi olarak belirtebilirsiniz <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, veya <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Aşağıdaki kodda gösterildiği gibi bir belirteç yalnızca belirtilen düzeyinde oluşturulur.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Aşağıdaki tabloda bir önbelleğe alınan belirtecinden belirlerken hizmet edinir kimliğe bürünme düzeyini belirtir.  
  
|`AllowedImpersonationLevel` Değer|Hizmet var `SeImpersonatePrivilege`|Hizmet ve istemci için temsilci seçme özelliği|Önbelleğe alınan belirteci `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonim|Evet|yok|Kimliğe bürünme|  
|Anonim|Hayır|yok|Tanımlama|  
|Tanımlama|yok|yok|Tanımlama|  
|Kimliğe bürünme|Evet|yok|Kimliğe bürünme|  
|Kimliğe bürünme|Hayır|yok|Tanımlama|  
|Temsilci seçme|Evet|Evet|Temsilci seçme|  
|Temsilci seçme|Evet|Hayır|Kimliğe bürünme|  
|Temsilci seçme|Hayır|yok|Tanımlama|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Kimliğe bürünme düzeyi'kullanıcı adı kimlik bilgileri elde ve belirteç kimliğe bürünme önbelleğe  
 Hizmetin kullanıcı adı ve parola geçirerek, bir istemci ayarı için eşdeğer bir gruba bu kullanıcı olarak oturum açmak WCF sağlar `AllowedImpersonationLevel` özelliğine <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. ( `AllowedImpersonationLevel` Kullanılabilir <xref:System.ServiceModel.Security.WindowsClientCredential> ve <xref:System.ServiceModel.Security.HttpDigestClientCredential> sınıfları.) Aşağıdaki tabloda hizmetin kullanıcı adı kimlik bilgilerini aldığında düzeyi elde kimliğe bürünme sağlar.  
  
|`AllowedImpersonationLevel`|Hizmet var `SeImpersonatePrivilege`|Hizmet ve istemci için temsilci seçme özelliği|Önbelleğe alınan belirteci `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|yok|Evet|Evet|Temsilci seçme|  
|yok|Evet|Hayır|Kimliğe bürünme|  
|yok|Hayır|yok|Tanımlama|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Kimliğe bürünme S4U tabanlı elde edilen kimliğe bürünme düzeyi  
  
|Hizmet var `SeTcbPrivilege`|Hizmet var `SeImpersonatePrivilege`|Hizmet ve istemci için temsilci seçme özelliği|Önbelleğe alınan belirteci `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Evet|Evet|yok|Kimliğe bürünme|  
|Evet|Hayır|yok|Tanımlama|  
|Hayır|yok|yok|Tanımlama|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Bir Windows hesabı için bir istemci sertifikası eşleme  
 Bir istemci bir sertifika kullanarak bir hizmet için kendi kimliğini doğrulamak ve var olan bir hesabı Active Directory üzerinden istemciye hizmet eşlemesi için mümkündür. Aşağıdaki XML sertifika eşlemek için hizmetinin nasıl yapılandırılacağı gösterilmektedir.  
  
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
  
 Aşağıdaki kod hizmetinin nasıl yapılandırılacağı gösterilmektedir.  
  
```  
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>Temsilci seçme  
 Kerberos kimlik doğrulaması Windows kimliğini kullanarak arka uç hizmetine doğrudan veya bir arka uç hizmetine temsilci seçmek için bir hizmet bir Kerberos çok leg (SSPI NTLM geri dönüş olmadan'i) gerçekleştirebilirsiniz. Bir arka uç hizmeti temsilci seçmesine oluşturmak bir <xref:System.ServiceModel.ChannelFactory%601> ve bir kanal ve sonra istemci kimliğine bürünme sırasında kanal aracılığıyla iletişim kurar. Bu temsilci form ile ön uç hizmeti tarafından elde kimliğe bürünme düzeyi, arka uç hizmeti ön uç hizmetinden bulunabilir uzaklığı bağlıdır. Kimliğe bürünme düzeyi olduğunda <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, ön uç ve arka uç hizmetlerini aynı makinede çalıştırması gerekir. Kimliğe bürünme düzeyi olduğunda <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, ön uç ve arka uç hizmetlerini ayrı makinelerde ya da aynı makine üzerindeki olabilir. Temsilci düzeyi kimliğe bürünme özelliğini etkinleştirme Windows etki alanı ilkesi temsilci izin verecek şekilde yapılandırılmasını gerektirir. Active Directory temsilci desteği için yapılandırma hakkında daha fazla bilgi için bkz: [temsilci kimlik doğrulamasını etkinleştirme](http://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
>  Bir kullanıcı adı ve bir Windows hesabı arka uç hizmetine karşılık gelen parola kullanarak ön uç hizmeti için bir istemci kimlik doğrulaması gerçekleştirdiğinde ön uç hizmeti istemcinin kullanıcı adınızı ve parolanızı yeniden kullanarak arka uç hizmetine doğrulayabilir. Bu özellikle güçlü kimlik akış, kullanıcı adı geçirme çünkü biçimidir ve kimliğe bürünme gerçekleştirmek için arka uç hizmetini arka uç hizmetine parola sağlar, ancak Kerberos kullanılmadığından, temsilci niteliğinde değildir. Temsilci Active Directory denetimlerinde kullanıcı adı ve parola kimlik doğrulaması için geçerli değildir.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Kimliğe bürünme düzeyi bir işlevi olarak temsilci seçme olanağı  
  
|Kimliğe bürünme düzeyi|Çapraz işlem temsilci hizmeti gerçekleştirebilir|Hizmet makineler arası temsilci gerçekleştirebilirsiniz|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Hayır|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Evet|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Evet|Evet|  
  
 Aşağıdaki kod örneğinde, temsili kullanmak üzere gösterilmiştir.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Kısıtlanmış temsili kullanmak üzere bir uygulama yapılandırma  
 İçin önce kullanım Kısıtlı temsilci, gönderen, alıcı ve bunu yapmak için etki alanı denetleyicisinin yapılandırılması gerekir. Aşağıdaki yordamı Kısıtlanmış temsilci etkinleştirme adımları listeler. Bölümü temsilci ile Kısıtlanmış temsilci arasındaki farklar hakkında daha fazla bilgi için bkz [Windows Server 2003 Kerberos uzantıları](http://go.microsoft.com/fwlink/?LinkId=100194) kısıtlanmış tartışma açıklanır.  
  
1.  Etki alanı denetleyicisinde temizleyin **Hesap duyarlıdır ve devredilemez** istemci uygulamasının altında çalıştığı hesap için onay kutusunu.  
  
2.  Etki alanı denetleyicisinde seçin **hesabıdır temsilci olarak güvenilir** istemci uygulamasının altında çalıştığı hesap için onay kutusunu.  
  
3.  Temsilci olarak güvenilir tıklayarak orta katman bilgisayarın etki alanı denetleyicisinde yapılandırın **bilgisayara temsilci seçmek için güven** seçeneği.  
  
4.  Etki alanı denetleyicisinde tıklayarak kısıtlanmış temsili kullanmak üzere orta katman bilgisayarı yapılandırma **bu bilgisayara yalnızca belirtilen hizmetlere temsilci seçmek için güven** seçeneği.  
  
 Kısıtlanmış temsilci seçmeyi yapılandırma hakkında daha ayrıntılı yönergeler için MSDN'de bulunan aşağıdaki konulara bakın:  
  
-   [Kerberos temsilcisi seçme sorunlarını giderme](http://go.microsoft.com/fwlink/?LinkId=36724)  
  
-   [Kerberos protokol geçişi ve Kısıtlanmış temsilci seçme](http://go.microsoft.com/fwlink/?LinkId=36725)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>  
 <xref:System.ServiceModel.ImpersonationOption>  
 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>  
 <xref:System.ServiceModel.ServiceSecurityContext>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ChannelFactory%601>  
 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>  
 [Aktarım Güvenliği ile Kimliğe Bürünme Kullanma](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [İstemci Kimliğine Bürünme](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
