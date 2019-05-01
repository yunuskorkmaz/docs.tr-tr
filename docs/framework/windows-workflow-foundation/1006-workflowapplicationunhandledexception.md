---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924715"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="300de-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="300de-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="300de-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="300de-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="300de-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="300de-104">ID</span></span>|<span data-ttu-id="300de-105">1006</span><span class="sxs-lookup"><span data-stu-id="300de-105">1006</span></span>|  
|<span data-ttu-id="300de-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="300de-106">Keywords</span></span>|<span data-ttu-id="300de-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="300de-107">WFRuntime</span></span>|  
|<span data-ttu-id="300de-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="300de-108">Level</span></span>|<span data-ttu-id="300de-109">Hata</span><span class="sxs-lookup"><span data-stu-id="300de-109">Error</span></span>|  
|<span data-ttu-id="300de-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="300de-110">Channel</span></span>|<span data-ttu-id="300de-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="300de-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="300de-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="300de-112">Description</span></span>  
 <span data-ttu-id="300de-113">Bir iş akışı uygulaması işlenmeyen bir özel durumla karşılaştı gösterir.</span><span class="sxs-lookup"><span data-stu-id="300de-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="300de-114">İleti</span><span class="sxs-lookup"><span data-stu-id="300de-114">Message</span></span>  
 <span data-ttu-id="300de-115">WorkflowInstance ID: '%1' işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="300de-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="300de-116">Özel durum '%2', DisplayName etkinliğinden kaynaklanan: '%3'.</span><span class="sxs-lookup"><span data-stu-id="300de-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="300de-117">Aşağıdaki işlem yapılmayacak: %4.</span><span class="sxs-lookup"><span data-stu-id="300de-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="300de-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="300de-118">Details</span></span>  
  
|<span data-ttu-id="300de-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="300de-119">Data Item Name</span></span>|<span data-ttu-id="300de-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="300de-120">Data Item Type</span></span>|<span data-ttu-id="300de-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="300de-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="300de-122">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="300de-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="300de-123">İş akışı örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="300de-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="300de-124">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="300de-124">Exception</span></span>|`xs:string`|<span data-ttu-id="300de-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="300de-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="300de-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="300de-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="300de-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="300de-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
