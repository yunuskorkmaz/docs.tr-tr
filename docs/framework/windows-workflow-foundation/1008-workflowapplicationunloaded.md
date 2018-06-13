---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509567"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="f9cac-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="f9cac-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="f9cac-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f9cac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9cac-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f9cac-104">ID</span></span>|<span data-ttu-id="f9cac-105">1008</span><span class="sxs-lookup"><span data-stu-id="f9cac-105">1008</span></span>|  
|<span data-ttu-id="f9cac-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f9cac-106">Keywords</span></span>|<span data-ttu-id="f9cac-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f9cac-107">WFRuntime</span></span>|  
|<span data-ttu-id="f9cac-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f9cac-108">Level</span></span>|<span data-ttu-id="f9cac-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f9cac-109">Information</span></span>|  
|<span data-ttu-id="f9cac-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f9cac-110">Channel</span></span>|<span data-ttu-id="f9cac-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f9cac-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f9cac-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9cac-112">Description</span></span>  
 <span data-ttu-id="f9cac-113">Bir iş akışı uygulaması kaldırıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9cac-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f9cac-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f9cac-114">Message</span></span>  
 <span data-ttu-id="f9cac-115">İş akışı örneği kimliği: '%1'. yüklenmeyen.</span><span class="sxs-lookup"><span data-stu-id="f9cac-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f9cac-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f9cac-116">Details</span></span>  
  
|<span data-ttu-id="f9cac-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f9cac-117">Data Item Name</span></span>|<span data-ttu-id="f9cac-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f9cac-118">Data Item Type</span></span>|<span data-ttu-id="f9cac-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9cac-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f9cac-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="f9cac-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="f9cac-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="f9cac-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="f9cac-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f9cac-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f9cac-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f9cac-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
