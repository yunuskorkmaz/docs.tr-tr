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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779aabf5ec9b1bca7151eaf781c6dd6f2631b58f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="44fc8-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="44fc8-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="44fc8-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="44fc8-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44fc8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44fc8-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="44fc8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="44fc8-105">Methods</span></span>  
 <span data-ttu-id="44fc8-106">ServiceThrottlingBehavior'dan sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="44fc8-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="44fc8-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="44fc8-107">Properties</span></span>  
 <span data-ttu-id="44fc8-108">ServiceThrottlingBehavior'dan sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="44fc8-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="44fc8-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="44fc8-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="44fc8-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="44fc8-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="44fc8-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="44fc8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="44fc8-112">ServiceHost içindeki tüm dağıtıcı nesnelerinde etkin olarak işlenen ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="44fc8-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="44fc8-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="44fc8-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="44fc8-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="44fc8-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="44fc8-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="44fc8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="44fc8-116">Bir kerede yürütebilir hizmet nesneleri maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="44fc8-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="44fc8-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="44fc8-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="44fc8-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="44fc8-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="44fc8-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="44fc8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="44fc8-120">Bir ana bilgisayar aynı anda kabul edebilir oturumları maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="44fc8-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44fc8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44fc8-121">Requirements</span></span>  
  
|<span data-ttu-id="44fc8-122">MOF</span><span class="sxs-lookup"><span data-stu-id="44fc8-122">MOF</span></span>|<span data-ttu-id="44fc8-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="44fc8-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="44fc8-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="44fc8-124">Namespace</span></span>|<span data-ttu-id="44fc8-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="44fc8-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44fc8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44fc8-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
