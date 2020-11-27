---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 96ea253fd61652a3719eaf8b1a4d31aa88337eeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294267"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="becbd-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="becbd-102">1036 - RuntimeTransactionCompletionRequested</span></span>

## <a name="properties"></a><span data-ttu-id="becbd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="becbd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="becbd-104">ID</span><span class="sxs-lookup"><span data-stu-id="becbd-104">ID</span></span>|<span data-ttu-id="becbd-105">1036</span><span class="sxs-lookup"><span data-stu-id="becbd-105">1036</span></span>|  
|<span data-ttu-id="becbd-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="becbd-106">Keywords</span></span>|<span data-ttu-id="becbd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="becbd-107">WFRuntime</span></span>|  
|<span data-ttu-id="becbd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="becbd-108">Level</span></span>|<span data-ttu-id="becbd-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="becbd-109">Verbose</span></span>|  
|<span data-ttu-id="becbd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="becbd-110">Channel</span></span>|<span data-ttu-id="becbd-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="becbd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="becbd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="becbd-112">Description</span></span>  

 <span data-ttu-id="becbd-113">Bir etkinliğin çalışma zamanı işleminin tamamlandığını zamanladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="becbd-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="becbd-114">İleti</span><span class="sxs-lookup"><span data-stu-id="becbd-114">Message</span></span>  

 <span data-ttu-id="becbd-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si çalışma zamanı işleminin tamamlanmasını zamanladı.</span><span class="sxs-lookup"><span data-stu-id="becbd-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="becbd-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="becbd-116">Details</span></span>  
  
|<span data-ttu-id="becbd-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="becbd-117">Data Item Name</span></span>|<span data-ttu-id="becbd-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="becbd-118">Data Item Type</span></span>|<span data-ttu-id="becbd-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="becbd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="becbd-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="becbd-120">Activity</span></span>|<span data-ttu-id="becbd-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="becbd-121">xs:string</span></span>|<span data-ttu-id="becbd-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="becbd-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="becbd-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="becbd-123">DisplayName</span></span>|<span data-ttu-id="becbd-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="becbd-124">xs:string</span></span>|<span data-ttu-id="becbd-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="becbd-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="becbd-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="becbd-126">InstanceId</span></span>|<span data-ttu-id="becbd-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="becbd-127">xs:string</span></span>|<span data-ttu-id="becbd-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="becbd-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="becbd-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="becbd-129">AppDomain</span></span>|<span data-ttu-id="becbd-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="becbd-130">xs:string</span></span>|<span data-ttu-id="becbd-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="becbd-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
