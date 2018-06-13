---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510253"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="77173-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="77173-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="77173-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="77173-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77173-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="77173-104">ID</span></span>|<span data-ttu-id="77173-105">1032</span><span class="sxs-lookup"><span data-stu-id="77173-105">1032</span></span>|  
|<span data-ttu-id="77173-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="77173-106">Keywords</span></span>|<span data-ttu-id="77173-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="77173-107">WFRuntime</span></span>|  
|<span data-ttu-id="77173-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="77173-108">Level</span></span>|<span data-ttu-id="77173-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="77173-109">Verbose</span></span>|  
|<span data-ttu-id="77173-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="77173-110">Channel</span></span>|<span data-ttu-id="77173-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="77173-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77173-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77173-112">Description</span></span>  
 <span data-ttu-id="77173-113">Bir RuntimeWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="77173-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77173-114">İleti</span><span class="sxs-lookup"><span data-stu-id="77173-114">Message</span></span>  
 <span data-ttu-id="77173-115">'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesi zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="77173-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77173-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="77173-116">Details</span></span>  
  
|<span data-ttu-id="77173-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="77173-117">Data Item Name</span></span>|<span data-ttu-id="77173-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="77173-118">Data Item Type</span></span>|<span data-ttu-id="77173-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77173-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77173-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="77173-120">Activity</span></span>|<span data-ttu-id="77173-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="77173-121">xs:string</span></span>|<span data-ttu-id="77173-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="77173-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="77173-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="77173-123">DisplayName</span></span>|<span data-ttu-id="77173-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="77173-124">xs:string</span></span>|<span data-ttu-id="77173-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="77173-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="77173-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="77173-126">InstanceId</span></span>|<span data-ttu-id="77173-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="77173-127">xs:string</span></span>|<span data-ttu-id="77173-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="77173-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="77173-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="77173-129">AppDomain</span></span>|<span data-ttu-id="77173-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="77173-130">xs:string</span></span>|<span data-ttu-id="77173-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="77173-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
