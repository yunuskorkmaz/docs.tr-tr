---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b31bb8db8252474d20f7523e08cadf35bfcc84a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="f55ca-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="f55ca-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="f55ca-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f55ca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f55ca-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f55ca-104">ID</span></span>|<span data-ttu-id="f55ca-105">1125</span><span class="sxs-lookup"><span data-stu-id="f55ca-105">1125</span></span>|  
|<span data-ttu-id="f55ca-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f55ca-106">Keywords</span></span>|<span data-ttu-id="f55ca-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f55ca-107">WFRuntime</span></span>|  
|<span data-ttu-id="f55ca-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f55ca-108">Level</span></span>|<span data-ttu-id="f55ca-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f55ca-109">Information</span></span>|  
|<span data-ttu-id="f55ca-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f55ca-110">Channel</span></span>|<span data-ttu-id="f55ca-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f55ca-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f55ca-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f55ca-112">Description</span></span>  
 <span data-ttu-id="f55ca-113">CacheMetadata adımı sırasında InvokeMethod etkinlik çağrılacak yöntemi statik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f55ca-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f55ca-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f55ca-114">Message</span></span>  
 <span data-ttu-id="f55ca-115">'%1' - InvokeMethod yöntemi statik değil.</span><span class="sxs-lookup"><span data-stu-id="f55ca-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f55ca-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f55ca-116">Details</span></span>  
  
|<span data-ttu-id="f55ca-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f55ca-117">Data Item Name</span></span>|<span data-ttu-id="f55ca-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f55ca-118">Data Item Type</span></span>|<span data-ttu-id="f55ca-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f55ca-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f55ca-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f55ca-120">InvokeMethod</span></span>|<span data-ttu-id="f55ca-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="f55ca-121">xs:string</span></span>|<span data-ttu-id="f55ca-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f55ca-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f55ca-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f55ca-123">AppDomain</span></span>|<span data-ttu-id="f55ca-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f55ca-124">xs:string</span></span>|<span data-ttu-id="f55ca-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f55ca-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
