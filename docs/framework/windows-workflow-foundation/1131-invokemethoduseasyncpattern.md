---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009961"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="4b150-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="4b150-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="4b150-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4b150-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b150-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4b150-104">ID</span></span>|<span data-ttu-id="4b150-105">1131</span><span class="sxs-lookup"><span data-stu-id="4b150-105">1131</span></span>|  
|<span data-ttu-id="4b150-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4b150-106">Keywords</span></span>|<span data-ttu-id="4b150-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4b150-107">WFRuntime</span></span>|  
|<span data-ttu-id="4b150-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4b150-108">Level</span></span>|<span data-ttu-id="4b150-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="4b150-109">Information</span></span>|  
|<span data-ttu-id="4b150-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4b150-110">Channel</span></span>|<span data-ttu-id="4b150-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4b150-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4b150-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b150-112">Description</span></span>  
 <span data-ttu-id="4b150-113">CacheMetadata adımı sırasında InvokeMethod etkinliği, zaman uyumsuz desen yöntemi çağrılırken kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b150-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4b150-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4b150-114">Message</span></span>  
 <span data-ttu-id="4b150-115">InvokeMethod '%1' - '%2' ve '%3', zaman uyumsuz desen yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b150-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4b150-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4b150-116">Details</span></span>  
  
|<span data-ttu-id="4b150-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4b150-117">Data Item Name</span></span>|<span data-ttu-id="4b150-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4b150-118">Data Item Type</span></span>|<span data-ttu-id="4b150-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b150-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4b150-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="4b150-120">InvokeMethod</span></span>|<span data-ttu-id="4b150-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b150-121">xs:string</span></span>|<span data-ttu-id="4b150-122">InvokeMethod etkinliği görünen adı.</span><span class="sxs-lookup"><span data-stu-id="4b150-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="4b150-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="4b150-123">BeginMethod</span></span>|<span data-ttu-id="4b150-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b150-124">xs:string</span></span>|<span data-ttu-id="4b150-125">Begin yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="4b150-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="4b150-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="4b150-126">EndMethod</span></span>|<span data-ttu-id="4b150-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b150-127">xs:string</span></span>|<span data-ttu-id="4b150-128">End yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="4b150-128">The name of the end method.</span></span>|  
|<span data-ttu-id="4b150-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4b150-129">AppDomain</span></span>|<span data-ttu-id="4b150-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b150-130">xs:string</span></span>|<span data-ttu-id="4b150-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4b150-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
