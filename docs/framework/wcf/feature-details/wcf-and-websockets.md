---
title: WCF ve WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: df4a251eb5a570c9fedf19d385a027e23481afed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594952"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="a8612-102">WCF ve WebSockets</span><span class="sxs-lookup"><span data-stu-id="a8612-102">WCF and WebSockets</span></span>
<span data-ttu-id="a8612-103">.NET Framework 4,5, Windows Communication Foundation için WebSockets desteğini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="a8612-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="a8612-104">WebSockets, standart HTTP bağlantı noktaları 80 ve 443 üzerinden çift yönlü iletişim sağlayan verimli, standartlara dayalı bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="a8612-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="a8612-105">Standart HTTP bağlantı noktalarının kullanımı, WebSockets 'in aracılar aracılığıyla Web üzerinden iletişim kurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a8612-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="a8612-106">WebSocket aktarımı üzerinden iletişimi desteklemek için iki yeni standart bağlama eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8612-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="a8612-107"><xref:System.ServiceModel.NetHttpBinding> ve <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="a8612-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="a8612-108">WebSockets 'e özgü ayarlar, özelliğine erişerek üzerinde yapılandırılabilir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> .</span><span class="sxs-lookup"><span data-stu-id="a8612-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="a8612-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a8612-109">In This Section</span></span>  
 [<span data-ttu-id="a8612-110">NetHttpBinding Kullanma</span><span class="sxs-lookup"><span data-stu-id="a8612-110">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)  
 <span data-ttu-id="a8612-111"><xref:System.ServiceModel.NetHttpBinding>Ve nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8612-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="a8612-112">Nasıl yapılır: WebSockets Üzerinden İletişim Kuran Bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8612-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="a8612-113">WebSockets üzerinden iletişim kuran bir WCF hizmeti oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a8612-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a8612-114">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a8612-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8612-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a8612-115">Related Sections</span></span>
