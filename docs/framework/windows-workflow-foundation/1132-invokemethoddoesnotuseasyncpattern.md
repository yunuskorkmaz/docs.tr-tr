---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 300e843529bfc76df4193b46cd713ce0bd9cdbfd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="55322-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="55322-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="55322-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="55322-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55322-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="55322-104">ID</span></span>|<span data-ttu-id="55322-105">1132</span><span class="sxs-lookup"><span data-stu-id="55322-105">1132</span></span>|  
|<span data-ttu-id="55322-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="55322-106">Keywords</span></span>|<span data-ttu-id="55322-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="55322-107">WFRuntime</span></span>|  
|<span data-ttu-id="55322-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="55322-108">Level</span></span>|<span data-ttu-id="55322-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="55322-109">Information</span></span>|  
|<span data-ttu-id="55322-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="55322-110">Channel</span></span>|<span data-ttu-id="55322-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="55322-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="55322-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55322-112">Description</span></span>  
 <span data-ttu-id="55322-113">CacheMetadata adımı sırasında bu zaman uyumsuz desen yöntemi çağrılırken kullanmadığından emin InvokeMethod etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="55322-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="55322-114">İleti</span><span class="sxs-lookup"><span data-stu-id="55322-114">Message</span></span>  
 <span data-ttu-id="55322-115">'%1' - InvokeMethod yöntemini zaman uyumsuz desen kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="55322-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="55322-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="55322-116">Details</span></span>  
  
|<span data-ttu-id="55322-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="55322-117">Data Item Name</span></span>|<span data-ttu-id="55322-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="55322-118">Data Item Type</span></span>|<span data-ttu-id="55322-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55322-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="55322-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="55322-120">InvokeMethod</span></span>|<span data-ttu-id="55322-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="55322-121">xs:string</span></span>|<span data-ttu-id="55322-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="55322-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="55322-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="55322-123">AppDomain</span></span>|<span data-ttu-id="55322-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="55322-124">xs:string</span></span>|<span data-ttu-id="55322-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="55322-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
