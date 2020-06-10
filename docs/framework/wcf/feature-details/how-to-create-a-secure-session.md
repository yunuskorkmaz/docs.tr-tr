---
title: 'Nasıl yapılır: Güvenli Oturum Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 80973a31050cf1ede03d4a3919066c62625ae590
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593418"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="6100e-102">Nasıl yapılır: Güvenli Oturum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6100e-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="6100e-103">[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)Bağlama dışında, Windows Communication Foundation (WCF) içindeki sistem tarafından sağlanan bağlamalar, ileti güvenliği etkinleştirildiğinde otomatik olarak güvenli oturumları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6100e-103">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="6100e-104">Varsayılan olarak, güvenli oturumlar geri dönüştürülecek bir Web sunucusunu sürdürmez.</span><span class="sxs-lookup"><span data-stu-id="6100e-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="6100e-105">Güvenli bir oturum oluşturulduğunda, istemci ve hizmet güvenli oturumla ilişkili anahtarı önbelleğe alın.</span><span class="sxs-lookup"><span data-stu-id="6100e-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="6100e-106">İletiler alışverişi sırasında yalnızca önbelleğe alınmış anahtara yönelik bir tanımlayıcı alışverişi yapılır.</span><span class="sxs-lookup"><span data-stu-id="6100e-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="6100e-107">Web sunucusu geri dönüştürüldüğünde, önbellek de, Web sunucusu tanımlayıcı için önbelleğe alınmış anahtarı alamadığından geri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="6100e-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="6100e-108">Bu durumda, istemciye geri bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6100e-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="6100e-109">Durum bilgisi olan güvenlik bağlamı belirteci (SCT) kullanan güvenli oturumlar, bir Web sunucusunun geri dönüştürülmekte olmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6100e-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="6100e-110">Güvenli bir oturumda durum bilgisi olan bir SCT kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="6100e-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="6100e-111">Bir hizmetin, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenli oturumlar kullandığını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="6100e-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="6100e-112">Bir hizmeti, ileti güvenliğini destekleyen sistem tarafından sağlanmış bir bağlama kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="6100e-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="6100e-113">[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)Bağlama dışında, sistem tarafından belirtilen bağlamalar ileti güvenliği kullanmak üzere yapılandırıldığında, WCF otomatik olarak güvenli oturumları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6100e-113">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="6100e-114">Aşağıdaki tabloda, ileti güvenliğini destekleyen sistem tarafından sağlanmış bağlamalar ve ileti güvenliği 'nin varsayılan güvenlik mekanizması olup olmadığı listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6100e-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="6100e-115">Sistem tarafından sağlanmış bağlama</span><span class="sxs-lookup"><span data-stu-id="6100e-115">System-provided binding</span></span>|<span data-ttu-id="6100e-116">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="6100e-116">Configuration element</span></span>|<span data-ttu-id="6100e-117">Varsayılan olarak ileti güvenliği</span><span class="sxs-lookup"><span data-stu-id="6100e-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="6100e-118">Hayır</span><span class="sxs-lookup"><span data-stu-id="6100e-118">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="6100e-119">Yes</span><span class="sxs-lookup"><span data-stu-id="6100e-119">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="6100e-120">Yes</span><span class="sxs-lookup"><span data-stu-id="6100e-120">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="6100e-121">Yes</span><span class="sxs-lookup"><span data-stu-id="6100e-121">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="6100e-122">Hayır</span><span class="sxs-lookup"><span data-stu-id="6100e-122">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="6100e-123">Hayır</span><span class="sxs-lookup"><span data-stu-id="6100e-123">No</span></span>|  
  
     <span data-ttu-id="6100e-124">Aşağıdaki kod örneği `wsHttpBinding_Calculator` [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ,, ileti güvenliği ve güvenli oturumları kullanan adlı bir bağlama belirtmek için yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6100e-124">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="6100e-125">Aşağıdaki kod örneği [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , hizmeti güvenli hale getirmek için ileti güvenliği ve güvenli oturumların kullanıldığını belirtir `secureCalculator` .</span><span class="sxs-lookup"><span data-stu-id="6100e-125">The following code example specifies that the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="6100e-126">İçin güvenli oturumlar, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) `establishSecurityContext` özniteliği olarak ayarlanarak kapatılabilir `false` .</span><span class="sxs-lookup"><span data-stu-id="6100e-126">Secure sessions can be turned off for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="6100e-127">Sistem tarafından sağlanmış diğer bağlamalar için güvenli oturumlar yalnızca özel bir bağlama oluşturularak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="6100e-127">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="6100e-128">Bir hizmetin özel bir bağlama kullanarak güvenli oturumlar kullandığını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="6100e-128">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="6100e-129">SOAP iletilerinin güvenli bir oturum tarafından korunduğunu belirten özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6100e-129">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="6100e-130">Özel bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: sistem tarafından sağlanmış bağlamayı özelleştirme](../extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="6100e-130">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="6100e-131">Aşağıdaki kod örneği, güvenli bir oturum kullanan iletilerin özel bir bağlamasını belirtmek için yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6100e-131">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="6100e-132">Aşağıdaki kod örneği, <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> güvenli bir oturumu önyüklemek için kimlik doğrulama modunu kullanan özel bir bağlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6100e-132">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6100e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6100e-133">See also</span></span>

- [<span data-ttu-id="6100e-134">WCF Bağlamaları Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6100e-134">WCF Bindings Overview</span></span>](../bindings-overview.md)
