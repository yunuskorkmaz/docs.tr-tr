---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008648"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="cf1e7-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="cf1e7-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="cf1e7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cf1e7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf1e7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="cf1e7-104">ID</span></span>|<span data-ttu-id="cf1e7-105">1001</span><span class="sxs-lookup"><span data-stu-id="cf1e7-105">1001</span></span>|  
|<span data-ttu-id="cf1e7-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="cf1e7-106">Keywords</span></span>|<span data-ttu-id="cf1e7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cf1e7-107">WFRuntime</span></span>|  
|<span data-ttu-id="cf1e7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="cf1e7-108">Level</span></span>|<span data-ttu-id="cf1e7-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="cf1e7-109">Information</span></span>|  
|<span data-ttu-id="cf1e7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="cf1e7-110">Channel</span></span>|<span data-ttu-id="cf1e7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="cf1e7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cf1e7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf1e7-112">Description</span></span>  
 <span data-ttu-id="cf1e7-113">Bir iş akışı uygulama kapalı durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf1e7-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cf1e7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="cf1e7-114">Message</span></span>  
 <span data-ttu-id="cf1e7-115">WorkflowInstance ID: '%1' kapalı durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="cf1e7-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cf1e7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cf1e7-116">Details</span></span>  
  
|<span data-ttu-id="cf1e7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="cf1e7-117">Data Item Name</span></span>|<span data-ttu-id="cf1e7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="cf1e7-118">Data Item Type</span></span>|<span data-ttu-id="cf1e7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf1e7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cf1e7-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="cf1e7-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cf1e7-121">İş akışı örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="cf1e7-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cf1e7-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cf1e7-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cf1e7-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="cf1e7-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
