---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008635"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="9883c-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="9883c-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="9883c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9883c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9883c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9883c-104">ID</span></span>|<span data-ttu-id="9883c-105">1003</span><span class="sxs-lookup"><span data-stu-id="9883c-105">1003</span></span>|  
|<span data-ttu-id="9883c-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9883c-106">Keywords</span></span>|<span data-ttu-id="9883c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9883c-107">WFRuntime</span></span>|  
|<span data-ttu-id="9883c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9883c-108">Level</span></span>|<span data-ttu-id="9883c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9883c-109">Information</span></span>|  
|<span data-ttu-id="9883c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9883c-110">Channel</span></span>|<span data-ttu-id="9883c-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9883c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9883c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9883c-112">Description</span></span>  
 <span data-ttu-id="9883c-113">Bir iş akışı örneği iptal edildi durumunda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9883c-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9883c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9883c-114">Message</span></span>  
 <span data-ttu-id="9883c-115">WorkflowInstance ID: '%1' iptal edildi durumunda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9883c-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9883c-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9883c-116">Details</span></span>  
  
|<span data-ttu-id="9883c-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9883c-117">Data Item Name</span></span>|<span data-ttu-id="9883c-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9883c-118">Data Item Type</span></span>|<span data-ttu-id="9883c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9883c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9883c-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="9883c-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9883c-121">İş akışı örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="9883c-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9883c-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9883c-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9883c-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9883c-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
