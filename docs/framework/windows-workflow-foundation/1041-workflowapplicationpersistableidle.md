---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509673"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="22309-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="22309-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="22309-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="22309-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22309-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="22309-104">ID</span></span>|<span data-ttu-id="22309-105">1041</span><span class="sxs-lookup"><span data-stu-id="22309-105">1041</span></span>|  
|<span data-ttu-id="22309-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="22309-106">Keywords</span></span>|<span data-ttu-id="22309-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="22309-107">WFRuntime</span></span>|  
|<span data-ttu-id="22309-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="22309-108">Level</span></span>|<span data-ttu-id="22309-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="22309-109">Information</span></span>|  
|<span data-ttu-id="22309-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="22309-110">Channel</span></span>|<span data-ttu-id="22309-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="22309-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="22309-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22309-112">Description</span></span>  
 <span data-ttu-id="22309-113">Bir iş akışı uygulaması boşta ve kalıcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="22309-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="22309-114">İş akışı uygulama idled ya da kalıcı.</span><span class="sxs-lookup"><span data-stu-id="22309-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="22309-115">İleti</span><span class="sxs-lookup"><span data-stu-id="22309-115">Message</span></span>  
 <span data-ttu-id="22309-116">WorkflowApplication kimliği: boşta ve kalıcı '%1'.</span><span class="sxs-lookup"><span data-stu-id="22309-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="22309-117">Aşağıdaki işlem yapılmaz: %2.</span><span class="sxs-lookup"><span data-stu-id="22309-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="22309-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="22309-118">Details</span></span>  
  
|<span data-ttu-id="22309-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="22309-119">Data Item Name</span></span>|<span data-ttu-id="22309-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="22309-120">Data Item Type</span></span>|<span data-ttu-id="22309-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22309-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="22309-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="22309-122">WorkflowApplicationId</span></span>|<span data-ttu-id="22309-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="22309-123">xs:string</span></span>|<span data-ttu-id="22309-124">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="22309-124">The workflow application id</span></span>|  
|<span data-ttu-id="22309-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="22309-125">ActionTaken</span></span>|<span data-ttu-id="22309-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="22309-126">xs:string</span></span>|<span data-ttu-id="22309-127">İş akışı uygulaması üzerinde gerçekleştirilecek eylem.</span><span class="sxs-lookup"><span data-stu-id="22309-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="22309-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="22309-128">AppDomain</span></span>|<span data-ttu-id="22309-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="22309-129">xs:string</span></span>|<span data-ttu-id="22309-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="22309-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
