---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 9995823753fc78ca3f278cd635fcf6c7d2b84325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238944"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="6b748-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="6b748-102">1041 - WorkflowApplicationPersistableIdle</span></span>

## <a name="properties"></a><span data-ttu-id="6b748-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6b748-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b748-104">ID</span><span class="sxs-lookup"><span data-stu-id="6b748-104">ID</span></span>|<span data-ttu-id="6b748-105">1041</span><span class="sxs-lookup"><span data-stu-id="6b748-105">1041</span></span>|  
|<span data-ttu-id="6b748-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="6b748-106">Keywords</span></span>|<span data-ttu-id="6b748-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6b748-107">WFRuntime</span></span>|  
|<span data-ttu-id="6b748-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="6b748-108">Level</span></span>|<span data-ttu-id="6b748-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="6b748-109">Information</span></span>|  
|<span data-ttu-id="6b748-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="6b748-110">Channel</span></span>|<span data-ttu-id="6b748-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="6b748-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6b748-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b748-112">Description</span></span>  

 <span data-ttu-id="6b748-113">Bir iş akışı uygulamasının boşta ve kalıcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b748-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="6b748-114">İş akışı uygulaması bırakılacak veya kalıcı olacak.</span><span class="sxs-lookup"><span data-stu-id="6b748-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6b748-115">İleti</span><span class="sxs-lookup"><span data-stu-id="6b748-115">Message</span></span>  

 <span data-ttu-id="6b748-116">WorkflowApplication kimliği: ' %1 ' boşta ve sürekli tablo.</span><span class="sxs-lookup"><span data-stu-id="6b748-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="6b748-117">Şu işlem gerçekleştirilecek: %2.</span><span class="sxs-lookup"><span data-stu-id="6b748-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6b748-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6b748-118">Details</span></span>  
  
|<span data-ttu-id="6b748-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="6b748-119">Data Item Name</span></span>|<span data-ttu-id="6b748-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="6b748-120">Data Item Type</span></span>|<span data-ttu-id="6b748-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b748-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6b748-122">Workflowapplicationıd</span><span class="sxs-lookup"><span data-stu-id="6b748-122">WorkflowApplicationId</span></span>|<span data-ttu-id="6b748-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="6b748-123">xs:string</span></span>|<span data-ttu-id="6b748-124">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="6b748-124">The workflow application id</span></span>|  
|<span data-ttu-id="6b748-125">Gerçekleştirilen eylem</span><span class="sxs-lookup"><span data-stu-id="6b748-125">ActionTaken</span></span>|<span data-ttu-id="6b748-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="6b748-126">xs:string</span></span>|<span data-ttu-id="6b748-127">İş akışı uygulamasında gerçekleştirilecek eylem.</span><span class="sxs-lookup"><span data-stu-id="6b748-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="6b748-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6b748-128">AppDomain</span></span>|<span data-ttu-id="6b748-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="6b748-129">xs:string</span></span>|<span data-ttu-id="6b748-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6b748-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
