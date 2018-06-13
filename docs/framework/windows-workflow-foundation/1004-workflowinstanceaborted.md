---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d1eaf3cf107a6b5e244cc2d9372ee68d387ef6c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510672"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="84c6c-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="84c6c-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="84c6c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="84c6c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84c6c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="84c6c-104">ID</span></span>|<span data-ttu-id="84c6c-105">1004</span><span class="sxs-lookup"><span data-stu-id="84c6c-105">1004</span></span>|  
|<span data-ttu-id="84c6c-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="84c6c-106">Keywords</span></span>|<span data-ttu-id="84c6c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="84c6c-107">WFRuntime</span></span>|  
|<span data-ttu-id="84c6c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="84c6c-108">Level</span></span>|<span data-ttu-id="84c6c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="84c6c-109">Information</span></span>|  
|<span data-ttu-id="84c6c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="84c6c-110">Channel</span></span>|<span data-ttu-id="84c6c-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="84c6c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="84c6c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84c6c-112">Description</span></span>  
 <span data-ttu-id="84c6c-113">Bir özel durum ile bir akışı örneği durdurdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84c6c-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="84c6c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="84c6c-114">Message</span></span>  
 <span data-ttu-id="84c6c-115">İş akışı örneği kimliği: '%1' olan bir özel durum durduruldu.</span><span class="sxs-lookup"><span data-stu-id="84c6c-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="84c6c-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="84c6c-116">Details</span></span>  
  
|<span data-ttu-id="84c6c-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="84c6c-117">Data Item Name</span></span>|<span data-ttu-id="84c6c-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="84c6c-118">Data Item Type</span></span>|<span data-ttu-id="84c6c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84c6c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="84c6c-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="84c6c-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="84c6c-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="84c6c-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="84c6c-122">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="84c6c-122">Exception</span></span>|`xs:string`|<span data-ttu-id="84c6c-123">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="84c6c-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="84c6c-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="84c6c-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="84c6c-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="84c6c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
