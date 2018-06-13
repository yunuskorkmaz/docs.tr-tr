---
title: Keşif Sürümü Oluşturma
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 18c160e5e08ed9b6733bed9d5e40a4dde00dfd1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489186"
---
# <a name="discovery-versioning"></a><span data-ttu-id="1a1e6-102">Keşif Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a1e6-102">Discovery Versioning</span></span>
<span data-ttu-id="1a1e6-103">Bu konu, bazı yeni bulma özellikler uyarlamasını kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-103">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="1a1e6-104">Ayrıca bulma sürümün kullanılacağını seçme hakkında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-104">It also gives an overview on how to select the discovery version to use.</span></span>  
  
## <a name="discovery-versioning"></a><span data-ttu-id="1a1e6-105">Keşif Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a1e6-105">Discovery Versioning</span></span>  
 <span data-ttu-id="1a1e6-106">Bulma özelliği üç WS_Discovery protokol sürümleri için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-106">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="1a1e6-107">Bulma API'leri kullanmak istediğiniz protokol sürümünü seçmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-107">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="1a1e6-108">Bu belgede kısaca sürüm oluşturma ile ilgili ayarları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-108">This document briefly describes the versioning-related settings.</span></span>  
  
 <span data-ttu-id="1a1e6-109">Aşağıdaki bulma sınıflar şimdi sahip bir <xref:System.ServiceModel.Discovery.DiscoveryVersion> özelliği ve Al bir <xref:System.ServiceModel.Discovery.DiscoveryVersion> kendi oluşturucu bağımsız değişkeni:</span><span class="sxs-lookup"><span data-stu-id="1a1e6-109">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="1a1e6-110">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="1a1e6-110">DiscoveryVersion.WSDiscoveryApril2005</span></span>  
 <span data-ttu-id="1a1e6-111">Sağlama <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> Oluşturucusu parametreyi WS bulma protokolünü April2005 sürümünü kullanmanız uygulama yapar.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-111">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="1a1e6-112">Bu sürüm, WS-Bulma Protokolü Belirtimi yayımlanan sürüme karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-112">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="1a1e6-113">Bu sürüm, WS-bulma April2005 sürümünü kullanan eski uygulaması ile birlikte çalışmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-113">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>  
  
### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="1a1e6-114">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="1a1e6-114">DiscoveryVersion.WSDiscovery11</span></span>  
 <span data-ttu-id="1a1e6-115">API tarafından kullanılan varsayılan bulma sürüm <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-115">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="1a1e6-116">Bu WS bulma protokolünü geçerli standartlaştırılmış sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-116">This is the current standardized version of the WS-Discovery protocol.</span></span>  
  
## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="1a1e6-117">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="1a1e6-117">DiscoveryVersion.WSDiscoveryCD1</span></span>  
 <span data-ttu-id="1a1e6-118">Sağlama <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> kullanmak uygulama Oluşturucu parametresini getirir komitesi WS bulma protokolünü 1 sürümü taslak.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-118">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="1a1e6-119">Bu protokol sürümü WS bulma protokolünü CD1 sürümünü çalıştıran uygulamaları ile birlikte çalışmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-119">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="1a1e6-120">Farklı bulma sürümlerini tek hizmet ana bilgisayarda için birden fazla UDP bulma uç noktası destekleme</span><span class="sxs-lookup"><span data-stu-id="1a1e6-120">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>  
 <span data-ttu-id="1a1e6-121">Farklı bulma sürümlerini tek hizmet ana bilgisayarda için birden çok UDP bulma uç noktaları kullanıma sunmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-121">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="1a1e6-122">Bunu yapmak için her UDP bulma uç noktası için benzersiz bir adresi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-122">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="1a1e6-123">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a1e6-123">The following example shows how to do this.</span></span>  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
