---
title: WCF Keşfetme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 63c6589cb2ecff9f0a5e7c8bb61b454f6516c98c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600185"
---
# <a name="wcf-discovery"></a><span data-ttu-id="ec8ba-102">WCF Keşfetme</span><span class="sxs-lookup"><span data-stu-id="ec8ba-102">WCF Discovery</span></span>
<span data-ttu-id="ec8ba-103">Windows Communication Foundation (WCF), WS-Discovery protokolünü kullanarak birlikte çalışabilen bir şekilde hizmetlerin çalışma zamanında keşfedilmesini sağlamak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="ec8ba-104">WCF Hizmetleri, çok noktaya yayın iletisi veya bulma proxy sunucusu kullanarak ağ üzerinde kullanılabilirlik durumunu duyurur.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="ec8ba-105">İstemci uygulamaları, bir dizi ölçütü karşılayan hizmetleri bulmak için ağda veya bulma proxy sunucusunda arama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="ec8ba-106">Bu bölümdeki konularda bir genel bakış sağlanır ve bu özelliğin programlama modeli ayrıntılı olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec8ba-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ec8ba-107">In This Section</span></span>  
 [<span data-ttu-id="ec8ba-108">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ec8ba-108">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="ec8ba-109">WCF tarafından sağlanan WS-Discovery desteğine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="ec8ba-110">WCF Keşif Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="ec8ba-110">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="ec8ba-111">Nesne modelindeki sınıfları ve WS-Discovery desteğinin genişletilebilirliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="ec8ba-112">Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme</span><span class="sxs-lookup"><span data-stu-id="ec8ba-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="ec8ba-113">Windows Communication Foundation (WCF) hizmetini nasıl bulunabilir hale getirmek istediğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="ec8ba-114">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="ec8ba-114">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="ec8ba-115">Bulma proxy 'si uygulamak için gereken adımları, bulma proxy 'sine kaydeden keşfedilebilir bir hizmeti ve keşfedilebilir hizmeti bulmak için bulma proxy 'sini kullanan bir istemciyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="ec8ba-116">Keşif Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec8ba-116">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="ec8ba-117">Bazı yeni keşif özelliklerinin prototip uygulamasına kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="ec8ba-118">Ayrıca, kullanılacak bulma sürümünün nasıl kullanılacağına ilişkin bir genel bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="ec8ba-119">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec8ba-119">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="ec8ba-120">Yapılandırmada bulmanın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="ec8ba-121">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ec8ba-121">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="ec8ba-122">Bir WCF istemci uygulaması yazarken bulma Istemci kanalının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec8ba-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
