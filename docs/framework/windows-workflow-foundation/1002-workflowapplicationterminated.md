---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: e7c92dcc9ce472c50af6f0aa26c59f55d62fbb9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239945"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="b9e2a-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="b9e2a-102">1002 - WorkflowApplicationTerminated</span></span>

## <a name="properties"></a><span data-ttu-id="b9e2a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b9e2a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9e2a-104">ID</span><span class="sxs-lookup"><span data-stu-id="b9e2a-104">ID</span></span>|<span data-ttu-id="b9e2a-105">1002</span><span class="sxs-lookup"><span data-stu-id="b9e2a-105">1002</span></span>|  
|<span data-ttu-id="b9e2a-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b9e2a-106">Keywords</span></span>|<span data-ttu-id="b9e2a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b9e2a-107">WFRuntime</span></span>|  
|<span data-ttu-id="b9e2a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b9e2a-108">Level</span></span>|<span data-ttu-id="b9e2a-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="b9e2a-109">Information</span></span>|  
|<span data-ttu-id="b9e2a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b9e2a-110">Channel</span></span>|<span data-ttu-id="b9e2a-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="b9e2a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b9e2a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9e2a-112">Description</span></span>  

 <span data-ttu-id="b9e2a-113">Bir iş akışı uygulamasının hatalı durumda bir özel durumla sonlandırdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b9e2a-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b9e2a-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b9e2a-114">Message</span></span>  

 <span data-ttu-id="b9e2a-115">WorkflowApplication kimliği: ' %1 ' sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="b9e2a-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="b9e2a-116">Hatalı durumda bir özel durumla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b9e2a-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b9e2a-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b9e2a-117">Details</span></span>  
  
|<span data-ttu-id="b9e2a-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b9e2a-118">Data Item Name</span></span>|<span data-ttu-id="b9e2a-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b9e2a-119">Data Item Type</span></span>|<span data-ttu-id="b9e2a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9e2a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b9e2a-121">Workflowapplicationıd</span><span class="sxs-lookup"><span data-stu-id="b9e2a-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="b9e2a-122">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="b9e2a-122">The workflow application id</span></span>|  
|<span data-ttu-id="b9e2a-123">Özel durum</span><span class="sxs-lookup"><span data-stu-id="b9e2a-123">Exception</span></span>|`xs:string`|<span data-ttu-id="b9e2a-124">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b9e2a-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="b9e2a-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b9e2a-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b9e2a-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b9e2a-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
