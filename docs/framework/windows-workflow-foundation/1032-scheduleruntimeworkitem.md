---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924871"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="04c18-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="04c18-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="04c18-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="04c18-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04c18-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="04c18-104">ID</span></span>|<span data-ttu-id="04c18-105">1032</span><span class="sxs-lookup"><span data-stu-id="04c18-105">1032</span></span>|  
|<span data-ttu-id="04c18-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="04c18-106">Keywords</span></span>|<span data-ttu-id="04c18-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="04c18-107">WFRuntime</span></span>|  
|<span data-ttu-id="04c18-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="04c18-108">Level</span></span>|<span data-ttu-id="04c18-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="04c18-109">Verbose</span></span>|  
|<span data-ttu-id="04c18-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="04c18-110">Channel</span></span>|<span data-ttu-id="04c18-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="04c18-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="04c18-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04c18-112">Description</span></span>  
 <span data-ttu-id="04c18-113">Bir RuntimeWorkItem zamanlandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="04c18-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="04c18-114">İleti</span><span class="sxs-lookup"><span data-stu-id="04c18-114">Message</span></span>  
 <span data-ttu-id="04c18-115">Bir çalışma zamanı iş öğesi '%1', DisplayName etkinliği için zamanlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="04c18-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="04c18-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="04c18-116">Details</span></span>  
  
|<span data-ttu-id="04c18-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="04c18-117">Data Item Name</span></span>|<span data-ttu-id="04c18-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="04c18-118">Data Item Type</span></span>|<span data-ttu-id="04c18-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04c18-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="04c18-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="04c18-120">Activity</span></span>|<span data-ttu-id="04c18-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="04c18-121">xs:string</span></span>|<span data-ttu-id="04c18-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="04c18-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="04c18-123">displayName</span><span class="sxs-lookup"><span data-stu-id="04c18-123">DisplayName</span></span>|<span data-ttu-id="04c18-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="04c18-124">xs:string</span></span>|<span data-ttu-id="04c18-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="04c18-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="04c18-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="04c18-126">InstanceId</span></span>|<span data-ttu-id="04c18-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="04c18-127">xs:string</span></span>|<span data-ttu-id="04c18-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="04c18-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="04c18-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="04c18-129">AppDomain</span></span>|<span data-ttu-id="04c18-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="04c18-130">xs:string</span></span>|<span data-ttu-id="04c18-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="04c18-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
