---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 7ba2ada1fbd5217592b4e4e3cffd813ffbe978ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275251"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="50ad1-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="50ad1-102">1026 - ScheduleTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="50ad1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="50ad1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50ad1-104">ID</span><span class="sxs-lookup"><span data-stu-id="50ad1-104">ID</span></span>|<span data-ttu-id="50ad1-105">1026</span><span class="sxs-lookup"><span data-stu-id="50ad1-105">1026</span></span>|  
|<span data-ttu-id="50ad1-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="50ad1-106">Keywords</span></span>|<span data-ttu-id="50ad1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="50ad1-107">WFRuntime</span></span>|  
|<span data-ttu-id="50ad1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="50ad1-108">Level</span></span>|<span data-ttu-id="50ad1-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="50ad1-109">Verbose</span></span>|  
|<span data-ttu-id="50ad1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="50ad1-110">Channel</span></span>|<span data-ttu-id="50ad1-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="50ad1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="50ad1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50ad1-112">Description</span></span>  

 <span data-ttu-id="50ad1-113">Bir TransactionContextWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="50ad1-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="50ad1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="50ad1-114">Message</span></span>  

 <span data-ttu-id="50ad1-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir TransactionContextWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="50ad1-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="50ad1-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="50ad1-116">Details</span></span>  
  
|<span data-ttu-id="50ad1-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="50ad1-117">Data Item Name</span></span>|<span data-ttu-id="50ad1-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="50ad1-118">Data Item Type</span></span>|<span data-ttu-id="50ad1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50ad1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="50ad1-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="50ad1-120">Activity</span></span>|<span data-ttu-id="50ad1-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="50ad1-121">xs:string</span></span>|<span data-ttu-id="50ad1-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="50ad1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="50ad1-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="50ad1-123">DisplayName</span></span>|<span data-ttu-id="50ad1-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="50ad1-124">xs:string</span></span>|<span data-ttu-id="50ad1-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="50ad1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="50ad1-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="50ad1-126">InstanceId</span></span>|<span data-ttu-id="50ad1-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="50ad1-127">xs:string</span></span>|<span data-ttu-id="50ad1-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="50ad1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="50ad1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="50ad1-129">AppDomain</span></span>|<span data-ttu-id="50ad1-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="50ad1-130">xs:string</span></span>|<span data-ttu-id="50ad1-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="50ad1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
