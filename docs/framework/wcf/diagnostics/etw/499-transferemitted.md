---
description: 'Hakkında daha fazla bilgi edinin: 499-Transferyayınlandı'
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: d9802ef718ce6091abe1d1092ad6bb7e7fff108a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783579"
---
# <a name="499---transferemitted"></a><span data-ttu-id="7732e-103">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="7732e-103">499 - TransferEmitted</span></span>

## <a name="properties"></a><span data-ttu-id="7732e-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7732e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7732e-105">ID</span><span class="sxs-lookup"><span data-stu-id="7732e-105">ID</span></span>|<span data-ttu-id="7732e-106">499</span><span class="sxs-lookup"><span data-stu-id="7732e-106">499</span></span>|  
|<span data-ttu-id="7732e-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="7732e-107">Keywords</span></span>|<span data-ttu-id="7732e-108">Sorun giderme, Kullanıcıetkinlikleri, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="7732e-108">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="7732e-109">Level</span><span class="sxs-lookup"><span data-stu-id="7732e-109">Level</span></span>|<span data-ttu-id="7732e-110">Günlüğe kaydetme her zaman</span><span class="sxs-lookup"><span data-stu-id="7732e-110">LogAlways</span></span>|  
|<span data-ttu-id="7732e-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="7732e-111">Channel</span></span>|<span data-ttu-id="7732e-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="7732e-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7732e-113">Description</span><span class="sxs-lookup"><span data-stu-id="7732e-113">Description</span></span>  

 <span data-ttu-id="7732e-114">Bu olay, aktarım olayı gerçekleştiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="7732e-114">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7732e-115">İleti</span><span class="sxs-lookup"><span data-stu-id="7732e-115">Message</span></span>  

 <span data-ttu-id="7732e-116">Aktarım olayı yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="7732e-116">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7732e-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7732e-117">Details</span></span>  
  
|<span data-ttu-id="7732e-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7732e-118">Data Item Name</span></span>|<span data-ttu-id="7732e-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7732e-119">Data Item Type</span></span>|<span data-ttu-id="7732e-120">Description</span><span class="sxs-lookup"><span data-stu-id="7732e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7732e-121">HostReference</span><span class="sxs-lookup"><span data-stu-id="7732e-121">HostReference</span></span>|`xs:string`|<span data-ttu-id="7732e-122">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7732e-122">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7732e-123">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7732e-123">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7732e-124">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="7732e-124">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7732e-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7732e-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7732e-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7732e-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
