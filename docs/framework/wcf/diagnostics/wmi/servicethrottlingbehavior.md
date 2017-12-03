---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59f85a148d6707876a4df512d5cfbd07ca0e54b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="e6643-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="e6643-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="e6643-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="e6643-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6643-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6643-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e6643-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e6643-105">Methods</span></span>  
 <span data-ttu-id="e6643-106">ServiceThrottlingBehavior'dan sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e6643-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e6643-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e6643-107">Properties</span></span>  
 <span data-ttu-id="e6643-108">ServiceThrottlingBehavior'dan sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e6643-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="e6643-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="e6643-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="e6643-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e6643-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e6643-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e6643-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e6643-112">ServiceHost içindeki tüm dağıtıcı nesnelerinde etkin olarak işlenen ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="e6643-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="e6643-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="e6643-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="e6643-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e6643-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e6643-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e6643-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e6643-116">Bir kerede yürütebilir hizmet nesneleri maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e6643-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="e6643-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="e6643-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="e6643-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e6643-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e6643-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e6643-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e6643-120">Bir ana bilgisayar aynı anda kabul edebilir oturumları maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e6643-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6643-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6643-121">Requirements</span></span>  
  
|<span data-ttu-id="e6643-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e6643-122">MOF</span></span>|<span data-ttu-id="e6643-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e6643-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e6643-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e6643-124">Namespace</span></span>|<span data-ttu-id="e6643-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e6643-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6643-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6643-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
