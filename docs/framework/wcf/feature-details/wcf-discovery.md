---
title: WCF Keşfetme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 175f79096d2bbda81a602d38e027d5a6d871fa12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768699"
---
# <a name="wcf-discovery"></a><span data-ttu-id="877fe-102">WCF Keşfetme</span><span class="sxs-lookup"><span data-stu-id="877fe-102">WCF Discovery</span></span>
<span data-ttu-id="877fe-103">Windows Communication Foundation (WCF) WS bulma protokolünü kullanarak birlikte çalışabilir bir şekilde çalışma zamanında bulunabilir olması hizmetleri etkinleştirmek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="877fe-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="877fe-104">WCF hizmetleri, çok noktaya yayın ileti kullanarak ağ veya bulma proxy sunucu duyurmaktan.</span><span class="sxs-lookup"><span data-stu-id="877fe-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="877fe-105">İstemci uygulamaları, ağ veya bir dizi kriteri karşılayan Hizmetleri bulmak için bulma proxy sunucusu arama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="877fe-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="877fe-106">Bu bölümdeki konular, genel bir bakış sağlar ve ayrıntılı bu özellik için programlama modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="877fe-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="877fe-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="877fe-107">In This Section</span></span>  
 [<span data-ttu-id="877fe-108">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="877fe-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="877fe-109">WCF tarafından sağlanan WS-bulma desteği'ne genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="877fe-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="877fe-110">WCF Bulma Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="877fe-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="877fe-111">Nesne modeli ve genişletilebilirlik WS-bulma destek sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="877fe-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="877fe-112">Nasıl yapılır: Bir WCF hizmeti ve istemci programlı bir şekilde Keşfedilebilirlik ekleme</span><span class="sxs-lookup"><span data-stu-id="877fe-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="877fe-113">Bir Windows Communication Foundation (WCF) hizmeti bulunabilir hale gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="877fe-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="877fe-114">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="877fe-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="877fe-115">Keşif proxy'si, Keşif proxy'sine kayıtlı bir bulunabilir hizmet ve keşfedilebilir hizmeti bulmak için keşif proxy'sini kullanan bir istemci uygulamak için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="877fe-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="877fe-116">Keşif Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="877fe-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="877fe-117">Bazı yeni bulma özelliklerinin bir prototip uygulamasını kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="877fe-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="877fe-118">Ayrıca bulma sürümün kullanılacağını seçme hakkında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="877fe-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="877fe-119">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="877fe-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="877fe-120">Yapılandırmada bulma yapılandırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="877fe-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="877fe-121">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="877fe-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="877fe-122">WCF istemci uygulaması yazarken keşif istemcisi kanalını kullanma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="877fe-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
