---
description: 'Hakkında daha fazla bilgi edinin: 1131-ınvokemethodumevsimsyncmodel'
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 59d8e5e1fe7c5b038df6fce3211fd01977abc4f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667323"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="f0d34-103">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="f0d34-103">1131 - InvokeMethodUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="f0d34-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f0d34-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0d34-105">ID</span><span class="sxs-lookup"><span data-stu-id="f0d34-105">ID</span></span>|<span data-ttu-id="f0d34-106">1131</span><span class="sxs-lookup"><span data-stu-id="f0d34-106">1131</span></span>|  
|<span data-ttu-id="f0d34-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f0d34-107">Keywords</span></span>|<span data-ttu-id="f0d34-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f0d34-108">WFRuntime</span></span>|  
|<span data-ttu-id="f0d34-109">Level</span><span class="sxs-lookup"><span data-stu-id="f0d34-109">Level</span></span>|<span data-ttu-id="f0d34-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="f0d34-110">Information</span></span>|  
|<span data-ttu-id="f0d34-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="f0d34-111">Channel</span></span>|<span data-ttu-id="f0d34-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="f0d34-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f0d34-113">Description</span><span class="sxs-lookup"><span data-stu-id="f0d34-113">Description</span></span>  

 <span data-ttu-id="f0d34-114">CacheMetadata adımı sırasında InvokeMethod etkinliği yöntemi çağrılırken zaman uyumsuz bir model kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0d34-114">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f0d34-115">İleti</span><span class="sxs-lookup"><span data-stu-id="f0d34-115">Message</span></span>  

 <span data-ttu-id="f0d34-116">InvokeMethod ' %1 '-Yöntem ' %2 ' ve ' %3 ' zaman uyumsuz modelini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="f0d34-116">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f0d34-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f0d34-117">Details</span></span>  
  
|<span data-ttu-id="f0d34-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f0d34-118">Data Item Name</span></span>|<span data-ttu-id="f0d34-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f0d34-119">Data Item Type</span></span>|<span data-ttu-id="f0d34-120">Description</span><span class="sxs-lookup"><span data-stu-id="f0d34-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f0d34-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f0d34-121">InvokeMethod</span></span>|<span data-ttu-id="f0d34-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="f0d34-122">xs:string</span></span>|<span data-ttu-id="f0d34-123">InvokeMethod etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f0d34-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f0d34-124">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="f0d34-124">BeginMethod</span></span>|<span data-ttu-id="f0d34-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="f0d34-125">xs:string</span></span>|<span data-ttu-id="f0d34-126">Begin yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="f0d34-126">The name of the begin method.</span></span>|  
|<span data-ttu-id="f0d34-127">EndMethod</span><span class="sxs-lookup"><span data-stu-id="f0d34-127">EndMethod</span></span>|<span data-ttu-id="f0d34-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="f0d34-128">xs:string</span></span>|<span data-ttu-id="f0d34-129">End yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="f0d34-129">The name of the end method.</span></span>|  
|<span data-ttu-id="f0d34-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f0d34-130">AppDomain</span></span>|<span data-ttu-id="f0d34-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="f0d34-131">xs:string</span></span>|<span data-ttu-id="f0d34-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f0d34-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
