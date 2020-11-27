---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 9249bdd0fe996ee7c1b04783ac8fef2c48063cc0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294163"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="ca6c5-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="ca6c5-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="ca6c5-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ca6c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca6c5-104">ID</span><span class="sxs-lookup"><span data-stu-id="ca6c5-104">ID</span></span>|<span data-ttu-id="ca6c5-105">1132</span><span class="sxs-lookup"><span data-stu-id="ca6c5-105">1132</span></span>|  
|<span data-ttu-id="ca6c5-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ca6c5-106">Keywords</span></span>|<span data-ttu-id="ca6c5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ca6c5-107">WFRuntime</span></span>|  
|<span data-ttu-id="ca6c5-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ca6c5-108">Level</span></span>|<span data-ttu-id="ca6c5-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="ca6c5-109">Information</span></span>|  
|<span data-ttu-id="ca6c5-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ca6c5-110">Channel</span></span>|<span data-ttu-id="ca6c5-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="ca6c5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ca6c5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca6c5-112">Description</span></span>  

 <span data-ttu-id="ca6c5-113">CacheMetadata adımı sırasında InvokeMethod etkinliği, yöntemi çağrılırken zaman uyumsuz deseninin kullanılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca6c5-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ca6c5-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ca6c5-114">Message</span></span>  

 <span data-ttu-id="ca6c5-115">InvokeMethod ' %1 '-yöntem zaman uyumsuz model kullanmıyor.</span><span class="sxs-lookup"><span data-stu-id="ca6c5-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ca6c5-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ca6c5-116">Details</span></span>  
  
|<span data-ttu-id="ca6c5-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ca6c5-117">Data Item Name</span></span>|<span data-ttu-id="ca6c5-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ca6c5-118">Data Item Type</span></span>|<span data-ttu-id="ca6c5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca6c5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ca6c5-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="ca6c5-120">InvokeMethod</span></span>|<span data-ttu-id="ca6c5-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="ca6c5-121">xs:string</span></span>|<span data-ttu-id="ca6c5-122">InvokeMethod etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ca6c5-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="ca6c5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ca6c5-123">AppDomain</span></span>|<span data-ttu-id="ca6c5-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="ca6c5-124">xs:string</span></span>|<span data-ttu-id="ca6c5-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ca6c5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
