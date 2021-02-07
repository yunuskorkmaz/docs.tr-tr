---
description: 'Daha fazla bilgi edinin: nasıl yapılır: güvenli bir oturum için güvenlik bağlamı belirteci oluşturma'
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 29e8b694779f2a960f449469438c3aed0d0a815d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734678"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="6a2eb-103">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6a2eb-103">How to: Create a Security Context Token for a Secure Session</span></span>

<span data-ttu-id="6a2eb-104">Güvenli bir oturumda durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak, oturum hizmetin geri dönüştürülmemesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-104">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="6a2eb-105">Örneğin, bir durum bilgisiz SCT güvenli bir oturumda kullanıldığında ve Internet Information Services (IIS) sıfırlandığında, hizmetle ilişkili oturum verileri kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-105">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="6a2eb-106">Bu oturum verileri bir SCT belirteç önbelleği içerir.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-106">This session data includes an SCT token cache.</span></span> <span data-ttu-id="6a2eb-107">Bu nedenle, bir istemci hizmeti durum bilgisiz SCT ' yi bir sonraki gönderişinde, SCT ile ilişkili anahtar alınamadığından bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-107">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="6a2eb-108">Ancak, durum bilgisi olan bir SCT kullanılırsa, SCT ile ilişkili anahtar, SCT içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-108">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="6a2eb-109">Anahtar SCT içinde bulunduğundan ve bu nedenle ileti içinde yer aldığı için güvenli oturum, geri dönüştürülecek hizmetten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-109">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="6a2eb-110">Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda durum bilgisiz SCTs 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-110">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="6a2eb-111">Bu konuda güvenli bir oturumda durum bilgisi olan SCN 'leri kullanma hakkında ayrıntılı bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-111">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a2eb-112">Durum bilgisi olan SCN 'ler, öğesinden türetilen bir sözleşmeyi içeren güvenli bir oturumda kullanılamaz <xref:System.ServiceModel.Channels.IDuplexChannel> .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-112">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a2eb-113">Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanan uygulamalar için, hizmetin iş parçacığı kimliği, ilişkili kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-113">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="6a2eb-114">Hizmet, gibi bir kullanıcı profiline sahip olmayan bir hesap altında çalıştırıldığında `Local Service` bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-114">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a2eb-115">Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olmayan bir SCT olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-115">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="6a2eb-116">Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir oluşturulur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-116">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="6a2eb-117">Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="6a2eb-117">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="6a2eb-118">Güvenli bir oturumda durum bilgisi olan SCN 'leri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6a2eb-118">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="6a2eb-119">SOAP iletilerinin durum bilgisi olan bir SCT kullanan güvenli bir oturumla korunduğunu belirten özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-119">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="6a2eb-120">Hizmet için yapılandırma dosyasına bir ekleyerek özel bir bağlama tanımlayın [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-120">Define a custom binding, by adding a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. <span data-ttu-id="6a2eb-121">Öğesine bir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) alt öğesi ekleyin [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-121">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="6a2eb-122">`name`Özniteliği yapılandırma dosyası içindeki benzersiz bir ada ayarlayarak bir bağlama adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-122">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. <span data-ttu-id="6a2eb-123">Öğesine bir alt öğe ekleyerek bu hizmetten gönderilen ve giden iletiler için kimlik doğrulama modunu belirtin [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-123">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="6a2eb-124">Özniteliğini olarak ayarlayarak güvenli bir oturumun kullanıldığını belirtin `authenticationMode` `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-124">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="6a2eb-125">Özniteliği olarak ayarlanarak durum bilgisi olan SCN 'leri belirtin `requireSecurityContextCancellation` `false` .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-125">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. <span data-ttu-id="6a2eb-126">' Ye bir alt öğesi eklenerek, güvenli oturum oluşturulduğunda istemcinin nasıl doğrulandığını belirtin [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-126">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="6a2eb-127">Özniteliğini ayarlayarak istemcinin kimliğinin nasıl doğrulandığını belirtin `authenticationMode` .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-127">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="6a2eb-128">Bir kodlama öğesi ekleyerek ileti kodlamasını belirtin (örneğin,) [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-128">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="6a2eb-129">Taşıma öğesi ekleyerek taşımayı belirtin [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2eb-129">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="6a2eb-130">Aşağıdaki kod örneği, iletilerin, güvenli bir oturumda durum bilgisi olan SCN 'ler ile kullanabileceği özel bir bağlama belirtmek için yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-130">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6a2eb-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a2eb-131">Example</span></span>  

 <span data-ttu-id="6a2eb-132">Aşağıdaki kod örneği, <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturumu önyüklemek için kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-132">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="6a2eb-133">Windows kimlik doğrulaması durum bilgisi olan bir SCT ile birlikte kullanıldığında, WCF, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği gerçek arayanın kimliğiyle doldurmaz, bunun yerine özelliği anonim olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-133">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="6a2eb-134">WCF güvenliği, gelen SCT 'nin her isteği için hizmet güvenlik bağlamının içeriğini yeniden oluşturması gerektiğinden, sunucu bellekteki güvenlik oturumunu izlemez.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-134">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="6a2eb-135">Örneği SCT 'e seri hale getirmek imkansız olduğundan <xref:System.Security.Principal.WindowsIdentity> , <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> Özelliği anonim bir kimlik döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-135">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="6a2eb-136">Aşağıdaki yapılandırma bu davranışı sergiler.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-136">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a2eb-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a2eb-137">See also</span></span>

- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
