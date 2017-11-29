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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 934c2947e86b429e9b990c273f22c0511f209a53
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="452cf-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="452cf-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="452cf-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="452cf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="452cf-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="452cf-104">ID</span></span>|<span data-ttu-id="452cf-105">1125</span><span class="sxs-lookup"><span data-stu-id="452cf-105">1125</span></span>|  
|<span data-ttu-id="452cf-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="452cf-106">Keywords</span></span>|<span data-ttu-id="452cf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="452cf-107">WFRuntime</span></span>|  
|<span data-ttu-id="452cf-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="452cf-108">Level</span></span>|<span data-ttu-id="452cf-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="452cf-109">Information</span></span>|  
|<span data-ttu-id="452cf-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="452cf-110">Channel</span></span>|<span data-ttu-id="452cf-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="452cf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="452cf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="452cf-112">Description</span></span>  
 <span data-ttu-id="452cf-113">CacheMetadata adımı sırasında InvokeMethod etkinlik çağrılacak yöntemi statik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="452cf-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="452cf-114">İleti</span><span class="sxs-lookup"><span data-stu-id="452cf-114">Message</span></span>  
 <span data-ttu-id="452cf-115">'%1' - InvokeMethod yöntemi statik değil.</span><span class="sxs-lookup"><span data-stu-id="452cf-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="452cf-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="452cf-116">Details</span></span>  
  
|<span data-ttu-id="452cf-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="452cf-117">Data Item Name</span></span>|<span data-ttu-id="452cf-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="452cf-118">Data Item Type</span></span>|<span data-ttu-id="452cf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="452cf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="452cf-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="452cf-120">InvokeMethod</span></span>|<span data-ttu-id="452cf-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="452cf-121">xs:string</span></span>|<span data-ttu-id="452cf-122">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="452cf-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="452cf-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="452cf-123">AppDomain</span></span>|<span data-ttu-id="452cf-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="452cf-124">xs:string</span></span>|<span data-ttu-id="452cf-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="452cf-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
