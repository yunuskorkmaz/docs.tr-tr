---
title: "WCF Keşfetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c11daa14a3897b05947dd6f8c3f3be99eb69c377
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-discovery"></a><span data-ttu-id="83029-102">WCF Keşfetme</span><span class="sxs-lookup"><span data-stu-id="83029-102">WCF Discovery</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="83029-103">WS bulma protokolünü kullanarak bir birlikte çalışabilen şekilde çalışma zamanında bulunabilir olması hizmetleri etkinleştirmek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="83029-103"> provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="83029-104">Hizmetleri kullanılabilirliklerini bir çok noktaya yayın ileti kullanarak ağ veya bulma proxy sunucu duyurusu.</span><span class="sxs-lookup"><span data-stu-id="83029-104"> services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="83029-105">İstemci uygulamaları, ağ veya bir ölçüt kümesine uyan Hizmetleri bulmak için bulma proxy sunucusu arama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83029-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="83029-106">Bu bölümdeki konular, genel bir bakış sağlar ve bu özellik ayrıntılı için programlama modelini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83029-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83029-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="83029-107">In This Section</span></span>  
 [<span data-ttu-id="83029-108">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="83029-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="83029-109">WS-bulma desteği tarafından sağlanan genel bir bakış sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83029-109">Provides an overview of WS-Discovery support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="83029-110">WCF Bulma Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="83029-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="83029-111">Nesne modeli ve genişletilebilirlik WS-bulma destek sınıflarında açıklar.</span><span class="sxs-lookup"><span data-stu-id="83029-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="83029-112">Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme</span><span class="sxs-lookup"><span data-stu-id="83029-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="83029-113">Nasıl yapılacağını gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="83029-113">Shows how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span>  
  
 [<span data-ttu-id="83029-114">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="83029-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="83029-115">Keşif proxy'si, Keşif proxy'sine kayıtlı bir bulunabilir hizmet ve bulunabilir hizmet bulmak için keşif proxy'si kullanan istemci uygulamak için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="83029-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="83029-116">Keşif Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="83029-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="83029-117">Bazı yeni bulma özellikler prototip uyarlamasını kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="83029-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="83029-118">Ayrıca bulma sürümün kullanılacağını seçme hakkında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="83029-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="83029-119">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="83029-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="83029-120">Bulma yapılandırmasını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="83029-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="83029-121">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="83029-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="83029-122">Keşif istemcisi kanalını yazılırken kullanılacak gösterilmiştir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="83029-122">Shows how to use a Discovery Client Channel when writing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span>
