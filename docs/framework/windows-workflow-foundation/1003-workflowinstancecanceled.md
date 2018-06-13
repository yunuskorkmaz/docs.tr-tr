---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509775"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="d531e-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="d531e-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="d531e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d531e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d531e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="d531e-104">ID</span></span>|<span data-ttu-id="d531e-105">1003</span><span class="sxs-lookup"><span data-stu-id="d531e-105">1003</span></span>|  
|<span data-ttu-id="d531e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="d531e-106">Keywords</span></span>|<span data-ttu-id="d531e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d531e-107">WFRuntime</span></span>|  
|<span data-ttu-id="d531e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d531e-108">Level</span></span>|<span data-ttu-id="d531e-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="d531e-109">Information</span></span>|  
|<span data-ttu-id="d531e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d531e-110">Channel</span></span>|<span data-ttu-id="d531e-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d531e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d531e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d531e-112">Description</span></span>  
 <span data-ttu-id="d531e-113">Bir iş akışı örneği iptal edilmiş durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d531e-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d531e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d531e-114">Message</span></span>  
 <span data-ttu-id="d531e-115">İş akışı örneği kimliği: '%1' iptal edilmiş durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d531e-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d531e-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d531e-116">Details</span></span>  
  
|<span data-ttu-id="d531e-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d531e-117">Data Item Name</span></span>|<span data-ttu-id="d531e-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d531e-118">Data Item Type</span></span>|<span data-ttu-id="d531e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d531e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d531e-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="d531e-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="d531e-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="d531e-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="d531e-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d531e-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d531e-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d531e-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
