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
ms.openlocfilehash: 4f86636cd244ce53ed00f80b38777e78a3278d6f
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912500"
---
# <a name="delegation-and-impersonation-with-wcf"></a>WCF ile Temsilcilik ve Kimliğe Bürünme
*Kimliğe bürünme* Hizmetleri İstemci Erişim hizmeti etki alanının kaynaklarına erişimi kısıtlama kullanmak yaygın bir tekniktir. Hizmeti etki alanı kaynaklarına ya da yerel dosyaları (kimliğe bürünme) gibi makine kaynakları veya bir dosya paylaşımı (temsilci) gibi başka bir makinedeki bir kaynak olabilir. Örnek bir uygulama için bkz: [istemci kimliğine bürünme](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Kimliğe bürünme kullanma örneği için bkz: [nasıl yapılır: Bir hizmette istemci kimliğine bürünme](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
>  Bir hizmette istemci kimliğine bürünme, hizmet sunucu işlemi daha yüksek ayrıcalıklara sahip olabilecek istemcinin kimlik bilgileriyle çalıştığını unutmayın.  
  
## <a name="overview"></a>Genel Bakış  
 Genellikle, istemcileri istemci adına bazı eylemler gerçekleştirme hizmet için bir hizmet çağırın. Kimliğe bürünme hizmet eylem gerçekleştirilirken istemci gibi davranmasını sağlar. Temsilci seçme, istemcinin isteği arka uç hizmeti istemci kimliğine bürünür şekilde arka uç hizmetine iletmek bir ön uç hizmeti sağlar. Kimliğe bürünme, temsilci istemci kimliğini, birlikte akışı sağlama kimliğe bürünme özelliklerinin bir arka uç hizmeti için bir yol olsa da, belirli bir eylemi gerçekleştirmek için bir istemci yetki verilip verilmediğini denetleme bir yolu olarak en yaygın olarak kullanılır. Temsilci Kerberos tabanlı kimlik doğrulaması yapıldığında, kullanılabilir bir Windows etki alanı özelliğidir. Temsilci kimlik akıştan farklıdır ve temsilci istemcinin parola elinde olmadan istemci kimliğine bürünme özelliğini aktardığından bir çok daha yüksek ayrıcalıklı kimlik akış daha işlemdir.  
  
 Kimliğe bürünme hem temsilci istemci bir Windows kimliği olduğunu gerektirir. Bir istemci bir Windows kimliği sahip değil, kullanılabilecek tek seçenek, ikinci bir hizmete istemcinin kimliğini akması şeklindedir.  
  
## <a name="impersonation-basics"></a>Kimliğe bürünme temelleri  
 Windows Communication Foundation (WCF) çeşitli istemci kimlik bilgileri için kimliğe bürünme özelliğini destekler. Bu konu, bir hizmet yöntemin uygulanmasını sırasında çağıranın kimliğine bürünmek için hizmet modeli desteğini açıklar. Olan kimliğe bürünme ve SOAP Güvenliği ve bu senaryolarda WCF seçenekleri ile ilgili sık karşılaşılan dağıtım senaryoları da bahsedilmiştir.  
  
 Bu konu, SOAP Güvenliği kullanıldığında kimliğe bürünme ve temsilci wcf'de odaklanır. Kimliğe bürünme ve temsilci WCF ile Aktarım güvenliği kullanırken açıklandığı kullanabilirsiniz [aktarım güvenliği ile kimliğe bürünme özelliğini kullanarak](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>İki yöntemi  
 WCF SOAP Güvenliği kimliğe bürünme gerçekleştirmek için iki farklı yöntem vardır. Kullanılan yöntem noktasındaki bağlama bağlıdır. Kimliğe bürünme bir Windows belirteçten sonra hizmette önbelleğe alınan Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI) veya Kerberos kimlik doğrulaması alınan biridir. Kimliğe bürünme bir Windows belirteçten topluca adlı Kerberos extensions elde ikincisinin *kullanıcı için hizmet* (S4U).  
  
### <a name="cached-token-impersonation"></a>Önbelleğe alınan belirteç kimliğe bürünme  
 Önbelleğe alınan belirteç kimliğe bürünme ile aşağıdakileri gerçekleştirebilirsiniz:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, ve <xref:System.ServiceModel.NetTcpBinding> Windows istemci kimlik bilgileri.  
  
- <xref:System.ServiceModel.BasicHttpBinding> ile bir <xref:System.ServiceModel.BasicHttpSecurityMode> kümesine <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> kimlik bilgisi ve diğer istemci hizmeti için geçerli bir Windows hesabı eşleyebilirsiniz bir kullanıcı adı kimlik bilgisi nerede sunar standart bağlama.  
  
- Tüm <xref:System.ServiceModel.Channels.CustomBinding> ile Windows istemci kimlik bilgilerini kullanan `requireCancellation` kümesine `true`. (Aşağıdaki sınıflarda özellik kullanılabilir: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, ve <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Güvenli konuşma bağlamadaki kullanılırsa, ayrıca olmalıdır `requireCancellation` özelliğini `true`.  
  
- Tüm <xref:System.ServiceModel.Channels.CustomBinding> istemci bir kullanıcı adı kimlik bilgisi nerede sunar. Güvenli konuşma bağlamadaki kullanılır, ayrıca olmalıdır `requireCancellation` özelliğini `true`.  
  
### <a name="s4u-based-impersonation"></a>Kimliğe bürünme S4U tabanlı  
 S4U tabanlı kimliğe bürünme ile aşağıdakileri gerçekleştirebilirsiniz:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, ve <xref:System.ServiceModel.NetTcpBinding> , hizmet için geçerli bir Windows hesabı eşleyebilirsiniz sertifika istemci kimlik bilgileri.  
  
- Tüm <xref:System.ServiceModel.Channels.CustomBinding> ile Windows istemci kimlik bilgilerini kullanan `requireCancellation` özelliğini `false`.  
  
- Tüm <xref:System.ServiceModel.Channels.CustomBinding> kullanan bir kullanıcı adı veya Windows istemcisi kimlik bilgisi ve güvenli Konuşmayla `requireCancellation` özelliğini `false`.  
  
 Hizmet istemci kimliğine bürünür ölçüde hizmet hesabı kimliğe bürünme, kimliğe bürünme kullanılan tür ve büyük olasılıkla istemci verir kimliğe bürünme kapsamını çalıştığında tutan ayrıcalıklarını bağlıdır.  
  
> [!NOTE]
>  Ne zaman aynı bilgisayarda çalışan istemci ve hizmet ve istemci bir sistem hesabı altında çalışıyor (örneğin, `Local System` veya `Network Service`), durum bilgisi olan güvenlik bağlamı ile güvenli bir oturum kurulduktan sonra istemci veritabanının özellikleri alınamaz belirteçleri. Böylece hesap varsayılan olarak taklit edilebileceğini bir Windows Form veya konsol uygulaması, genellikle oturum açtığınız hesap altında çalışır. Ancak, istemci olduğunda bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sayfası ve bu sayfayı barındırılan [!INCLUDE[iis601](../../../../includes/iis601-md.md)] veya [!INCLUDE[iisver](../../../../includes/iisver-md.md)], istemci altında çalıştırırsanız `Network Service` varsayılan hesabı. Tüm güvenli oturumlar destekleyen sistem tarafından sağlanan bağlamaları, varsayılan olarak bir durum bilgisi olmayan güvenlik bağlamı belirteci (SCT) kullanın. Ancak, istemci bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sayfası ve durum bilgisi olan SCTs ile güvenli oturumlar kullanılıyorsa, istemci veritabanının özellikleri alınamaz. Durum bilgisi olan SCTs güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Kimliğe bürünme hizmet yöntemi içinde: Bildirim temelli modeli  
 Kimliğe bürünme senaryo, hizmet yöntemi arayan bağlamda yürütülmesi gerekebilir. WCF sağlar, bu kimliğe bürünme gereksinimini belirtmesini sağlayarak yapmasını kolaylaştırır bir kimliğe bürünme özelliği <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği. Örneğin, aşağıdaki kodda, WCF altyapısı çağrıyı yürütmeden önce taklit `Hello` yöntemi. Yapmaya içinde yerel kaynaklara erişmeye `Hello` yöntemi yalnızca kaynak erişim denetimi listesi (ACL) çağıranın izin veriyorsa başarılı erişim ayrıcalıkları. Kimliğe bürünme özelliğini etkinleştirmek için <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliğini birine <xref:System.ServiceModel.ImpersonationOption> ya da sabit listesi değerleri <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> veya <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>aşağıdaki örnekte gösterildiği gibi.  
  
> [!NOTE]
>  Uzak istemci daha yüksek kimlik bilgileri hizmet sahip olduğunda, hizmet kimlik bilgilerini, kullanılan <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği <xref:System.ServiceModel.ImpersonationOption.Allowed>. Diğer bir deyişle, bir düşük ayrıcalıklı kullanıcı kimlik bilgilerini sağlıyorsa, daha yüksek ayrıcalıklı hizmeti hizmetin kimlik bilgileri ile yürütülür ve düşük ayrıcalıklı kullanıcı aksi kullanmanız mümkün olmayacaktır kaynakları kullanabilir.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 Arayan bir Windows hesabının eşlenebilecek kimlik bilgileri ile doğrulanırsa WCF altyapısı çağıranın kimliğine bürünüp. Hizmet için bir Windows hesabı eşlenemez bir kimlik bilgilerini kullanarak kimlik doğrulaması için yapılandırılmışsa, hizmet yöntemi yürütülemiyor.  
  
> [!NOTE]
>  Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)], kimliğe bürünme başarısız olursa SCT oluşturulur, sonuçta bir durum bilgisi olan bir <xref:System.InvalidOperationException>. Daha fazla bilgi için [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Kimliğe bürünme hizmet yöntemi içinde: Kesinlik temelli modeli  
 Bazen çağıran işlev, ancak yalnızca bir bölümü için tüm hizmet yöntemi taklit gerekmez. Bu durumda, arayanın hizmet yöntemi içinde Windows kimliğini edinmek ve kesin kimliğe bürünme gerçekleştirin. Kullanarak bunu <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği <xref:System.ServiceModel.ServiceSecurityContext> örneği döndürülecek <xref:System.Security.Principal.WindowsIdentity> sınıfı ve arama <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemi örneği kullanmadan önce.  
  
> [!NOTE]
>  Visual Basic kullandığınızdan emin olun`Using` deyimi veya C# `using` kimliğe bürünme eylemi otomatik olarak geri bildirimi. Deyim kullanmayın veya Visual Basic veya C# dışındaki bir programlama dili kullanırsanız, kimliğe bürünme düzeyi geri emin olun. Bunun yapılmaması, hizmet reddi ve ayrıcalıkların yükseltilmesi saldırılarını için temel oluşturabilir.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Tüm hizmet yöntemleri için kimliğe bürünme  
 Bazı durumlarda, arayanın bağlamında bir hizmetin tüm yöntemleri gerçekleştirmeniz gerekir. Bu özellik yöntemi başına temelinde açıkça etkinleştirmek yerine kullanmak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Aşağıdaki kodda gösterilen şekilde ayarlayın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> özelliğini `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Davranışlarını koleksiyonlardan alınan <xref:System.ServiceModel.ServiceHost> sınıfı. Ayrıca `Impersonation` özelliği <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanan her bir yöntemi de ayarlanması gerekir ya da çok <xref:System.ServiceModel.ImpersonationOption.Allowed> veya <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Aşağıdaki tabloda tüm olası eşleştirme birleşimlerini WCF davranışı açıklanmaktadır `ImpersonationOption` ve `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Davranış|  
|---------------------------|------------------------------------------------|--------------|  
|Gerekli|yok|WCF çağıranın kimliğine bürünür|  
|İzin Verildi|false|WCF çağıranın kimliğine bürünüp değil|  
|İzin Verildi|true|WCF çağıranın kimliğine bürünür|  
|Noktayla|false|WCF çağıranın kimliğine bürünüp değil|  
|Noktayla|true|İzin verilmiyor. (Bir <xref:System.InvalidOperationException> oluşturulur.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Kimliğe bürünme düzeyi'Windows kimlik bilgileri elde edilen ve önbelleğe alınan belirteç kimliğe bürünme  
 Bazı senaryolarda istemci hizmeti Windows istemci kimlik bilgilerini kullanıldığında gerçekleştirir kimliğe bürünme düzeyini kısmi denetime sahiptir. Senaryolardan biri, istemci bir anonim kimliğe bürünme düzeyini belirtir oluşur. Diğer bir önbelleğe alınan belirteç ile kimliğe bürünme gerçekleştirirken gerçekleşir. Bu ayarı gerçekleştirilir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> özelliği genel olarak erişilebilen sınıfı <xref:System.ServiceModel.ChannelFactory%601> sınıfı.  
  
> [!NOTE]
>  Anonim bir kimliğe bürünme düzeyi belirterek istemci hizmete anonim olarak oturum açmak neden olur. Hizmet, bu nedenle oturum açma, kimliğe bürünme gerçekleştirilip bağımsız olarak anonim, izin vermelidir.  
  
 İstemcinin kimliğe bürünme düzeyi olarak belirtebilirsiniz <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, veya <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Aşağıdaki kodda gösterildiği gibi yalnızca bir belirteç belirtilen düzeyinde oluşturulur.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Aşağıdaki tabloda, hizmet uygulamasından bir önbelleğe alınan belirteç belirlerken alır kimliğe bürünme düzeyini belirtir.  
  
|`AllowedImpersonationLevel` Değer|Hizmet içerir `SeImpersonatePrivilege`|Hizmet ve istemci için temsilci seçme özelliği|Önbelleğe alınan belirteç `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonim|Evet|yok|Kimliğe bürünme|  
|Anonim|Hayır|yok|Tanımlama|  
|Tanımlama|yok|yok|Tanımlama|  
|Kimliğe bürünme|Evet|yok|Kimliğe bürünme|  
|Kimliğe bürünme|Hayır|yok|Tanımlama|  
|Temsilci seçme|Evet|Evet|Temsilci seçme|  
|Temsilci seçme|Evet|Hayır|Kimliğe bürünme|  
|Temsilci seçme|Hayır|yok|Tanımlama|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Kimliğe bürünme düzeyi elde edilen kullanıcı adı kimlik bilgilerini ve önbelleğe alınan belirteç kimliğe bürünme  
 Hizmet kullanıcı adı ve parola geçirerek, bir istemci olarak ayarlamakla eşdeğerdir bu kullanıcı, oturum açmak WCF sağlar `AllowedImpersonationLevel` özelliğini <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. ( `AllowedImpersonationLevel` Kullanılabilir <xref:System.ServiceModel.Security.WindowsClientCredential> ve <xref:System.ServiceModel.Security.HttpDigestClientCredential> sınıfları.) Aşağıdaki tabloda hizmet kullanıcı adı kimlik bilgilerini aldığında düzeyi elde kimliğe bürünme sağlar.  
  
|`AllowedImpersonationLevel`|Hizmet içerir `SeImpersonatePrivilege`|Hizmet ve istemci için temsilci seçme özelliği|Önbelleğe alınan belirteç `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|yok|Evet|Evet|Temsilci seçme|  
|yok|Evet|Hayır|Kimliğe bürünme|  
|yok|Hayır|yok|Tanımlama|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Kimliğe bürünme S4U tabanlı alınan kimliğe bürünme düzeyi  
  
|Hizmet içerir `SeTcbPrivilege`|Hizmet içerir `SeImpersonatePrivilege`|Hizmet ve istemci için temsilci seçme özelliği|Önbelleğe alınan belirteç `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Evet|Evet|yok|Kimliğe bürünme|  
|Evet|Hayır|yok|Tanımlama|  
|Hayır|yok|yok|Tanımlama|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Bir Windows hesabı için bir istemci sertifikası eşlemesi  
 Bir istemci bir sertifika kullanarak bir hizmete kendi kimliğini doğrulamak ve var olan bir Active Directory hesabıyla istemciye hizmet eşlemesi için mümkündür. Aşağıdaki XML, sertifika eşlemek için hizmet yapılandırma işlemi gösterilmektedir.  
  
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
  
 Aşağıdaki kod, hizmet yapılandırma işlemi gösterilmektedir.  
  
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
 Kerberos kimlik doğrulaması için Windows kimliğini kullanarak arka uç hizmetini doğrudan ya da bir arka uç hizmetine temsilci olarak hizmet Kerberos çok oluşturan (SSPI NTLM geri dönüş olmadan) gerçekleştirmeniz gerekir. Bir arka uç hizmetine temsilci olarak oluşturma bir <xref:System.ServiceModel.ChannelFactory%601> ve bir kanal ve ardından istemci kimliğine bürünülürken kanalı iletişim. Bu temsilci formla ön uç hizmeti tarafından gerçekleştirilen kimliğe bürünme düzeyi, arka uç hizmeti ön uç hizmetinden bulunabilir uzaklık bağlıdır. Kimliğe bürünme düzeyi olduğunda <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, ön uç ve arka uç Hizmetleri aynı makinede çalıştırılması gerekir. Kimliğe bürünme düzeyi olduğunda <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, ön uç ve arka uç Hizmetleri, ayrı makinelerde ya da aynı makinede olabilir. Temsilci düzeyi kimliğe bürünmesi etkinleştirilirken, Windows etki alanı ilkesi temsilci izin vermek için yapılandırılmasını gerektirir. Active Directory temsilci seçme desteği için yapılandırma hakkında daha fazla bilgi için bkz. [yetki verilmiş kimlik doğrulamasını etkinleştirme](https://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
>  Bir istemci ön uç hizmeti bir kullanıcı adı ve bir Windows hesabı arka uç hizmetine karşılık gelen parola kullanarak kimlik doğrulamasını gerçekleştirdiğinde ön uç hizmeti arka uç hizmetine istemcinin kullanıcı adını ve parolayı yeniden kullanarak kimlik doğrulaması yapabilir. Bunun nedeni, kullanıcı adı kimlik akışı özellikle güçlü bir tür ve arka uç hizmetine parola kimliğe bürünme işlemi için arka uç hizmetini etkinleştirir, ancak Kerberos kullanılmadığından temsilci oluşturmadığına. Temsilci Active Directory denetimlerinde kullanıcı adı ve parola kimlik doğrulaması için geçerli değildir.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Kimliğe bürünme düzeyi işlevi olarak temsilci özelliği  
  
|Kimliğe bürünme düzeyi|Hizmet çapraz işlem temsilci gerçekleştirebilirsiniz.|Çapraz makine temsilci hizmet gerçekleştirebilirsiniz|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Hayır|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Evet|Hayır|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Evet|Evet|  
  
 Aşağıdaki kod örneği, temsili kullanmak üzere nasıl gösterir.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Kısıtlanmış temsili kullanmak üzere bir uygulama yapılandırma  
 Önce kullanım Kısıtlanmış temsilci seçme, gönderen, alıcı ve etki alanı denetleyicisi, bunu yapmak için yapılandırılmalıdır. Aşağıdaki yordamı Kısıtlanmış temsilci etkinleştirme adımları listeler. Bölümünü Kısıtlanmış temsilci seçme ile temsilci arasındaki farklar hakkında daha fazla bilgi için bkz. [Windows Server 2003 Kerberos uzantıları](https://go.microsoft.com/fwlink/?LinkId=100194) kısıtlanmış tartışma açıklanır.  
  
1. Etki alanı denetleyicisinde Temizle **Hesap duyarlıdır ve devredilemez** istemci uygulamasının altında çalıştığı hesabı için onay kutusu.  
  
2. Etki alanı denetleyicisinde seçin **hesabıdır temsilci seçme için güvenilir** istemci uygulamasının altında çalıştığı hesabı için onay kutusu.  
  
3. Temsilci seçme için güvenilir olması tıklayarak etki alanı denetleyicisinde, orta katman bilgisayarı yapılandırmak **temsilci seçme için bilgisayara güven** seçeneği.  
  
4. Etki alanı denetleyicisinde tıklayarak kısıtlanmış temsili kullanmak için orta katman bilgisayarı yapılandırmak **bu bilgisayara yalnızca belirtilen hizmetlere temsilci seçmek için güven** seçeneği.  
  
 Kısıtlanmış temsili yapılandırma hakkında daha ayrıntılı yönergeler için MSDN'de aşağıdaki konulara bakın:  
  
- [Kerberos temsilci seçme sorunlarını giderme](https://go.microsoft.com/fwlink/?LinkId=36724)  
  
- [Kerberos protokol geçişi ve kısıtlanmış temsil](https://go.microsoft.com/fwlink/?LinkId=36725)  
  
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
- [Nasıl yapılır: Bir hizmette istemci kimliğine bürünme](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
