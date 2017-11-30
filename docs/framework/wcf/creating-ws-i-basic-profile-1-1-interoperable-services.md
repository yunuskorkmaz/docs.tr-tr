---
title: "WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma"
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
helpviewer_keywords: configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a725f1cbe50bcad5247e727efcffbad62985a01a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="8e1d6-102">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e1d6-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="8e1d6-103">Yapılandırmak için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] birlikte çalışabilir olmasını Hizmeti uç noktası [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmeti istemcileri:</span><span class="sxs-lookup"><span data-stu-id="8e1d6-103">To configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="8e1d6-104">Kullanım <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türü olarak hizmet uç noktası için bağlama türü.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="8e1d6-105">Geri çağırma ve oturum sözleşme özellikleri veya işlem davranışları Hizmeti uç noktanızı kullanmayın</span><span class="sxs-lookup"><span data-stu-id="8e1d6-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="8e1d6-106">İsteğe bağlı olarak, HTTPS ve bağlama üzerinde aktarım düzeyinde istemci kimlik doğrulaması için destek de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="8e1d6-107">Aşağıdaki özellikleri <xref:System.ServiceModel.BasicHttpBinding> sınıfı WS ötesinde işlevselliği gerektiren-ı temel Profil 1.1:</span><span class="sxs-lookup"><span data-stu-id="8e1d6-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="8e1d6-108">İleti iletim en iyi duruma getirme mekanizmasını (MTOM) ileti kodlama denetlenen <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8e1d6-109">Bu özellik olan kendi varsayılan değerinde bırakın <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> MTOM kullanmayacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="8e1d6-110">İleti tarafından denetlenen güvenlik <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> değeri, WS-güvenlik desteği WS ile uyumlu sağlar-ı temel güvenlik profili 1.0.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="8e1d6-111">Bu özellik olan kendi varsayılan değerinde bırakın <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> WS-güvenlik kullanmayacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="8e1d6-112">İçin meta verileri oluşturmak için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti için kullanılabilir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Web hizmeti istemcisi oluşturma araçlarını kullanma: [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Hizmetleri bulma Aracı () Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979)ve `Add Web Reference` özelliğini [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; meta veri yayımlama etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-112">To make the metadata for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979), and the `Add Web Reference` feature in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; you must enable metadata publication.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8e1d6-113">[Meta veri uç noktalarını yayımlama](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="8e1d6-113"> [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e1d6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e1d6-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8e1d6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e1d6-115">Description</span></span>  
 <span data-ttu-id="8e1d6-116">Aşağıdaki kod örneği nasıl ekleneceği gösterilmektedir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ile uyumlu uç nokta [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmeti istemcileri kodda ve alternatif olarak, bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-116">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8e1d6-117">Kod</span><span class="sxs-lookup"><span data-stu-id="8e1d6-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8e1d6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e1d6-118">See Also</span></span>  
 [<span data-ttu-id="8e1d6-119">ASP.NET Web Hizmetleri ile birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="8e1d6-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
