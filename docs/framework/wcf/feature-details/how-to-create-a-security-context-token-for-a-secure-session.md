---
title: 'Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ef2f02bb5ad6e7458ae11e7880fe403f3a6e9916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493418"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="5ad2b-102">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ad2b-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="5ad2b-103">Güvenli bir oturumda bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanarak oturum dönüştürülüyor hizmet dayanabilir.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="5ad2b-104">Örneğin, durum bilgisiz SCT güvenli bir oturumda kullanılır ve Internet Information Services (IIS) sıfırlanır sonra hizmetiyle ilişkili oturum veriler kaybolur.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="5ad2b-105">Bu oturum verilerini bir SCT belirteç önbelleği içerir.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="5ad2b-106">SCT ile ilişkili anahtar alınamadığından bu nedenle, bir istemci hizmeti durum bilgisiz SCT gönderir başlatıldığında bir hata, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="5ad2b-107">Ancak, bir durum bilgisi olan SCT kullanılıyorsa, SCT ile ilişkili anahtar SCT içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="5ad2b-108">Anahtar SCT içinde yer alan ve bu nedenle iletinin içinde yer alan olduğundan, güvenli oturum dönüştürülüyor hizmeti tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="5ad2b-109">Varsayılan olarak, Windows Communication Foundation (WCF) güvenli bir oturumda durum bilgisiz SCTs kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="5ad2b-110">Bu konu, güvenli bir oturumda durum bilgisi olan SCTs kullanmayı ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ad2b-111">Durum bilgisi olan SCTs türeyen bir sözleşme içerir güvenli bir oturum kullanılamaz <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ad2b-112">Durum bilgisi olan SCTs güvenli bir oturumda kullanan uygulamalar için iş parçacığı kimliği hizmeti için bir ilişkili kullanıcı profiline sahip bir kullanıcı hesabı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="5ad2b-113">Hizmet bir kullanıcı profili gibi sahip olmayan bir hesap altında çalıştırıldığında `Local Service`, bir özel durum oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ad2b-114">Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan SCT olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="5ad2b-115">Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="5ad2b-116">Daha fazla bilgi için bkz: [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="5ad2b-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="5ad2b-117">Durum bilgisi olan SCTs güvenli bir oturumda kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5ad2b-117">To use stateful SCTs in a secure session</span></span>  
  
-   <span data-ttu-id="5ad2b-118">SOAP iletilerine durum bilgisi olan SCT kullanan güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1.  <span data-ttu-id="5ad2b-119">Özel bağlama ekleyerek tanımlarsınız bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) dosya hizmeti için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  <span data-ttu-id="5ad2b-120">Ekleme bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) alt öğeye [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="5ad2b-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="5ad2b-121">Bir bağlama ad ayarlayarak belirtin `name` yapılandırma dosyasında benzersiz bir ad özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  <span data-ttu-id="5ad2b-122">Bu hizmet gelen ve giden ekleyerek gönderilen iletiler için kimlik doğrulaması modunu belirtin bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) alt öğeye [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="5ad2b-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="5ad2b-123">Güvenli bir oturum ayarlayarak kullanıldığını belirtmek `authenticationMode` özniteliğini `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="5ad2b-124">Durum bilgisi olan SCTs ayarlayarak kullanıldığını belirtin `requireSecurityContextCancellation` özniteliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  <span data-ttu-id="5ad2b-125">Güvenli oturum ekleyerek belirlenirken istemci kimlik doğrulamasının nasıl belirtin bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğeye [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="5ad2b-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="5ad2b-126">İstemci ayarlayarak kimlik doğrulamasının nasıl belirtin `authenticationMode` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  <span data-ttu-id="5ad2b-127">Bir kodlama öğesi ekleyerek ileti kodlama belirtin [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="5ad2b-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  <span data-ttu-id="5ad2b-128">Bir taşıma öğesi ekleyerek taşıma belirtin [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="5ad2b-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="5ad2b-129">Aşağıdaki kod örneğinde yapılandırma iletileri güvenli bir oturumda durum bilgisi olan SCTs ile kullanabileceğiniz özel bağlama belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5ad2b-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ad2b-130">Example</span></span>  
 <span data-ttu-id="5ad2b-131">Aşağıdaki kod örneği kullanan özel bağlama oluşturur <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturum bootstrap için kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="5ad2b-132">Windows kimlik doğrulaması, bir durum bilgisi olan SCT ile birlikte kullanıldığında, WCF değil doldurmak <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> gerçek çağıran özelliğiyle kimlik kullanıcının ancak bunun yerine özelliği anonim olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="5ad2b-133">WCF güvenlik gelen SCT gelen her istek için hizmet güvenlik bağlamı içeriğini yeniden oluşturmanız gerekir çünkü sunucunun bellek güvenlik oturumu izlemek değil.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="5ad2b-134">Seri hale getirmek mümkün değildir çünkü <xref:System.Security.Principal.WindowsIdentity> SCT örneğine <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> anonim bir kimlik özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="5ad2b-135">Aşağıdaki yapılandırma bu davranışı sergiler.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ad2b-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ad2b-136">See Also</span></span>  
 [<span data-ttu-id="5ad2b-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5ad2b-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
