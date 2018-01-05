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
ms.workload: dotnet
ms.openlocfilehash: 5dc752a5c9d5bebe39a4d4be2c3642333aa041de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="f016b-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="f016b-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="f016b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f016b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f016b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f016b-104">ID</span></span>|<span data-ttu-id="f016b-105">1126</span><span class="sxs-lookup"><span data-stu-id="f016b-105">1126</span></span>|  
|<span data-ttu-id="f016b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f016b-106">Keywords</span></span>|<span data-ttu-id="f016b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f016b-107">WFRuntime</span></span>|  
|<span data-ttu-id="f016b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f016b-108">Level</span></span>|<span data-ttu-id="f016b-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f016b-109">Information</span></span>|  
|<span data-ttu-id="f016b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f016b-110">Channel</span></span>|<span data-ttu-id="f016b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f016b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f016b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f016b-112">Description</span></span>  
 <span data-ttu-id="f016b-113">Tarafından InvokeMethod etkinlik tarafından çağrılan yöntemi bir özel durum oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f016b-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f016b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f016b-114">Message</span></span>  
 <span data-ttu-id="f016b-115">Etkinlik tarafından '%1' adlı yöntemi özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="f016b-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="f016b-116">%2</span><span class="sxs-lookup"><span data-stu-id="f016b-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="f016b-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f016b-117">Details</span></span>  
  
|<span data-ttu-id="f016b-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f016b-118">Data Item Name</span></span>|<span data-ttu-id="f016b-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f016b-119">Data Item Type</span></span>|<span data-ttu-id="f016b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f016b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f016b-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f016b-121">InvokeMethod</span></span>|<span data-ttu-id="f016b-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="f016b-122">xs:string</span></span>|<span data-ttu-id="f016b-123">InvokeMethod etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f016b-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f016b-124">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="f016b-124">Exception</span></span>|<span data-ttu-id="f016b-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="f016b-125">xs:string</span></span>|<span data-ttu-id="f016b-126">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="f016b-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="f016b-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f016b-127">AppDomain</span></span>|<span data-ttu-id="f016b-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="f016b-128">xs:string</span></span>|<span data-ttu-id="f016b-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f016b-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
