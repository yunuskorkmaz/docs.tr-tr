---
title: 1131 - InvokeMethodUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 739357df85ceb73e246adcb2b09f88d270d853ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="9cd71-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="9cd71-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="9cd71-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9cd71-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cd71-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9cd71-104">ID</span></span>|<span data-ttu-id="9cd71-105">1131</span><span class="sxs-lookup"><span data-stu-id="9cd71-105">1131</span></span>|  
|<span data-ttu-id="9cd71-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9cd71-106">Keywords</span></span>|<span data-ttu-id="9cd71-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9cd71-107">WFRuntime</span></span>|  
|<span data-ttu-id="9cd71-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9cd71-108">Level</span></span>|<span data-ttu-id="9cd71-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9cd71-109">Information</span></span>|  
|<span data-ttu-id="9cd71-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9cd71-110">Channel</span></span>|<span data-ttu-id="9cd71-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9cd71-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9cd71-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cd71-112">Description</span></span>  
 <span data-ttu-id="9cd71-113">CacheMetadata adımı sırasında InvokeMethod etkinlik, zaman uyumsuz desen yöntemi çağrılırken kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cd71-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9cd71-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9cd71-114">Message</span></span>  
 <span data-ttu-id="9cd71-115">InvokeMethod '%1' - '%2' ve '%3' zaman uyumsuz desen yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cd71-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9cd71-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9cd71-116">Details</span></span>  
  
|<span data-ttu-id="9cd71-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9cd71-117">Data Item Name</span></span>|<span data-ttu-id="9cd71-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9cd71-118">Data Item Type</span></span>|<span data-ttu-id="9cd71-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cd71-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9cd71-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9cd71-120">InvokeMethod</span></span>|<span data-ttu-id="9cd71-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="9cd71-121">xs:string</span></span>|<span data-ttu-id="9cd71-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9cd71-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9cd71-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="9cd71-123">BeginMethod</span></span>|<span data-ttu-id="9cd71-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="9cd71-124">xs:string</span></span>|<span data-ttu-id="9cd71-125">Begin yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="9cd71-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="9cd71-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="9cd71-126">EndMethod</span></span>|<span data-ttu-id="9cd71-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="9cd71-127">xs:string</span></span>|<span data-ttu-id="9cd71-128">End yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="9cd71-128">The name of the end method.</span></span>|  
|<span data-ttu-id="9cd71-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9cd71-129">AppDomain</span></span>|<span data-ttu-id="9cd71-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="9cd71-130">xs:string</span></span>|<span data-ttu-id="9cd71-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9cd71-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
