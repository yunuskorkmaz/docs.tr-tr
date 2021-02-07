---
description: 'Hakkında daha fazla bilgi edinin: 1132-ınvokemethodlınotumevsimsyncmodel'
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 05bbd1f6047ab4c6451d71a4f6007f3112f9630f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667284"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="b1ef3-103">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="b1ef3-103">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="b1ef3-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b1ef3-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1ef3-105">ID</span><span class="sxs-lookup"><span data-stu-id="b1ef3-105">ID</span></span>|<span data-ttu-id="b1ef3-106">1132</span><span class="sxs-lookup"><span data-stu-id="b1ef3-106">1132</span></span>|  
|<span data-ttu-id="b1ef3-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b1ef3-107">Keywords</span></span>|<span data-ttu-id="b1ef3-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b1ef3-108">WFRuntime</span></span>|  
|<span data-ttu-id="b1ef3-109">Level</span><span class="sxs-lookup"><span data-stu-id="b1ef3-109">Level</span></span>|<span data-ttu-id="b1ef3-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="b1ef3-110">Information</span></span>|  
|<span data-ttu-id="b1ef3-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="b1ef3-111">Channel</span></span>|<span data-ttu-id="b1ef3-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="b1ef3-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b1ef3-113">Description</span><span class="sxs-lookup"><span data-stu-id="b1ef3-113">Description</span></span>  

 <span data-ttu-id="b1ef3-114">CacheMetadata adımı sırasında InvokeMethod etkinliği, yöntemi çağrılırken zaman uyumsuz deseninin kullanılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1ef3-114">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b1ef3-115">İleti</span><span class="sxs-lookup"><span data-stu-id="b1ef3-115">Message</span></span>  

 <span data-ttu-id="b1ef3-116">InvokeMethod ' %1 '-yöntem zaman uyumsuz model kullanmıyor.</span><span class="sxs-lookup"><span data-stu-id="b1ef3-116">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b1ef3-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b1ef3-117">Details</span></span>  
  
|<span data-ttu-id="b1ef3-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b1ef3-118">Data Item Name</span></span>|<span data-ttu-id="b1ef3-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b1ef3-119">Data Item Type</span></span>|<span data-ttu-id="b1ef3-120">Description</span><span class="sxs-lookup"><span data-stu-id="b1ef3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b1ef3-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="b1ef3-121">InvokeMethod</span></span>|<span data-ttu-id="b1ef3-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="b1ef3-122">xs:string</span></span>|<span data-ttu-id="b1ef3-123">InvokeMethod etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b1ef3-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="b1ef3-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b1ef3-124">AppDomain</span></span>|<span data-ttu-id="b1ef3-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="b1ef3-125">xs:string</span></span>|<span data-ttu-id="b1ef3-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b1ef3-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
