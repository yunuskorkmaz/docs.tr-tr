---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512673"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="17ca8-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="17ca8-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="17ca8-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="17ca8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17ca8-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="17ca8-104">ID</span></span>|<span data-ttu-id="17ca8-105">1131</span><span class="sxs-lookup"><span data-stu-id="17ca8-105">1131</span></span>|  
|<span data-ttu-id="17ca8-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="17ca8-106">Keywords</span></span>|<span data-ttu-id="17ca8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="17ca8-107">WFRuntime</span></span>|  
|<span data-ttu-id="17ca8-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="17ca8-108">Level</span></span>|<span data-ttu-id="17ca8-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="17ca8-109">Information</span></span>|  
|<span data-ttu-id="17ca8-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="17ca8-110">Channel</span></span>|<span data-ttu-id="17ca8-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="17ca8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17ca8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17ca8-112">Description</span></span>  
 <span data-ttu-id="17ca8-113">CacheMetadata adımı sırasında InvokeMethod etkinlik, zaman uyumsuz desen yöntemi çağrılırken kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="17ca8-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17ca8-114">İleti</span><span class="sxs-lookup"><span data-stu-id="17ca8-114">Message</span></span>  
 <span data-ttu-id="17ca8-115">InvokeMethod '%1' - '%2' ve '%3' zaman uyumsuz desen yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="17ca8-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17ca8-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="17ca8-116">Details</span></span>  
  
|<span data-ttu-id="17ca8-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="17ca8-117">Data Item Name</span></span>|<span data-ttu-id="17ca8-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="17ca8-118">Data Item Type</span></span>|<span data-ttu-id="17ca8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17ca8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17ca8-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="17ca8-120">InvokeMethod</span></span>|<span data-ttu-id="17ca8-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="17ca8-121">xs:string</span></span>|<span data-ttu-id="17ca8-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="17ca8-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="17ca8-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="17ca8-123">BeginMethod</span></span>|<span data-ttu-id="17ca8-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="17ca8-124">xs:string</span></span>|<span data-ttu-id="17ca8-125">Begin yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="17ca8-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="17ca8-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="17ca8-126">EndMethod</span></span>|<span data-ttu-id="17ca8-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="17ca8-127">xs:string</span></span>|<span data-ttu-id="17ca8-128">End yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="17ca8-128">The name of the end method.</span></span>|  
|<span data-ttu-id="17ca8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="17ca8-129">AppDomain</span></span>|<span data-ttu-id="17ca8-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="17ca8-130">xs:string</span></span>|<span data-ttu-id="17ca8-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="17ca8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
