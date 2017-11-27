---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42d22a7187adc712c0f236111cecac89dd59e2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="09132-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="09132-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="09132-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="09132-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09132-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="09132-104">ID</span></span>|<span data-ttu-id="09132-105">1005</span><span class="sxs-lookup"><span data-stu-id="09132-105">1005</span></span>|  
|<span data-ttu-id="09132-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="09132-106">Keywords</span></span>|<span data-ttu-id="09132-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="09132-107">WFRuntime</span></span>|  
|<span data-ttu-id="09132-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="09132-108">Level</span></span>|<span data-ttu-id="09132-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="09132-109">Information</span></span>|  
|<span data-ttu-id="09132-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="09132-110">Channel</span></span>|<span data-ttu-id="09132-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="09132-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="09132-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09132-112">Description</span></span>  
 <span data-ttu-id="09132-113">Bir iş akışı uygulaması idled gösterir.</span><span class="sxs-lookup"><span data-stu-id="09132-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="09132-114">İleti</span><span class="sxs-lookup"><span data-stu-id="09132-114">Message</span></span>  
 <span data-ttu-id="09132-115">WorkflowApplication kimliği: '%1' boşta geçti.</span><span class="sxs-lookup"><span data-stu-id="09132-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="09132-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="09132-116">Details</span></span>  
  
|<span data-ttu-id="09132-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="09132-117">Data Item Name</span></span>|<span data-ttu-id="09132-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="09132-118">Data Item Type</span></span>|<span data-ttu-id="09132-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09132-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="09132-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="09132-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="09132-121">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="09132-121">The workflow application id</span></span>|  
|<span data-ttu-id="09132-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="09132-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="09132-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="09132-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
