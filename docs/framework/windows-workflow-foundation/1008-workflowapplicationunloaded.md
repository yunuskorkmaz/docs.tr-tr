---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925235"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="9cc78-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="9cc78-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="9cc78-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9cc78-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cc78-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9cc78-104">ID</span></span>|<span data-ttu-id="9cc78-105">1008</span><span class="sxs-lookup"><span data-stu-id="9cc78-105">1008</span></span>|  
|<span data-ttu-id="9cc78-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9cc78-106">Keywords</span></span>|<span data-ttu-id="9cc78-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9cc78-107">WFRuntime</span></span>|  
|<span data-ttu-id="9cc78-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9cc78-108">Level</span></span>|<span data-ttu-id="9cc78-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9cc78-109">Information</span></span>|  
|<span data-ttu-id="9cc78-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9cc78-110">Channel</span></span>|<span data-ttu-id="9cc78-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9cc78-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9cc78-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cc78-112">Description</span></span>  
 <span data-ttu-id="9cc78-113">Bir iş akışı uygulaması kaldırıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9cc78-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9cc78-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9cc78-114">Message</span></span>  
 <span data-ttu-id="9cc78-115">WorkflowInstance ID: '%1'. yüklenmemiş.</span><span class="sxs-lookup"><span data-stu-id="9cc78-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9cc78-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9cc78-116">Details</span></span>  
  
|<span data-ttu-id="9cc78-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9cc78-117">Data Item Name</span></span>|<span data-ttu-id="9cc78-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9cc78-118">Data Item Type</span></span>|<span data-ttu-id="9cc78-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cc78-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9cc78-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="9cc78-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9cc78-121">İş akışı örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="9cc78-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9cc78-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9cc78-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9cc78-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9cc78-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
