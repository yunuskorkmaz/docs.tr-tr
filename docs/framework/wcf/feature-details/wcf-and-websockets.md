---
title: WCF ve WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: ac888db14ebd21c4aed2f717c1f71bed310b8388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498533"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="1e985-102">WCF ve WebSockets</span><span class="sxs-lookup"><span data-stu-id="1e985-102">WCF and WebSockets</span></span>
<span data-ttu-id="1e985-103">.NET Framework 4.5, Windows Communication Foundation'da WebSockets desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="1e985-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="1e985-104">WebSockets standart HTTP 80 ve 443 bağlantı noktalarını çift yönlü iletişimi sağlayan bir verimli, standartlara dayalı teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="1e985-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="1e985-105">Standart HTTP bağlantı kullanımını aracılarla web üzerinden iletişim WebSockets izin verin.</span><span class="sxs-lookup"><span data-stu-id="1e985-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="1e985-106">WebSocket aktarımı üzerinden iletişimi desteklemek için iki yeni standart bağlamaları eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e985-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="1e985-107"><xref:System.ServiceModel.NetHttpBinding> ve <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="1e985-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="1e985-108">WebSockets özgü ayarları yapılandırılabilir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> erişerek <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1e985-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="1e985-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1e985-109">In This Section</span></span>  
 [<span data-ttu-id="1e985-110">NetHttpBinding Kullanma</span><span class="sxs-lookup"><span data-stu-id="1e985-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="1e985-111">Anlatılmaktadır <xref:System.ServiceModel.NetHttpBinding> ve nasıl yapılandırılacağı.</span><span class="sxs-lookup"><span data-stu-id="1e985-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="1e985-112">Nasıl yapılır: WebSockets Üzerinden İletişim Kuran Bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e985-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="1e985-113">Websockets üzerinden iletişim kuran bir WCF Hizmeti oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1e985-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1e985-114">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1e985-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1e985-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1e985-115">Related Sections</span></span>
