---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b11c2f167ce7afce992cddb2f32f840212d4ac8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="e6604-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="e6604-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="e6604-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e6604-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e6604-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e6604-104">ID</span></span>|<span data-ttu-id="e6604-105">1126</span><span class="sxs-lookup"><span data-stu-id="e6604-105">1126</span></span>|  
|<span data-ttu-id="e6604-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e6604-106">Keywords</span></span>|<span data-ttu-id="e6604-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e6604-107">WFRuntime</span></span>|  
|<span data-ttu-id="e6604-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e6604-108">Level</span></span>|<span data-ttu-id="e6604-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="e6604-109">Information</span></span>|  
|<span data-ttu-id="e6604-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e6604-110">Channel</span></span>|<span data-ttu-id="e6604-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e6604-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e6604-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6604-112">Description</span></span>  
 <span data-ttu-id="e6604-113">Tarafından InvokeMethod etkinlik tarafından çağrılan yöntemi bir özel durum oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6604-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e6604-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e6604-114">Message</span></span>  
 <span data-ttu-id="e6604-115">Etkinlik tarafından '%1' adlı yöntemi özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="e6604-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="e6604-116">%2</span><span class="sxs-lookup"><span data-stu-id="e6604-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="e6604-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e6604-117">Details</span></span>  
  
|<span data-ttu-id="e6604-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e6604-118">Data Item Name</span></span>|<span data-ttu-id="e6604-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e6604-119">Data Item Type</span></span>|<span data-ttu-id="e6604-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6604-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e6604-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e6604-121">InvokeMethod</span></span>|<span data-ttu-id="e6604-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="e6604-122">xs:string</span></span>|<span data-ttu-id="e6604-123">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e6604-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="e6604-124">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="e6604-124">Exception</span></span>|<span data-ttu-id="e6604-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="e6604-125">xs:string</span></span>|<span data-ttu-id="e6604-126">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e6604-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="e6604-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e6604-127">AppDomain</span></span>|<span data-ttu-id="e6604-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="e6604-128">xs:string</span></span>|<span data-ttu-id="e6604-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e6604-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
