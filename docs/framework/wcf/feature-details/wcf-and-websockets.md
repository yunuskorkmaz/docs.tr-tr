---
title: WCF ve WebSockets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 726b23f0dc3f5953611010dca5260cc19c7adaaf
ms.sourcegitcommit: 8d14e8c1b15009330c9880f8523686158924e1a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2017
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="75106-102">WCF ve WebSockets</span><span class="sxs-lookup"><span data-stu-id="75106-102">WCF and WebSockets</span></span>
<span data-ttu-id="75106-103">.NET Framework 4.5, Windows Communication Foundation'da WebSockets desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="75106-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="75106-104">WebSockets standart HTTP 80 ve 443 bağlantı noktalarını çift yönlü iletişimi sağlayan bir verimli, standartlara dayalı teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="75106-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="75106-105">Standart HTTP bağlantı kullanımını aracılarla web üzerinden iletişim WebSockets izin verin.</span><span class="sxs-lookup"><span data-stu-id="75106-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="75106-106">WebSocket aktarımı üzerinden iletişimi desteklemek için iki yeni standart bağlamaları eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="75106-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="75106-107"><xref:System.ServiceModel.NetHttpBinding>ve <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="75106-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="75106-108">WebSockets özgü ayarları yapılandırılabilir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> erişerek <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="75106-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="75106-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="75106-109">In This Section</span></span>  
 [<span data-ttu-id="75106-110">NetHttpBinding kullanma</span><span class="sxs-lookup"><span data-stu-id="75106-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="75106-111">Anlatılmaktadır <xref:System.ServiceModel.NetHttpBinding> ve nasıl yapılandırılacağı.</span><span class="sxs-lookup"><span data-stu-id="75106-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="75106-112">Nasıl yapılır: WebSockets üzerinden iletişim kuran bir WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="75106-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="75106-113">Websockets üzerinden iletişim kuran bir WCF Hizmeti oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="75106-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="75106-114">Başvuru</span><span class="sxs-lookup"><span data-stu-id="75106-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="75106-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="75106-115">Related Sections</span></span>
