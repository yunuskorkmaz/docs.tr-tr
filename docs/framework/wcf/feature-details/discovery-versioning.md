---
description: 'Daha fazla bilgi edinin: bulma sürümü oluşturma'
title: Keşif Sürümü Oluşturma
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 075fefce0477810336c8b857343984070ed89b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743193"
---
# <a name="discovery-versioning"></a><span data-ttu-id="2555a-103">Keşif Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2555a-103">Discovery Versioning</span></span>

<span data-ttu-id="2555a-104">Bu konu, bazı yeni keşif özelliklerinin uygulanmasına ilişkin kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2555a-104">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="2555a-105">Ayrıca, kullanılacak bulma sürümünün nasıl kullanılacağına ilişkin bir genel bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="2555a-105">It also gives an overview on how to select the discovery version to use.</span></span>

## <a name="discovery-versioning"></a><span data-ttu-id="2555a-106">Keşif Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2555a-106">Discovery Versioning</span></span>

<span data-ttu-id="2555a-107">Bulma özelliği, WS_Discovery protokolünün üç sürümü için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="2555a-107">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="2555a-108">Bulma API 'Leri, kullanmak istediğiniz protokolün sürümünü seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2555a-108">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="2555a-109">Bu belge, sürüm oluşturma ile ilgili ayarları kısaca açıklar.</span><span class="sxs-lookup"><span data-stu-id="2555a-109">This document briefly describes the versioning-related settings.</span></span>

<span data-ttu-id="2555a-110">Aşağıdaki bulgu sınıfları artık bir özelliğe sahiptir <xref:System.ServiceModel.Discovery.DiscoveryVersion> ve <xref:System.ServiceModel.Discovery.DiscoveryVersion> oluşturucularında bir bağımsız değişken alır:</span><span class="sxs-lookup"><span data-stu-id="2555a-110">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>

### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="2555a-111">DiscoveryVersion. WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="2555a-111">DiscoveryVersion.WSDiscoveryApril2005</span></span>

<span data-ttu-id="2555a-112"><xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005>Oluşturucu parametresi olarak sağlanması, uygulamanın WS-Discovery protokolünün April2005 sürümünü kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2555a-112">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="2555a-113">Bu sürüm, WS-Discovery protokol belirtiminin yayımlanmış sürümüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2555a-113">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="2555a-114">Bu sürüm, WS-Discovery April2005 sürümünü kullanan eski uygulamayla birlikte çalışmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2555a-114">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>

### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="2555a-115">DiscoveryVersion. WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="2555a-115">DiscoveryVersion.WSDiscovery11</span></span>

<span data-ttu-id="2555a-116">API 'Ler tarafından kullanılan varsayılan bulma sürümü <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11> .</span><span class="sxs-lookup"><span data-stu-id="2555a-116">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="2555a-117">Bu, WS-Discovery protokolünün geçerli standartlaştırılmış sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="2555a-117">This is the current standardized version of the WS-Discovery protocol.</span></span>

## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="2555a-118">DiscoveryVersion. WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="2555a-118">DiscoveryVersion.WSDiscoveryCD1</span></span>

<span data-ttu-id="2555a-119"><xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1>Oluşturucu parametresi olarak sağlanması, uygulamanın WS-Discovery protokolünün komite taslak 1 sürümünü kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2555a-119">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="2555a-120">Protokolün bu sürümü, WS-Discovery protokolünün CD1 sürümünü çalıştıran uygulamalarla birlikte çalışmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2555a-120">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>

## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="2555a-121">Tek bir hizmet konağında farklı bulma sürümleri için birden çok UDP bulma uç noktası destekleme</span><span class="sxs-lookup"><span data-stu-id="2555a-121">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>

<span data-ttu-id="2555a-122">Tek bir hizmet konağında farklı bulma sürümleri için birden çok UDP bulma uç noktası göstermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2555a-122">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="2555a-123">Bunu yapmak için, her bir UDP bulma uç noktası için benzersiz bir adres belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2555a-123">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="2555a-124">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2555a-124">The following example shows how to do this.</span></span>

```csharp
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);

newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionApril2005");

serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);
```
