---
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 0405b4e1207db5c056fbd478b98c408258daf0c3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294215"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="910ff-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="910ff-102">1125 - InvokeMethodIsNotStatic</span></span>

## <a name="properties"></a><span data-ttu-id="910ff-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="910ff-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="910ff-104">ID</span><span class="sxs-lookup"><span data-stu-id="910ff-104">ID</span></span>|<span data-ttu-id="910ff-105">1125</span><span class="sxs-lookup"><span data-stu-id="910ff-105">1125</span></span>|  
|<span data-ttu-id="910ff-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="910ff-106">Keywords</span></span>|<span data-ttu-id="910ff-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="910ff-107">WFRuntime</span></span>|  
|<span data-ttu-id="910ff-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="910ff-108">Level</span></span>|<span data-ttu-id="910ff-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="910ff-109">Information</span></span>|  
|<span data-ttu-id="910ff-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="910ff-110">Channel</span></span>|<span data-ttu-id="910ff-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="910ff-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="910ff-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="910ff-112">Description</span></span>  

 <span data-ttu-id="910ff-113">CacheMetadata adımı sırasında InvokeMethod etkinliği çağrılacak yöntemin statik olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="910ff-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="910ff-114">İleti</span><span class="sxs-lookup"><span data-stu-id="910ff-114">Message</span></span>  

 <span data-ttu-id="910ff-115">InvokeMethod ' %1 '-metot static değil.</span><span class="sxs-lookup"><span data-stu-id="910ff-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="910ff-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="910ff-116">Details</span></span>  
  
|<span data-ttu-id="910ff-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="910ff-117">Data Item Name</span></span>|<span data-ttu-id="910ff-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="910ff-118">Data Item Type</span></span>|<span data-ttu-id="910ff-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="910ff-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="910ff-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="910ff-120">InvokeMethod</span></span>|<span data-ttu-id="910ff-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="910ff-121">xs:string</span></span>|<span data-ttu-id="910ff-122">InvokeMethod etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="910ff-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="910ff-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="910ff-123">AppDomain</span></span>|<span data-ttu-id="910ff-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="910ff-124">xs:string</span></span>|<span data-ttu-id="910ff-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="910ff-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
