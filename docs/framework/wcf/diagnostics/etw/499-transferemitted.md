---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774939"
---
# <a name="499---transferemitted"></a><span data-ttu-id="aff1f-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="aff1f-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="aff1f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aff1f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aff1f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="aff1f-104">ID</span></span>|<span data-ttu-id="aff1f-105">499</span><span class="sxs-lookup"><span data-stu-id="aff1f-105">499</span></span>|  
|<span data-ttu-id="aff1f-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="aff1f-106">Keywords</span></span>|<span data-ttu-id="aff1f-107">Sorun giderme, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="aff1f-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="aff1f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="aff1f-108">Level</span></span>|<span data-ttu-id="aff1f-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="aff1f-109">LogAlways</span></span>|  
|<span data-ttu-id="aff1f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="aff1f-110">Channel</span></span>|<span data-ttu-id="aff1f-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="aff1f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aff1f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff1f-112">Description</span></span>  
 <span data-ttu-id="aff1f-113">Bu olay, aktarımı olay gerçekleştiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="aff1f-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aff1f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="aff1f-114">Message</span></span>  
 <span data-ttu-id="aff1f-115">Olay yayınlanan aktarır.</span><span class="sxs-lookup"><span data-stu-id="aff1f-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aff1f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="aff1f-116">Details</span></span>  
  
|<span data-ttu-id="aff1f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="aff1f-117">Data Item Name</span></span>|<span data-ttu-id="aff1f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="aff1f-118">Data Item Type</span></span>|<span data-ttu-id="aff1f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff1f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aff1f-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="aff1f-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="aff1f-121">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aff1f-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="aff1f-122">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="aff1f-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="aff1f-123">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="aff1f-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="aff1f-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aff1f-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="aff1f-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="aff1f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
