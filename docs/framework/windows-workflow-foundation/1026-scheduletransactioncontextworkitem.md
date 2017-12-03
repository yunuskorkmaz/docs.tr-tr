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
ms.openlocfilehash: a5fb800718c1fd231d0cd02bf015333a44fa794f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="0c15d-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="0c15d-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0c15d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0c15d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c15d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0c15d-104">ID</span></span>|<span data-ttu-id="0c15d-105">1026</span><span class="sxs-lookup"><span data-stu-id="0c15d-105">1026</span></span>|  
|<span data-ttu-id="0c15d-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0c15d-106">Keywords</span></span>|<span data-ttu-id="0c15d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0c15d-107">WFRuntime</span></span>|  
|<span data-ttu-id="0c15d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0c15d-108">Level</span></span>|<span data-ttu-id="0c15d-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="0c15d-109">Verbose</span></span>|  
|<span data-ttu-id="0c15d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0c15d-110">Channel</span></span>|<span data-ttu-id="0c15d-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0c15d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c15d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c15d-112">Description</span></span>  
 <span data-ttu-id="0c15d-113">Bir TransactionContextWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c15d-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c15d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="0c15d-114">Message</span></span>  
 <span data-ttu-id="0c15d-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="0c15d-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c15d-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0c15d-116">Details</span></span>  
  
|<span data-ttu-id="0c15d-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0c15d-117">Data Item Name</span></span>|<span data-ttu-id="0c15d-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0c15d-118">Data Item Type</span></span>|<span data-ttu-id="0c15d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c15d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0c15d-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="0c15d-120">Activity</span></span>|<span data-ttu-id="0c15d-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c15d-121">xs:string</span></span>|<span data-ttu-id="0c15d-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="0c15d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0c15d-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="0c15d-123">DisplayName</span></span>|<span data-ttu-id="0c15d-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c15d-124">xs:string</span></span>|<span data-ttu-id="0c15d-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="0c15d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0c15d-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="0c15d-126">InstanceId</span></span>|<span data-ttu-id="0c15d-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c15d-127">xs:string</span></span>|<span data-ttu-id="0c15d-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="0c15d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0c15d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0c15d-129">AppDomain</span></span>|<span data-ttu-id="0c15d-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c15d-130">xs:string</span></span>|<span data-ttu-id="0c15d-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0c15d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
