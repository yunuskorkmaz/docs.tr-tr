---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924221"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="e6c29-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="e6c29-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="e6c29-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e6c29-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e6c29-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e6c29-104">ID</span></span>|<span data-ttu-id="e6c29-105">1132</span><span class="sxs-lookup"><span data-stu-id="e6c29-105">1132</span></span>|  
|<span data-ttu-id="e6c29-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e6c29-106">Keywords</span></span>|<span data-ttu-id="e6c29-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e6c29-107">WFRuntime</span></span>|  
|<span data-ttu-id="e6c29-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e6c29-108">Level</span></span>|<span data-ttu-id="e6c29-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="e6c29-109">Information</span></span>|  
|<span data-ttu-id="e6c29-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e6c29-110">Channel</span></span>|<span data-ttu-id="e6c29-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e6c29-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e6c29-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6c29-112">Description</span></span>  
 <span data-ttu-id="e6c29-113">CacheMetadata adımı sırasında zaman uyumsuz desen yöntemi çağrılırken kullanmadığından emin InvokeMethod etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6c29-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e6c29-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e6c29-114">Message</span></span>  
 <span data-ttu-id="e6c29-115">'%1' - InvokeMethod yöntemi zaman uyumsuz desen kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="e6c29-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e6c29-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e6c29-116">Details</span></span>  
  
|<span data-ttu-id="e6c29-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e6c29-117">Data Item Name</span></span>|<span data-ttu-id="e6c29-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e6c29-118">Data Item Type</span></span>|<span data-ttu-id="e6c29-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6c29-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e6c29-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e6c29-120">InvokeMethod</span></span>|<span data-ttu-id="e6c29-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c29-121">xs:string</span></span>|<span data-ttu-id="e6c29-122">InvokeMethod etkinliği görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e6c29-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="e6c29-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e6c29-123">AppDomain</span></span>|<span data-ttu-id="e6c29-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c29-124">xs:string</span></span>|<span data-ttu-id="e6c29-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e6c29-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
