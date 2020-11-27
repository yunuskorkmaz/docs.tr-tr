---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 2192b63b8a08657b69f6e3984f898bd6baddbc5f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294189"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="1d861-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="1d861-102">1131 - InvokeMethodUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="1d861-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1d861-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d861-104">ID</span><span class="sxs-lookup"><span data-stu-id="1d861-104">ID</span></span>|<span data-ttu-id="1d861-105">1131</span><span class="sxs-lookup"><span data-stu-id="1d861-105">1131</span></span>|  
|<span data-ttu-id="1d861-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="1d861-106">Keywords</span></span>|<span data-ttu-id="1d861-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1d861-107">WFRuntime</span></span>|  
|<span data-ttu-id="1d861-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1d861-108">Level</span></span>|<span data-ttu-id="1d861-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="1d861-109">Information</span></span>|  
|<span data-ttu-id="1d861-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1d861-110">Channel</span></span>|<span data-ttu-id="1d861-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="1d861-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1d861-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d861-112">Description</span></span>  

 <span data-ttu-id="1d861-113">CacheMetadata adımı sırasında InvokeMethod etkinliği yöntemi çağrılırken zaman uyumsuz bir model kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d861-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1d861-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1d861-114">Message</span></span>  

 <span data-ttu-id="1d861-115">InvokeMethod ' %1 '-Yöntem ' %2 ' ve ' %3 ' zaman uyumsuz modelini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="1d861-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1d861-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1d861-116">Details</span></span>  
  
|<span data-ttu-id="1d861-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1d861-117">Data Item Name</span></span>|<span data-ttu-id="1d861-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1d861-118">Data Item Type</span></span>|<span data-ttu-id="1d861-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d861-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1d861-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="1d861-120">InvokeMethod</span></span>|<span data-ttu-id="1d861-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d861-121">xs:string</span></span>|<span data-ttu-id="1d861-122">InvokeMethod etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="1d861-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="1d861-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="1d861-123">BeginMethod</span></span>|<span data-ttu-id="1d861-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d861-124">xs:string</span></span>|<span data-ttu-id="1d861-125">Begin yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="1d861-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="1d861-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="1d861-126">EndMethod</span></span>|<span data-ttu-id="1d861-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d861-127">xs:string</span></span>|<span data-ttu-id="1d861-128">End yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="1d861-128">The name of the end method.</span></span>|  
|<span data-ttu-id="1d861-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1d861-129">AppDomain</span></span>|<span data-ttu-id="1d861-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d861-130">xs:string</span></span>|<span data-ttu-id="1d861-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1d861-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
