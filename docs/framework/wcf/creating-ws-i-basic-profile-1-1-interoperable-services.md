---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389756"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="91409-102">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="91409-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="91409-103">WCF hizmet bitiş noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilir şekilde yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="91409-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="91409-104">Hizmet <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> bitiş noktanız için bağlama türü olarak türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="91409-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="91409-105">Hizmet bitiş noktanızda geri arama ve oturum sözleşmesi özelliklerini veya işlem davranışlarını kullanmayın</span><span class="sxs-lookup"><span data-stu-id="91409-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="91409-106">Bağlamada HTTPS ve aktarım düzeyinde istemci kimlik doğrulaması için isteğe bağlı olarak destek etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91409-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="91409-107"><xref:System.ServiceModel.BasicHttpBinding> Sınıfın aşağıdaki özellikleri WS-I Temel Profil 1.1'in ötesinde işlevsellik gerektirir:</span><span class="sxs-lookup"><span data-stu-id="91409-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="91409-108">İleti Aktarım Optimizasyonu Mekanizması (MTOM) ileti <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> kodlama özelliği tarafından denetlendi.</span><span class="sxs-lookup"><span data-stu-id="91409-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="91409-109">MTOM'u kullanmamak için <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> bu özelliği varsayılan değerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="91409-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="91409-110"><xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> Değer tarafından denetlenen ileti güvenliği, WS-I Temel Güvenlik Profili 1.0 ile uyumlu WS-Security desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="91409-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="91409-111">WS-Security'yi kullanmamak için <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> bu özelliği varsayılan değerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="91409-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="91409-112">Bir WCF hizmetinin meta verilerini ASP.NET kullanılabilir hale getirmek için Web hizmeti istemci oluşturma araçlarını kullanın: [Web Hizmetleri Açıklama Dil Aracı (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29)Web Hizmetleri Bulma Aracı [(Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)ve Visual Studio'da **Web Başvuru Ekle** özelliği.</span><span class="sxs-lookup"><span data-stu-id="91409-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="91409-113">Meta veri yayımı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="91409-113">Enable metadata publication.</span></span> <span data-ttu-id="91409-114">Daha fazla bilgi için meta [veri uçlarını yayımlama](publishing-metadata-endpoints.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="91409-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91409-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="91409-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="91409-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91409-116">Description</span></span>  
 <span data-ttu-id="91409-117">Aşağıdaki örnek kod, kod halinde ASP.NET Web hizmeti istemcisiyle ve alternatif olarak bir yapılandırma dosyasında uyumlu bir WCF bitiş noktasının nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91409-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="91409-118">Kod</span><span class="sxs-lookup"><span data-stu-id="91409-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="91409-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91409-119">See also</span></span>

- [<span data-ttu-id="91409-120">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="91409-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
