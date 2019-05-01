---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924195"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="4791d-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="4791d-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="4791d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4791d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4791d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4791d-104">ID</span></span>|<span data-ttu-id="4791d-105">1041</span><span class="sxs-lookup"><span data-stu-id="4791d-105">1041</span></span>|  
|<span data-ttu-id="4791d-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4791d-106">Keywords</span></span>|<span data-ttu-id="4791d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4791d-107">WFRuntime</span></span>|  
|<span data-ttu-id="4791d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4791d-108">Level</span></span>|<span data-ttu-id="4791d-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="4791d-109">Information</span></span>|  
|<span data-ttu-id="4791d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4791d-110">Channel</span></span>|<span data-ttu-id="4791d-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4791d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4791d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4791d-112">Description</span></span>  
 <span data-ttu-id="4791d-113">Bir iş akışı uygulaması boşta ve kalıcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4791d-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="4791d-114">İş akışı uygulama idled veya kalıcı.</span><span class="sxs-lookup"><span data-stu-id="4791d-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4791d-115">İleti</span><span class="sxs-lookup"><span data-stu-id="4791d-115">Message</span></span>  
 <span data-ttu-id="4791d-116">WorkflowApplication ID: '%1', boş ve kalıcı.</span><span class="sxs-lookup"><span data-stu-id="4791d-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="4791d-117">Aşağıdaki işlem yapılmayacak: %2.</span><span class="sxs-lookup"><span data-stu-id="4791d-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4791d-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4791d-118">Details</span></span>  
  
|<span data-ttu-id="4791d-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4791d-119">Data Item Name</span></span>|<span data-ttu-id="4791d-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4791d-120">Data Item Type</span></span>|<span data-ttu-id="4791d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4791d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4791d-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="4791d-122">WorkflowApplicationId</span></span>|<span data-ttu-id="4791d-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="4791d-123">xs:string</span></span>|<span data-ttu-id="4791d-124">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="4791d-124">The workflow application id</span></span>|  
|<span data-ttu-id="4791d-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="4791d-125">ActionTaken</span></span>|<span data-ttu-id="4791d-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="4791d-126">xs:string</span></span>|<span data-ttu-id="4791d-127">İş akışı uygulama üzerinde gerçekleştirilecek eylem.</span><span class="sxs-lookup"><span data-stu-id="4791d-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="4791d-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4791d-128">AppDomain</span></span>|<span data-ttu-id="4791d-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="4791d-129">xs:string</span></span>|<span data-ttu-id="4791d-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4791d-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
