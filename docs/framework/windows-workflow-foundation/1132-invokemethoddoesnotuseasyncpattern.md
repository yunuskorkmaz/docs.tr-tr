---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511882"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="c0165-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="c0165-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="c0165-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c0165-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0165-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c0165-104">ID</span></span>|<span data-ttu-id="c0165-105">1132</span><span class="sxs-lookup"><span data-stu-id="c0165-105">1132</span></span>|  
|<span data-ttu-id="c0165-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c0165-106">Keywords</span></span>|<span data-ttu-id="c0165-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c0165-107">WFRuntime</span></span>|  
|<span data-ttu-id="c0165-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c0165-108">Level</span></span>|<span data-ttu-id="c0165-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="c0165-109">Information</span></span>|  
|<span data-ttu-id="c0165-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c0165-110">Channel</span></span>|<span data-ttu-id="c0165-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c0165-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c0165-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0165-112">Description</span></span>  
 <span data-ttu-id="c0165-113">CacheMetadata adımı sırasında bu zaman uyumsuz desen yöntemi çağrılırken kullanmadığından emin InvokeMethod etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0165-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c0165-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c0165-114">Message</span></span>  
 <span data-ttu-id="c0165-115">'%1' - InvokeMethod yöntemini zaman uyumsuz desen kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="c0165-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c0165-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c0165-116">Details</span></span>  
  
|<span data-ttu-id="c0165-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c0165-117">Data Item Name</span></span>|<span data-ttu-id="c0165-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c0165-118">Data Item Type</span></span>|<span data-ttu-id="c0165-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0165-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c0165-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="c0165-120">InvokeMethod</span></span>|<span data-ttu-id="c0165-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="c0165-121">xs:string</span></span>|<span data-ttu-id="c0165-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c0165-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="c0165-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c0165-123">AppDomain</span></span>|<span data-ttu-id="c0165-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="c0165-124">xs:string</span></span>|<span data-ttu-id="c0165-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c0165-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
