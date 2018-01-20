---
title: "Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea71737e1e214aa1a035739901bf79f8ef4a9c7a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="7367a-102">Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7367a-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7367a-103">istemcileri Microsoft .NET (WSE) ne zaman Hizmetleri için Web Hizmetleri geliştirmeleri 3.0 hat düzeyinde uyumlu olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri WS adresleme belirtimi Ağustos 2004 sürümünü kullanacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7367a-103"> clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="7367a-104">WSE 3.0 Web hizmeti ile birlikte çalışmak için WCF istemcisini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="7367a-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="7367a-105">Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 Web hizmeti istemci.</span><span class="sxs-lookup"><span data-stu-id="7367a-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="7367a-106">WSE Web hizmeti için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci sınıfı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7367a-106">For a WSE Web service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class is created.</span></span>  
  
     <span data-ttu-id="7367a-107">Oluşturma hakkında daha fazla ayrıntı için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="7367a-107">For details about creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="7367a-108">WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7367a-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="7367a-109">Aşağıdaki sınıf parçası olan [WSE ile birlikte](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) örnek.</span><span class="sxs-lookup"><span data-stu-id="7367a-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="7367a-110">Türeyen bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7367a-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="7367a-111">Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` , türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7367a-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="7367a-112">Özellikler WSE anahtar teslimi onaylama, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup olmadığı ve ileti koruma ayarlarını belirtin sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7367a-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="7367a-113">Aşağıdaki kod örneğinde tanımlar `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` WSE anahtar teslimi onaylama, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarlarını belirten özellikleri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="7367a-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="7367a-114">Geçersiz kılma <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi bağlama özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7367a-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="7367a-115">Aşağıdaki kod örneğinde taşıma, ileti kodlama ve ileti koruma ayarları değerleri alma belirtir `SecurityAssertion` ve `MessageProtectionOrder` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7367a-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="7367a-116">İstemci uygulaması kodu bağlama özelliklerini ayarlamak için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7367a-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="7367a-117">Aşağıdaki kod örneğinde belirleyen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci kullanmalıdır ileti koruma ve kimlik doğrulama WSE 3.0 tarafından tanımlandığı şekilde `AnonymousForCertificate` anahtar teslimi güvenlik onaylama işlemi.</span><span class="sxs-lookup"><span data-stu-id="7367a-117">The following code example specifies that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="7367a-118">Ayrıca, güvenli oturumlar ve türetilmiş anahtar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7367a-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="7367a-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="7367a-119">Example</span></span>  
 <span data-ttu-id="7367a-120">Aşağıdaki kod örneğinde WSE 3.0 anahtar teslimi güvenlik onaylama işlemi özelliklerine karşılık özellikleri kullanıma sunan özel bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7367a-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="7367a-121">Adlı özel bağlama `WseHttpBinding`, ardından bağlama özelliklerini belirtmek için kullanılan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci.</span><span class="sxs-lookup"><span data-stu-id="7367a-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="7367a-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7367a-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="7367a-123">WSE ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="7367a-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
