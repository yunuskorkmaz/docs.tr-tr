---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509300"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="01c2f-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="01c2f-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="01c2f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="01c2f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01c2f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="01c2f-104">ID</span></span>|<span data-ttu-id="01c2f-105">1005</span><span class="sxs-lookup"><span data-stu-id="01c2f-105">1005</span></span>|  
|<span data-ttu-id="01c2f-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="01c2f-106">Keywords</span></span>|<span data-ttu-id="01c2f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="01c2f-107">WFRuntime</span></span>|  
|<span data-ttu-id="01c2f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="01c2f-108">Level</span></span>|<span data-ttu-id="01c2f-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="01c2f-109">Information</span></span>|  
|<span data-ttu-id="01c2f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="01c2f-110">Channel</span></span>|<span data-ttu-id="01c2f-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="01c2f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01c2f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01c2f-112">Description</span></span>  
 <span data-ttu-id="01c2f-113">Bir iş akışı uygulaması idled gösterir.</span><span class="sxs-lookup"><span data-stu-id="01c2f-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01c2f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="01c2f-114">Message</span></span>  
 <span data-ttu-id="01c2f-115">WorkflowApplication kimliği: '%1' boşta geçti.</span><span class="sxs-lookup"><span data-stu-id="01c2f-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01c2f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="01c2f-116">Details</span></span>  
  
|<span data-ttu-id="01c2f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="01c2f-117">Data Item Name</span></span>|<span data-ttu-id="01c2f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="01c2f-118">Data Item Type</span></span>|<span data-ttu-id="01c2f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01c2f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01c2f-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="01c2f-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="01c2f-121">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="01c2f-121">The workflow application id</span></span>|  
|<span data-ttu-id="01c2f-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="01c2f-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="01c2f-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="01c2f-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
