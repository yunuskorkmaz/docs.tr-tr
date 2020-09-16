---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 5fc29432bdd55daff2d60d641a4cea4925278032
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543023"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="ebde2-102">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebde2-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="ebde2-103">WCF hizmet uç noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilen şekilde yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="ebde2-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="ebde2-104"><xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>Hizmet uç noktanız için bağlama türü olarak türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="ebde2-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="ebde2-105">Hizmet uç noktanıza geri çağırma ve oturum sözleşmesi özellikleri ya da işlem davranışları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="ebde2-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="ebde2-106">İsteğe bağlı olarak, bağlamada HTTPS ve aktarım düzeyi istemci kimlik doğrulaması desteğini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebde2-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="ebde2-107">Sınıfının aşağıdaki özellikleri <xref:System.ServiceModel.BasicHttpBinding> WS-ı temel profil 1,1 ' nin ötesinde işlevsellik gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ebde2-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="ebde2-108">İleti Iletimi Iyileştirme mekanizması (MTOM) özelliği tarafından denetlenen ileti kodlaması <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ebde2-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ebde2-109">Bu özelliği varsayılan değerinde bırakın ve bu, MTOM 'yi <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="ebde2-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="ebde2-110">Değere göre denetlenen ileti güvenliği, WS <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> -ı temel güvenlik profili 1,0 ile uyumlu WS-güvenlik desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebde2-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="ebde2-111">Bu özelliği, WS-Security ' i kullanmayan varsayılan değerinde bırakın <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ebde2-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="ebde2-112">Bir WCF hizmetinin meta verilerini ASP.NET için kullanılabilir hale getirmek için Web hizmeti istemci oluşturma araçları: [Web Hizmetleri Açıklama Dil Aracı (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Hizmetleri bulma aracı (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))ve Visual Studio 'daki **Web başvurusu Ekle** özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ebde2-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="ebde2-113">Meta veri yayımlamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ebde2-113">Enable metadata publication.</span></span> <span data-ttu-id="ebde2-114">Daha fazla bilgi için bkz. [meta veri uç noktalarını yayımlama](publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="ebde2-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebde2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebde2-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ebde2-116">Description</span><span class="sxs-lookup"><span data-stu-id="ebde2-116">Description</span></span>  
 <span data-ttu-id="ebde2-117">Aşağıdaki örnek kod, bir yapılandırma dosyasında, koddaki ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktasının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebde2-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ebde2-118">Kod</span><span class="sxs-lookup"><span data-stu-id="ebde2-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ebde2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebde2-119">See also</span></span>

- [<span data-ttu-id="ebde2-120">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="ebde2-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
