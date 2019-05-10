---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 568b960bf49b2a9d79a3357c0a69b1daa767af6c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652063"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="cfb33-102">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cfb33-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="cfb33-103">Bir WCF Hizmeti uç noktası ile birlikte çalışabilir olacak şekilde yapılandırmak için [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmeti istemcileri:</span><span class="sxs-lookup"><span data-stu-id="cfb33-103">To configure a WCF service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
- <span data-ttu-id="cfb33-104">Kullanım <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türü, hizmet uç noktası için bağlama türü olarak.</span><span class="sxs-lookup"><span data-stu-id="cfb33-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="cfb33-105">Geri çağırma ve oturumu sözleşme özellikleri veya hareket davranışları, hizmet uç noktasında kullanmayın</span><span class="sxs-lookup"><span data-stu-id="cfb33-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="cfb33-106">İsteğe bağlı olarak, HTTPS ve bağlamadaki aktarım düzeyinde istemci kimlik doğrulaması için destek de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb33-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="cfb33-107">Aşağıdaki özellikleri <xref:System.ServiceModel.BasicHttpBinding> sınıfı WS ötesine işlevselliği gerektiren-ı Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="cfb33-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="cfb33-108">İleti, ileti aktarım en iyi duruma getirme mekanizması (MTOM) kodlama denetlenmektedir <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cfb33-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="cfb33-109">Bu özellik, kendi varsayılan değerde bırakın <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> MTOM kullanmayacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="cfb33-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="cfb33-110">İleti tarafından denetlenen güvenlik <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> değeri, WS ile uyumlu olan WS-güvenlik desteği sağlar-ı temel güvenlik profili 1.0.</span><span class="sxs-lookup"><span data-stu-id="cfb33-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="cfb33-111">Bu özellik, kendi varsayılan değerde bırakın <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> WS-Security kullanmayı.</span><span class="sxs-lookup"><span data-stu-id="cfb33-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="cfb33-112">Bir WCF hizmeti için meta veriler kullanılabilir hale getirmek için [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Web hizmeti istemcisi oluşturma araçlarını kullanın: [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Hizmetleri bulma Aracı (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)ve `Add Web Reference` özellik Visual Studio'da; meta verileri yayını etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cfb33-112">To make the metadata for a WCF service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="cfb33-113">Daha fazla bilgi için [meta veri uç noktalarını yayımlama](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="cfb33-113">For more information, see [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfb33-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfb33-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cfb33-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfb33-115">Description</span></span>  
 <span data-ttu-id="cfb33-116">Aşağıdaki örnek kod ile uyumlu bir WCF uç noktası ekleme gösterir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmet istemci kodu ve alternatif olarak, bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="cfb33-116">The following example code demonstrates how to add a WCF endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cfb33-117">Kod</span><span class="sxs-lookup"><span data-stu-id="cfb33-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cfb33-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfb33-118">See also</span></span>

- [<span data-ttu-id="cfb33-119">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="cfb33-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
