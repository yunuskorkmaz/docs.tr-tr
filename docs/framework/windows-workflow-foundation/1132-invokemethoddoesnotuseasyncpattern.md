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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 321d8c6185c8d24b7a3b6e255e235c36c119ff21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="abd96-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="abd96-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="abd96-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="abd96-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="abd96-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="abd96-104">ID</span></span>|<span data-ttu-id="abd96-105">1132</span><span class="sxs-lookup"><span data-stu-id="abd96-105">1132</span></span>|  
|<span data-ttu-id="abd96-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="abd96-106">Keywords</span></span>|<span data-ttu-id="abd96-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="abd96-107">WFRuntime</span></span>|  
|<span data-ttu-id="abd96-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="abd96-108">Level</span></span>|<span data-ttu-id="abd96-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="abd96-109">Information</span></span>|  
|<span data-ttu-id="abd96-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="abd96-110">Channel</span></span>|<span data-ttu-id="abd96-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="abd96-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="abd96-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abd96-112">Description</span></span>  
 <span data-ttu-id="abd96-113">CacheMetadata adımı sırasında bu zaman uyumsuz desen yöntemi çağrılırken kullanmadığından emin InvokeMethod etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="abd96-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="abd96-114">İleti</span><span class="sxs-lookup"><span data-stu-id="abd96-114">Message</span></span>  
 <span data-ttu-id="abd96-115">'%1' - InvokeMethod yöntemini zaman uyumsuz desen kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="abd96-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="abd96-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="abd96-116">Details</span></span>  
  
|<span data-ttu-id="abd96-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="abd96-117">Data Item Name</span></span>|<span data-ttu-id="abd96-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="abd96-118">Data Item Type</span></span>|<span data-ttu-id="abd96-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abd96-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="abd96-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="abd96-120">InvokeMethod</span></span>|<span data-ttu-id="abd96-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="abd96-121">xs:string</span></span>|<span data-ttu-id="abd96-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="abd96-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="abd96-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="abd96-123">AppDomain</span></span>|<span data-ttu-id="abd96-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="abd96-124">xs:string</span></span>|<span data-ttu-id="abd96-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="abd96-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
