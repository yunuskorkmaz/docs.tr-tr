---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: eb1cd12c45a276d5c3cb14f89205fff618121abc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320135"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="a30a8-102">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a30a8-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="a30a8-103">WCF hizmet uç noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilen şekilde yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="a30a8-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="a30a8-104">Hizmet uç noktanız için bağlama türü olarak <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="a30a8-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="a30a8-105">Hizmet uç noktanıza geri çağırma ve oturum sözleşmesi özellikleri ya da işlem davranışları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="a30a8-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="a30a8-106">İsteğe bağlı olarak, bağlamada HTTPS ve aktarım düzeyi istemci kimlik doğrulaması desteğini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a30a8-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="a30a8-107">@No__t-0 sınıfının aşağıdaki özellikleri, WS-ı temel profil 1,1 ' den daha fazla işlevsellik gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a30a8-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="a30a8-108">@No__t-0 özelliği tarafından denetlenen ileti Iletimi Iyileştirme mekanizması (MTOM) ileti kodlaması.</span><span class="sxs-lookup"><span data-stu-id="a30a8-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a30a8-109">Bu özelliği varsayılan değerinde bırakın, bu, MTOM 'yi kullanmak için <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> ' dır.</span><span class="sxs-lookup"><span data-stu-id="a30a8-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="a30a8-110">@No__t-0 değeri tarafından denetlenen ileti güvenliği, WS-ı temel güvenlik profili 1,0 ile uyumlu WS-güvenlik desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a30a8-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="a30a8-111">Bu özelliği, WS-Security ' i kullanmak için <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> olan varsayılan değerinde bırakın.</span><span class="sxs-lookup"><span data-stu-id="a30a8-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="a30a8-112">Bir WCF hizmetinin meta verilerini ASP.NET için kullanılabilir hale getirmek için Web hizmeti istemci oluşturma araçları: [Web Hizmetleri Açıklama Dili Aracı (wsdl. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Hizmetleri bulma aracı (Disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)ve Visual Studio 'da `Add Web Reference` özelliği kullanın; meta veri yayımlamayı etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a30a8-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="a30a8-113">Daha fazla bilgi için bkz. [meta veri uç noktalarını yayımlama](publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="a30a8-113">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a30a8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a30a8-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a30a8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a30a8-115">Description</span></span>  
 <span data-ttu-id="a30a8-116">Aşağıdaki örnek kod, bir yapılandırma dosyasında, koddaki ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktasının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a30a8-116">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a30a8-117">Kod</span><span class="sxs-lookup"><span data-stu-id="a30a8-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a30a8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a30a8-118">See also</span></span>

- [<span data-ttu-id="a30a8-119">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="a30a8-119">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
