---
title: 1026 - ScheduleTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c99ddf9c5d4a8fa468303fb198abc349ace6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="36feb-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="36feb-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="36feb-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="36feb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36feb-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="36feb-104">ID</span></span>|<span data-ttu-id="36feb-105">1026</span><span class="sxs-lookup"><span data-stu-id="36feb-105">1026</span></span>|  
|<span data-ttu-id="36feb-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="36feb-106">Keywords</span></span>|<span data-ttu-id="36feb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="36feb-107">WFRuntime</span></span>|  
|<span data-ttu-id="36feb-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="36feb-108">Level</span></span>|<span data-ttu-id="36feb-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="36feb-109">Verbose</span></span>|  
|<span data-ttu-id="36feb-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="36feb-110">Channel</span></span>|<span data-ttu-id="36feb-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="36feb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="36feb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36feb-112">Description</span></span>  
 <span data-ttu-id="36feb-113">Bir TransactionContextWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="36feb-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="36feb-114">İleti</span><span class="sxs-lookup"><span data-stu-id="36feb-114">Message</span></span>  
 <span data-ttu-id="36feb-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="36feb-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="36feb-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="36feb-116">Details</span></span>  
  
|<span data-ttu-id="36feb-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="36feb-117">Data Item Name</span></span>|<span data-ttu-id="36feb-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="36feb-118">Data Item Type</span></span>|<span data-ttu-id="36feb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36feb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="36feb-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="36feb-120">Activity</span></span>|<span data-ttu-id="36feb-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="36feb-121">xs:string</span></span>|<span data-ttu-id="36feb-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="36feb-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="36feb-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="36feb-123">DisplayName</span></span>|<span data-ttu-id="36feb-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="36feb-124">xs:string</span></span>|<span data-ttu-id="36feb-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="36feb-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="36feb-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="36feb-126">InstanceId</span></span>|<span data-ttu-id="36feb-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="36feb-127">xs:string</span></span>|<span data-ttu-id="36feb-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="36feb-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="36feb-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="36feb-129">AppDomain</span></span>|<span data-ttu-id="36feb-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="36feb-130">xs:string</span></span>|<span data-ttu-id="36feb-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="36feb-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
