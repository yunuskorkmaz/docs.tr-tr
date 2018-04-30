---
title: 'Nasıl yapılır: Güvenli Oturum Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: 10
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 0316d1120fe5f5b596374594de66e4f48dae84e8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="f20bc-102">Nasıl yapılır: Güvenli Oturum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f20bc-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="f20bc-103">Dışında [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlama, sistem tarafından sağlanan bağlamalar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenli oturumlar ileti güvenliği etkinleştirildiğinde otomatik olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="f20bc-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="f20bc-104">Varsayılan olarak, güvenli oturumlar geri dönüştürüldüğünde bir Web sunucusu varlığını sürdürmesini değil.</span><span class="sxs-lookup"><span data-stu-id="f20bc-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="f20bc-105">Güvenli bir oturum oluşturulduğunda, istemci ve hizmet güvenli oturumla ilişkili anahtar önbelleğe.</span><span class="sxs-lookup"><span data-stu-id="f20bc-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="f20bc-106">Değiştirilen mesajları gibi yalnızca bir tanımlayıcı önbelleğe alınan anahtarına değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="f20bc-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="f20bc-107">Web sunucusu geri dönüştürüldüğünde ise sağlayacak şekilde Web sunucusu tanımlayıcısı için önbelleğe alınan anahtar alınamıyor önbellek Ayrıca, dönüştürülmeden.</span><span class="sxs-lookup"><span data-stu-id="f20bc-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="f20bc-108">Bu durumda, bir özel durum istemciye geri atılır.</span><span class="sxs-lookup"><span data-stu-id="f20bc-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="f20bc-109">Bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanan güvenli oturumlar dönüştürüldüğü bir Web sunucusu varlığını sürdürmesini.</span><span class="sxs-lookup"><span data-stu-id="f20bc-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="f20bc-110">Durum bilgisi olan SCT güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="f20bc-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="f20bc-111">Sistem tarafından sağlanan bağlamalar birini kullanarak bir hizmeti güvenli oturumlar kullandığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="f20bc-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="f20bc-112">İleti güvenliği destekleyen sistem tarafından sağlanan bir bağlamayı kullanmak amacıyla hizmeti yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f20bc-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="f20bc-113">Dışında [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) ileti güvenliği kullanmak için sistem tarafından sağlanan bağlamaları yapılandırıldığında bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenli oturumlar otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="f20bc-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically uses secure sessions.</span></span> <span data-ttu-id="f20bc-114">İleti güvenliği ve ileti güvenliği varsayılan güvenlik mekanizması olup destek sistem tarafından sağlanan bağlamaları aşağıdaki tabloda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f20bc-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="f20bc-115">Sistem tarafından sağlanan bağlama</span><span class="sxs-lookup"><span data-stu-id="f20bc-115">System-provided binding</span></span>|<span data-ttu-id="f20bc-116">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="f20bc-116">Configuration element</span></span>|<span data-ttu-id="f20bc-117">Varsayılan ileti güvenliği</span><span class="sxs-lookup"><span data-stu-id="f20bc-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="f20bc-118">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f20bc-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="f20bc-119">Hayır</span><span class="sxs-lookup"><span data-stu-id="f20bc-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="f20bc-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f20bc-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="f20bc-121">Evet</span><span class="sxs-lookup"><span data-stu-id="f20bc-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="f20bc-122">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f20bc-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="f20bc-123">Evet</span><span class="sxs-lookup"><span data-stu-id="f20bc-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="f20bc-124">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f20bc-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="f20bc-125">Evet</span><span class="sxs-lookup"><span data-stu-id="f20bc-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="f20bc-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f20bc-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="f20bc-127">Hayır</span><span class="sxs-lookup"><span data-stu-id="f20bc-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="f20bc-128">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="f20bc-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="f20bc-129">Hayır</span><span class="sxs-lookup"><span data-stu-id="f20bc-129">No</span></span>|  
  
     <span data-ttu-id="f20bc-130">Adlı bir bağlama belirtmek için aşağıdaki kod örneğinde yapılandırmasını kullanan `wsHttpBinding_Calculator` kullanan [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ileti güvenlik ve güvenli oturumlar.</span><span class="sxs-lookup"><span data-stu-id="f20bc-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="f20bc-131">Aşağıdaki kod örneğinde belirtir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ileti güvenlik ve güvenli oturumlar güvenliğini sağlamak için kullanılan `secureCalculator` hizmet.</span><span class="sxs-lookup"><span data-stu-id="f20bc-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f20bc-132">Güvenli oturumlar açılabilir için [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlayarak `establishSecurityContext` özniteliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="f20bc-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="f20bc-133">Özel bağlama oluşturarak diğer sistem tarafından sağlanan bağlamaları için yalnızca güvenli oturumlar kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="f20bc-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="f20bc-134">Özel bağlama kullanarak bir hizmeti güvenli oturumlar kullandığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="f20bc-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="f20bc-135">SOAP iletilerine güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f20bc-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="f20bc-136">Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: System-Provided bir bağlamayı özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="f20bc-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="f20bc-137">Aşağıdaki kod örneği, bir özel bağlama güvenli oturum kullanarak bu iletileri belirtmek için yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="f20bc-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="f20bc-138">Aşağıdaki kod örneği kullanan özel bağlama oluşturur <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturum bootstrap için kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="f20bc-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f20bc-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f20bc-139">See Also</span></span>  
 [<span data-ttu-id="f20bc-140">WCF Bağlamalarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f20bc-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
