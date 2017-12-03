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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1021d7d23b8e9c25684da567b769c24380a8a0a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="9b998-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="9b998-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="9b998-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9b998-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b998-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9b998-104">ID</span></span>|<span data-ttu-id="9b998-105">1126</span><span class="sxs-lookup"><span data-stu-id="9b998-105">1126</span></span>|  
|<span data-ttu-id="9b998-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9b998-106">Keywords</span></span>|<span data-ttu-id="9b998-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9b998-107">WFRuntime</span></span>|  
|<span data-ttu-id="9b998-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9b998-108">Level</span></span>|<span data-ttu-id="9b998-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9b998-109">Information</span></span>|  
|<span data-ttu-id="9b998-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9b998-110">Channel</span></span>|<span data-ttu-id="9b998-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9b998-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9b998-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b998-112">Description</span></span>  
 <span data-ttu-id="9b998-113">Tarafından InvokeMethod etkinlik tarafından çağrılan yöntemi bir özel durum oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b998-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9b998-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9b998-114">Message</span></span>  
 <span data-ttu-id="9b998-115">Etkinlik tarafından '%1' adlı yöntemi özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="9b998-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="9b998-116">%2</span><span class="sxs-lookup"><span data-stu-id="9b998-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="9b998-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9b998-117">Details</span></span>  
  
|<span data-ttu-id="9b998-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9b998-118">Data Item Name</span></span>|<span data-ttu-id="9b998-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9b998-119">Data Item Type</span></span>|<span data-ttu-id="9b998-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b998-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9b998-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9b998-121">InvokeMethod</span></span>|<span data-ttu-id="9b998-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="9b998-122">xs:string</span></span>|<span data-ttu-id="9b998-123">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9b998-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9b998-124">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="9b998-124">Exception</span></span>|<span data-ttu-id="9b998-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="9b998-125">xs:string</span></span>|<span data-ttu-id="9b998-126">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9b998-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="9b998-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9b998-127">AppDomain</span></span>|<span data-ttu-id="9b998-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="9b998-128">xs:string</span></span>|<span data-ttu-id="9b998-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9b998-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
