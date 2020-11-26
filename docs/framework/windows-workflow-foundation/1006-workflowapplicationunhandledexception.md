---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 4bb76a93ec7a07a735def1f1d5dc79decb7792ad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239841"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="829ab-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="829ab-102">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="829ab-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="829ab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="829ab-104">ID</span><span class="sxs-lookup"><span data-stu-id="829ab-104">ID</span></span>|<span data-ttu-id="829ab-105">1006</span><span class="sxs-lookup"><span data-stu-id="829ab-105">1006</span></span>|  
|<span data-ttu-id="829ab-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="829ab-106">Keywords</span></span>|<span data-ttu-id="829ab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="829ab-107">WFRuntime</span></span>|  
|<span data-ttu-id="829ab-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="829ab-108">Level</span></span>|<span data-ttu-id="829ab-109">Hata</span><span class="sxs-lookup"><span data-stu-id="829ab-109">Error</span></span>|  
|<span data-ttu-id="829ab-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="829ab-110">Channel</span></span>|<span data-ttu-id="829ab-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="829ab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="829ab-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="829ab-112">Description</span></span>  

 <span data-ttu-id="829ab-113">Bir iş akışı uygulamasının işlenmemiş bir özel durumla karşılaşdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="829ab-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="829ab-114">İleti</span><span class="sxs-lookup"><span data-stu-id="829ab-114">Message</span></span>  

 <span data-ttu-id="829ab-115">WorkflowInstance kimliği: ' %1 ' işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="829ab-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="829ab-116">DisplayName: ' %3 ' olan ' %2 ' etkinliğinden kaynaklanan özel durum.</span><span class="sxs-lookup"><span data-stu-id="829ab-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="829ab-117">Şu işlem gerçekleştirilecek: %4.</span><span class="sxs-lookup"><span data-stu-id="829ab-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="829ab-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="829ab-118">Details</span></span>  
  
|<span data-ttu-id="829ab-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="829ab-119">Data Item Name</span></span>|<span data-ttu-id="829ab-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="829ab-120">Data Item Type</span></span>|<span data-ttu-id="829ab-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="829ab-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="829ab-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="829ab-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="829ab-123">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="829ab-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="829ab-124">Özel durum</span><span class="sxs-lookup"><span data-stu-id="829ab-124">Exception</span></span>|`xs:string`|<span data-ttu-id="829ab-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="829ab-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="829ab-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="829ab-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="829ab-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="829ab-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
