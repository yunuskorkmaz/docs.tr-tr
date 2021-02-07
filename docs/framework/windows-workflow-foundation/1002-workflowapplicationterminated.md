---
description: 'Hakkında daha fazla bilgi edinin: 1002-Workflowapplicationsonlandırılmış'
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 8ceef41515231833767fc7e2095ab3850bf80e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755635"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="91dad-103">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="91dad-103">1002 - WorkflowApplicationTerminated</span></span>

## <a name="properties"></a><span data-ttu-id="91dad-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="91dad-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91dad-105">ID</span><span class="sxs-lookup"><span data-stu-id="91dad-105">ID</span></span>|<span data-ttu-id="91dad-106">1002</span><span class="sxs-lookup"><span data-stu-id="91dad-106">1002</span></span>|  
|<span data-ttu-id="91dad-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="91dad-107">Keywords</span></span>|<span data-ttu-id="91dad-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="91dad-108">WFRuntime</span></span>|  
|<span data-ttu-id="91dad-109">Level</span><span class="sxs-lookup"><span data-stu-id="91dad-109">Level</span></span>|<span data-ttu-id="91dad-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="91dad-110">Information</span></span>|  
|<span data-ttu-id="91dad-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="91dad-111">Channel</span></span>|<span data-ttu-id="91dad-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="91dad-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91dad-113">Description</span><span class="sxs-lookup"><span data-stu-id="91dad-113">Description</span></span>  

 <span data-ttu-id="91dad-114">Bir iş akışı uygulamasının hatalı durumda bir özel durumla sonlandırdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91dad-114">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91dad-115">İleti</span><span class="sxs-lookup"><span data-stu-id="91dad-115">Message</span></span>  

 <span data-ttu-id="91dad-116">WorkflowApplication kimliği: ' %1 ' sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="91dad-116">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="91dad-117">Hatalı durumda bir özel durumla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="91dad-117">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91dad-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="91dad-118">Details</span></span>  
  
|<span data-ttu-id="91dad-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="91dad-119">Data Item Name</span></span>|<span data-ttu-id="91dad-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="91dad-120">Data Item Type</span></span>|<span data-ttu-id="91dad-121">Description</span><span class="sxs-lookup"><span data-stu-id="91dad-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91dad-122">Workflowapplicationıd</span><span class="sxs-lookup"><span data-stu-id="91dad-122">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="91dad-123">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="91dad-123">The workflow application id</span></span>|  
|<span data-ttu-id="91dad-124">Özel durum</span><span class="sxs-lookup"><span data-stu-id="91dad-124">Exception</span></span>|`xs:string`|<span data-ttu-id="91dad-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="91dad-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="91dad-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="91dad-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="91dad-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="91dad-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
