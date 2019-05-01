---
title: 1124 - InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 49a9dec73392681fd4150c611f78399a1e15dd48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924065"
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="2bad3-102">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="2bad3-102">1124 - InvokeMethodIsStatic</span></span>
## <a name="properties"></a><span data-ttu-id="2bad3-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2bad3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2bad3-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2bad3-104">ID</span></span>|<span data-ttu-id="2bad3-105">1124</span><span class="sxs-lookup"><span data-stu-id="2bad3-105">1124</span></span>|  
|<span data-ttu-id="2bad3-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="2bad3-106">Keywords</span></span>|<span data-ttu-id="2bad3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2bad3-107">WFRuntime</span></span>|  
|<span data-ttu-id="2bad3-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2bad3-108">Level</span></span>|<span data-ttu-id="2bad3-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="2bad3-109">Information</span></span>|  
|<span data-ttu-id="2bad3-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2bad3-110">Channel</span></span>|<span data-ttu-id="2bad3-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2bad3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2bad3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bad3-112">Description</span></span>  
 <span data-ttu-id="2bad3-113">CacheMetadata adımı sırasında çağrılacak yöntem statik ise InvokeMethod etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="2bad3-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2bad3-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2bad3-114">Message</span></span>  
 <span data-ttu-id="2bad3-115">InvokeMethod '%1' - yöntemi statik bir değer.</span><span class="sxs-lookup"><span data-stu-id="2bad3-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2bad3-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2bad3-116">Details</span></span>  
  
|<span data-ttu-id="2bad3-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2bad3-117">Data Item Name</span></span>|<span data-ttu-id="2bad3-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2bad3-118">Data Item Type</span></span>|<span data-ttu-id="2bad3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bad3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2bad3-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="2bad3-120">InvokeMethod</span></span>|<span data-ttu-id="2bad3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2bad3-121">xs:string</span></span>|<span data-ttu-id="2bad3-122">InvokeMethod etkinliği görünen adı.</span><span class="sxs-lookup"><span data-stu-id="2bad3-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="2bad3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2bad3-123">AppDomain</span></span>|<span data-ttu-id="2bad3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2bad3-124">xs:string</span></span>|<span data-ttu-id="2bad3-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2bad3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
