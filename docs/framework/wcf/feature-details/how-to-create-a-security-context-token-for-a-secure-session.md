---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 4e91580035d4de23ae90cd0d59a08f321ae70a1c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464142"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="ab1d6-102">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab1d6-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="ab1d6-103">Güvenli bir oturumda durumsal bir güvenlik bağlamı belirteci (SCT) kullanarak, oturum geri dönüştürülen hizmete dayanabilir.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="ab1d6-104">Örneğin, güvenli bir oturumda durum bilgisi olmayan bir SCT kullanıldığında ve Internet Information Services (IIS) sıfırlandığında, hizmetle ilişkili oturum verileri kaybolur.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="ab1d6-105">Bu oturum verileri bir SCT belirteç önbelleği içerir.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="ab1d6-106">Bu nedenle, bir istemci hizmeti bir sonraki kez durumsuz bir SCT gönderdiğinde, SCT ile ilişkili anahtar alınamadığından bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="ab1d6-107">Ancak, durum lu bir ÖST kullanılırsa, ÖSK ile ilişkili anahtar ÖSK içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="ab1d6-108">Anahtar ÖST içinde ve böylece ileti içinde bulunduğundan, güvenli oturum geri dönüştürülen hizmetten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="ab1d6-109">Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda devletsiz SCT'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="ab1d6-110">Bu konu, güvenli bir oturumda durum lu SCT'lerin nasıl kullanılacağını ayrıntılarıyla anlatır.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab1d6-111">Stateful SCT'ler, <xref:System.ServiceModel.Channels.IDuplexChannel>'den türeyen bir sözleşme içeren güvenli bir oturumda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab1d6-112">Güvenli bir oturumda durum daki SCT'leri kullanan uygulamalar için, hizmetin iş parçacığı kimliği ilişkili bir kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="ab1d6-113">Hizmet, kullanıcı profili olmayan bir hesap altında `Local Service`çalıştırıldığında, örneğin , bir özel durum atılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab1d6-114">Windows XP'de kimliğe bürünme gerektiğinde, devlete uygun bir SCT olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="ab1d6-115">Stateful SCTs kimliğe bürünme <xref:System.InvalidOperationException> ile kullanıldığında, bir atılır.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="ab1d6-116">Daha fazla bilgi için [desteklenmeyen senaryolar'a](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="ab1d6-117">Güvenli bir oturumda durum lu SCT'leri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="ab1d6-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="ab1d6-118">SOAP iletilerinin özel bir ÖTV kullanan güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="ab1d6-119">Hizmetin yapılandırma dosyasına [ \<özel](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlayıcı>ekleyerek özel bir bağlama tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. <span data-ttu-id="ab1d6-120">Bağlayıcı [ \<>](../../configure-apps/file-schema/wcf/bindings.md) alt öğesi [özelBağlayıcı>. \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="ab1d6-120">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ab1d6-121">Yapılandırma dosyasındaki `name` benzersiz bir ada özniteliği ayarlayarak bağlayıcı bir ad belirtin.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. <span data-ttu-id="ab1d6-122">ÖzelBağlayıcı>'ne bir [ \<güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) alt öğesi ekleyerek bu hizmete ve bu hizmetten gönderilen iletilerin kimlik doğrulama modunu belirtin. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="ab1d6-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ab1d6-123">Özniteliği ' ne `authenticationMode` `SecureConversation`ayarlayarak güvenli bir oturumun kullanıldığını belirtin</span><span class="sxs-lookup"><span data-stu-id="ab1d6-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="ab1d6-124">Stateful SCT'lerin `requireSecurityContextCancellation` özniteliği ni atlayarak `false`kullanıldığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. <span data-ttu-id="ab1d6-125">Güvenli oturum güvenlik>güvenli bir [ \<ConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğe ekleyerek kurulurken istemcinin nasıl doğrulanmış olduğunu belirtin. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="ab1d6-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="ab1d6-126">Öznitelik ayarlayarak istemcinin nasıl `authenticationMode` doğrulanmış olduğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="ab1d6-127">[ \<TextMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)gibi bir kodlama öğesi ekleyerek ileti kodlamasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="ab1d6-128">[ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)gibi bir aktarım öğesi ekleyerek aktarım'ı belirtin.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="ab1d6-129">Aşağıdaki kod örneği, iletilerin güvenli bir oturumda durum daki SCT'lerle kullanabileceği özel bir bağlama belirtmek için yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ab1d6-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab1d6-130">Example</span></span>  
 <span data-ttu-id="ab1d6-131">Aşağıdaki kod örneği, güvenli bir oturumu <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> önyükleme için kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="ab1d6-132">Windows kimlik doğrulaması durum salkıcısı ile birlikte kullanıldığında, WCF özelliği gerçek arayanın <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> kimliğiyle doldurmaz, bunun yerine özelliği anonim olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="ab1d6-133">WCF security'nin gelen SCT'den gelen her istek için hizmet güvenliği bağlamının içeriğini yeniden oluşturması gerektiğinden, sunucu bellekteki güvenlik oturumunu izlemez.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="ab1d6-134"><xref:System.Security.Principal.WindowsIdentity> Örneği SCT'ye seri hale getirmek mümkün <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> olmadığından, özellik anonim bir kimlik döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="ab1d6-135">Aşağıdaki yapılandırma bu davranışı sergiler.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab1d6-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab1d6-136">See also</span></span>

- [<span data-ttu-id="ab1d6-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ab1d6-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
