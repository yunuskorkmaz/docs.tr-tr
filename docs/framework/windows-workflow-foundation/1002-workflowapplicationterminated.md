---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 93a6a400576df84faae3cd58940462255b0073c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="4e636-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="4e636-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="4e636-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4e636-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e636-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4e636-104">ID</span></span>|<span data-ttu-id="4e636-105">1002</span><span class="sxs-lookup"><span data-stu-id="4e636-105">1002</span></span>|  
|<span data-ttu-id="4e636-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4e636-106">Keywords</span></span>|<span data-ttu-id="4e636-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4e636-107">WFRuntime</span></span>|  
|<span data-ttu-id="4e636-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4e636-108">Level</span></span>|<span data-ttu-id="4e636-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="4e636-109">Information</span></span>|  
|<span data-ttu-id="4e636-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4e636-110">Channel</span></span>|<span data-ttu-id="4e636-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4e636-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4e636-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e636-112">Description</span></span>  
 <span data-ttu-id="4e636-113">Bir iş akışı uygulaması Faulted durumunda bir özel durum ile sona erdi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e636-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4e636-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4e636-114">Message</span></span>  
 <span data-ttu-id="4e636-115">WorkflowApplication kimliği: '%1' sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="4e636-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="4e636-116">Faulted durumunda bir özel durum ile tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4e636-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4e636-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4e636-117">Details</span></span>  
  
|<span data-ttu-id="4e636-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4e636-118">Data Item Name</span></span>|<span data-ttu-id="4e636-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4e636-119">Data Item Type</span></span>|<span data-ttu-id="4e636-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e636-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4e636-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="4e636-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="4e636-122">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="4e636-122">The workflow application id</span></span>|  
|<span data-ttu-id="4e636-123">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="4e636-123">Exception</span></span>|`xs:string`|<span data-ttu-id="4e636-124">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="4e636-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="4e636-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4e636-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4e636-126">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4e636-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
