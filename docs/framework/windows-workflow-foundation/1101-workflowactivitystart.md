---
title: 1101 - WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 1e6db97284b7ca83d532166d96d7a42df0a51091
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924156"
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="392c1-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="392c1-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="392c1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="392c1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="392c1-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="392c1-104">ID</span></span>|<span data-ttu-id="392c1-105">1101</span><span class="sxs-lookup"><span data-stu-id="392c1-105">1101</span></span>|  
|<span data-ttu-id="392c1-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="392c1-106">Keywords</span></span>|<span data-ttu-id="392c1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="392c1-107">WFRuntime</span></span>|  
|<span data-ttu-id="392c1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="392c1-108">Level</span></span>|<span data-ttu-id="392c1-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="392c1-109">Information</span></span>|  
|<span data-ttu-id="392c1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="392c1-110">Channel</span></span>|<span data-ttu-id="392c1-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="392c1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="392c1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="392c1-112">Description</span></span>  
 <span data-ttu-id="392c1-113">Bir iş akışı etkinlik başlatıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="392c1-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="392c1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="392c1-114">Message</span></span>  
 <span data-ttu-id="392c1-115">WorkflowInstance ID: '%1' Aktivita E2E</span><span class="sxs-lookup"><span data-stu-id="392c1-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="392c1-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="392c1-116">Details</span></span>  
  
|<span data-ttu-id="392c1-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="392c1-117">Data Item Name</span></span>|<span data-ttu-id="392c1-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="392c1-118">Data Item Type</span></span>|<span data-ttu-id="392c1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="392c1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="392c1-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="392c1-120">WorkflowInstanceId</span></span>|<span data-ttu-id="392c1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="392c1-121">xs:string</span></span>|<span data-ttu-id="392c1-122">İş akışı örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="392c1-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="392c1-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="392c1-123">AppDomain</span></span>|<span data-ttu-id="392c1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="392c1-124">xs:string</span></span>|<span data-ttu-id="392c1-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="392c1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
