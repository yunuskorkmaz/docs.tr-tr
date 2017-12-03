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
ms.openlocfilehash: db529ed413d70165c7813e23ce8f164262c8e16b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="b95f0-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="b95f0-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="b95f0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b95f0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b95f0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b95f0-104">ID</span></span>|<span data-ttu-id="b95f0-105">1131</span><span class="sxs-lookup"><span data-stu-id="b95f0-105">1131</span></span>|  
|<span data-ttu-id="b95f0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b95f0-106">Keywords</span></span>|<span data-ttu-id="b95f0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b95f0-107">WFRuntime</span></span>|  
|<span data-ttu-id="b95f0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b95f0-108">Level</span></span>|<span data-ttu-id="b95f0-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="b95f0-109">Information</span></span>|  
|<span data-ttu-id="b95f0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b95f0-110">Channel</span></span>|<span data-ttu-id="b95f0-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b95f0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b95f0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b95f0-112">Description</span></span>  
 <span data-ttu-id="b95f0-113">CacheMetadata adımı sırasında InvokeMethod etkinlik, zaman uyumsuz desen yöntemi çağrılırken kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b95f0-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b95f0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b95f0-114">Message</span></span>  
 <span data-ttu-id="b95f0-115">InvokeMethod '%1' - '%2' ve '%3' zaman uyumsuz desen yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b95f0-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b95f0-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b95f0-116">Details</span></span>  
  
|<span data-ttu-id="b95f0-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b95f0-117">Data Item Name</span></span>|<span data-ttu-id="b95f0-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b95f0-118">Data Item Type</span></span>|<span data-ttu-id="b95f0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b95f0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b95f0-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="b95f0-120">InvokeMethod</span></span>|<span data-ttu-id="b95f0-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="b95f0-121">xs:string</span></span>|<span data-ttu-id="b95f0-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b95f0-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="b95f0-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="b95f0-123">BeginMethod</span></span>|<span data-ttu-id="b95f0-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="b95f0-124">xs:string</span></span>|<span data-ttu-id="b95f0-125">Begin yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="b95f0-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="b95f0-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="b95f0-126">EndMethod</span></span>|<span data-ttu-id="b95f0-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="b95f0-127">xs:string</span></span>|<span data-ttu-id="b95f0-128">End yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="b95f0-128">The name of the end method.</span></span>|  
|<span data-ttu-id="b95f0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b95f0-129">AppDomain</span></span>|<span data-ttu-id="b95f0-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="b95f0-130">xs:string</span></span>|<span data-ttu-id="b95f0-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b95f0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
