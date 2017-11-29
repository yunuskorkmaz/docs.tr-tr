---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a62a8448319e7b07a3ea302f00f2fa269bf654ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="02812-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="02812-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="02812-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="02812-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02812-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="02812-104">ID</span></span>|<span data-ttu-id="02812-105">1001</span><span class="sxs-lookup"><span data-stu-id="02812-105">1001</span></span>|  
|<span data-ttu-id="02812-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="02812-106">Keywords</span></span>|<span data-ttu-id="02812-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="02812-107">WFRuntime</span></span>|  
|<span data-ttu-id="02812-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="02812-108">Level</span></span>|<span data-ttu-id="02812-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="02812-109">Information</span></span>|  
|<span data-ttu-id="02812-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="02812-110">Channel</span></span>|<span data-ttu-id="02812-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="02812-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="02812-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02812-112">Description</span></span>  
 <span data-ttu-id="02812-113">Bir iş akışı uygulaması kapalı durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02812-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="02812-114">İleti</span><span class="sxs-lookup"><span data-stu-id="02812-114">Message</span></span>  
 <span data-ttu-id="02812-115">İş akışı örneği kimliği: '%1' kapalı durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="02812-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="02812-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="02812-116">Details</span></span>  
  
|<span data-ttu-id="02812-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="02812-117">Data Item Name</span></span>|<span data-ttu-id="02812-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="02812-118">Data Item Type</span></span>|<span data-ttu-id="02812-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02812-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="02812-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="02812-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="02812-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="02812-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="02812-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="02812-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="02812-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="02812-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
