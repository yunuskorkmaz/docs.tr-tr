---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: e6c41ed32d63932bc1fac72bc6e727eb82806617
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966079"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="f66cf-102">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f66cf-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="f66cf-103">Güvenli bir oturumda durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak, oturum hizmetin geri dönüştürülmemesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f66cf-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="f66cf-104">Örneğin, bir durum bilgisiz SCT güvenli bir oturumda kullanıldığında ve Internet Information Services (IIS) sıfırlandığında, hizmetle ilişkili oturum verileri kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="f66cf-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="f66cf-105">Bu oturum verileri bir SCT belirteç önbelleği içerir.</span><span class="sxs-lookup"><span data-stu-id="f66cf-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="f66cf-106">Bu nedenle, bir istemci hizmeti durum bilgisiz SCT ' yi bir sonraki gönderişinde, SCT ile ilişkili anahtar alınamadığından bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f66cf-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="f66cf-107">Ancak, durum bilgisi olan bir SCT kullanılırsa, SCT ile ilişkili anahtar, SCT içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="f66cf-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="f66cf-108">Anahtar SCT içinde bulunduğundan ve bu nedenle ileti içinde yer aldığı için güvenli oturum, geri dönüştürülecek hizmetten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="f66cf-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="f66cf-109">Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda durum bilgisiz SCTs 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f66cf-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="f66cf-110">Bu konuda güvenli bir oturumda durum bilgisi olan SCN 'leri kullanma hakkında ayrıntılı bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f66cf-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f66cf-111">Durum bilgisi olan SCN 'ler, öğesinden <xref:System.ServiceModel.Channels.IDuplexChannel>türetilen bir sözleşmeyi içeren güvenli bir oturumda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f66cf-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f66cf-112">Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanan uygulamalar için, hizmetin iş parçacığı kimliği, ilişkili kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f66cf-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="f66cf-113">Hizmet, gibi bir kullanıcı profiline `Local Service`sahip olmayan bir hesap altında çalıştırıldığında bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f66cf-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f66cf-114">Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olmayan bir SCT olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="f66cf-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="f66cf-115">Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f66cf-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="f66cf-116">Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="f66cf-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="f66cf-117">Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f66cf-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="f66cf-118">SOAP iletilerinin durum bilgisi olan bir SCT kullanan güvenli bir oturumla korunduğunu belirten özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f66cf-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="f66cf-119">Hizmetin yapılandırma dosyasına bir [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyerek özel bir bağlama tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f66cf-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. <span data-ttu-id="f66cf-120">CustomBinding > bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) [alt öğesi ekleyin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f66cf-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="f66cf-121">`name` Özniteliği yapılandırma dosyası içindeki benzersiz bir ada ayarlayarak bir bağlama adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="f66cf-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. <span data-ttu-id="f66cf-122">CustomBinding > bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [alt öğesi ekleyerek bu hizmetten gelen ve giden iletiler için kimlik doğrulama modunu belirtin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f66cf-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="f66cf-123">`authenticationMode` Özniteliğini olarak`SecureConversation`ayarlayarak güvenli bir oturumun kullanıldığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f66cf-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="f66cf-124">`requireSecurityContextCancellation` Özniteliği olarak`false`ayarlanarak durum bilgisi olan SCN 'leri belirtin.</span><span class="sxs-lookup"><span data-stu-id="f66cf-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. <span data-ttu-id="f66cf-125">Güvenlik > bir [ \<securesestionbootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) [alt öğesi eklenerek, istemcinin nasıl doğrulandığını belirtin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f66cf-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="f66cf-126">`authenticationMode` Özniteliğini ayarlayarak istemcinin kimliğinin nasıl doğrulandığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f66cf-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="f66cf-127">TextMessageEncoding > gibi bir kodlama öğesi [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)ekleyerek ileti kodlamasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f66cf-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="f66cf-128">[ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)gibi bir taşıma öğesi ekleyerek taşımayı belirtin.</span><span class="sxs-lookup"><span data-stu-id="f66cf-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="f66cf-129">Aşağıdaki kod örneği, iletilerin, güvenli bir oturumda durum bilgisi olan SCN 'ler ile kullanabileceği özel bir bağlama belirtmek için yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f66cf-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="f66cf-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="f66cf-130">Example</span></span>  
 <span data-ttu-id="f66cf-131">Aşağıdaki kod örneği, güvenli bir oturumu önyüklemek için <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f66cf-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="f66cf-132">Windows kimlik doğrulaması durum bilgisi olan bir SCT ile birlikte kullanıldığında, WCF, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği gerçek arayanın kimliğiyle doldurmaz, bunun yerine özelliği anonim olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f66cf-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="f66cf-133">WCF güvenliği, gelen SCT 'nin her isteği için hizmet güvenlik bağlamının içeriğini yeniden oluşturması gerektiğinden, sunucu bellekteki güvenlik oturumunu izlemez.</span><span class="sxs-lookup"><span data-stu-id="f66cf-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="f66cf-134"><xref:System.Security.Principal.WindowsIdentity> Örneği SCT 'e seri hale getirmek imkansız olduğundan <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> , özelliği anonim bir kimlik döndürür.</span><span class="sxs-lookup"><span data-stu-id="f66cf-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="f66cf-135">Aşağıdaki yapılandırma bu davranışı sergiler.</span><span class="sxs-lookup"><span data-stu-id="f66cf-135">The following configuration exhibits this behavior.</span></span>  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f66cf-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f66cf-136">See also</span></span>

- [<span data-ttu-id="f66cf-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f66cf-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
