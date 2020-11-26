---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: 654f961088c371ab53e4a81f40e3c63335efb1a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239594"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="07a2f-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="07a2f-102">1013 - CompleteExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="07a2f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="07a2f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07a2f-104">ID</span><span class="sxs-lookup"><span data-stu-id="07a2f-104">ID</span></span>|<span data-ttu-id="07a2f-105">1013</span><span class="sxs-lookup"><span data-stu-id="07a2f-105">1013</span></span>|  
|<span data-ttu-id="07a2f-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="07a2f-106">Keywords</span></span>|<span data-ttu-id="07a2f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="07a2f-107">WFRuntime</span></span>|  
|<span data-ttu-id="07a2f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="07a2f-108">Level</span></span>|<span data-ttu-id="07a2f-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="07a2f-109">Verbose</span></span>|  
|<span data-ttu-id="07a2f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="07a2f-110">Channel</span></span>|<span data-ttu-id="07a2f-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="07a2f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="07a2f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07a2f-112">Description</span></span>  

 <span data-ttu-id="07a2f-113">Bir ExecuteActivityWorkItem 'ın tamamlandığını belirtir</span><span class="sxs-lookup"><span data-stu-id="07a2f-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="07a2f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="07a2f-114">Message</span></span>  

 <span data-ttu-id="07a2f-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir ExecuteActivityWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="07a2f-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="07a2f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="07a2f-116">Details</span></span>  
  
|<span data-ttu-id="07a2f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="07a2f-117">Data Item Name</span></span>|<span data-ttu-id="07a2f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="07a2f-118">Data Item Type</span></span>|<span data-ttu-id="07a2f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07a2f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="07a2f-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="07a2f-120">Activity</span></span>|<span data-ttu-id="07a2f-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="07a2f-121">xs:string</span></span>|<span data-ttu-id="07a2f-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="07a2f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="07a2f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="07a2f-123">DisplayName</span></span>|<span data-ttu-id="07a2f-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="07a2f-124">xs:string</span></span>|<span data-ttu-id="07a2f-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="07a2f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="07a2f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="07a2f-126">InstanceId</span></span>|<span data-ttu-id="07a2f-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="07a2f-127">xs:string</span></span>|<span data-ttu-id="07a2f-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="07a2f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="07a2f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="07a2f-129">AppDomain</span></span>|<span data-ttu-id="07a2f-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="07a2f-130">xs:string</span></span>|<span data-ttu-id="07a2f-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="07a2f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
