---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509801"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="d2a15-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="d2a15-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="d2a15-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d2a15-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2a15-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="d2a15-104">ID</span></span>|<span data-ttu-id="d2a15-105">1001</span><span class="sxs-lookup"><span data-stu-id="d2a15-105">1001</span></span>|  
|<span data-ttu-id="d2a15-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="d2a15-106">Keywords</span></span>|<span data-ttu-id="d2a15-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d2a15-107">WFRuntime</span></span>|  
|<span data-ttu-id="d2a15-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d2a15-108">Level</span></span>|<span data-ttu-id="d2a15-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="d2a15-109">Information</span></span>|  
|<span data-ttu-id="d2a15-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d2a15-110">Channel</span></span>|<span data-ttu-id="d2a15-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d2a15-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d2a15-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2a15-112">Description</span></span>  
 <span data-ttu-id="d2a15-113">Bir iş akışı uygulaması kapalı durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2a15-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d2a15-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d2a15-114">Message</span></span>  
 <span data-ttu-id="d2a15-115">İş akışı örneği kimliği: '%1' kapalı durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d2a15-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d2a15-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d2a15-116">Details</span></span>  
  
|<span data-ttu-id="d2a15-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d2a15-117">Data Item Name</span></span>|<span data-ttu-id="d2a15-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d2a15-118">Data Item Type</span></span>|<span data-ttu-id="d2a15-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2a15-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d2a15-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="d2a15-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="d2a15-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="d2a15-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="d2a15-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d2a15-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d2a15-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d2a15-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
