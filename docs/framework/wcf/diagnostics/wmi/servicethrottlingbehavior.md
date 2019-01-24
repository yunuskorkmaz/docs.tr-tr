---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 98e8a720e92547ca0a893dd988b91cb7907660b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689857"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="3784a-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="3784a-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="3784a-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="3784a-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3784a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3784a-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3784a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3784a-105">Methods</span></span>  
 <span data-ttu-id="3784a-106">Denetlemek ServiceThrottlingBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="3784a-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3784a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3784a-107">Properties</span></span>  
 <span data-ttu-id="3784a-108">Denetlemek ServiceThrottlingBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3784a-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="3784a-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="3784a-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="3784a-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="3784a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="3784a-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3784a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3784a-112">Bir ServiceHost tüm dağıtıcı nesneler arasında etkin bir şekilde işlenen ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="3784a-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="3784a-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="3784a-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="3784a-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="3784a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="3784a-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3784a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3784a-116">Aynı anda çalışabilecek hizmet nesneleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="3784a-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="3784a-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="3784a-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="3784a-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="3784a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="3784a-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3784a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3784a-120">En fazla bir konak aynı anda kabul edebileceği oturum sayısını.</span><span class="sxs-lookup"><span data-stu-id="3784a-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3784a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3784a-121">Requirements</span></span>  
  
|<span data-ttu-id="3784a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3784a-122">MOF</span></span>|<span data-ttu-id="3784a-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3784a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3784a-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="3784a-124">Namespace</span></span>|<span data-ttu-id="3784a-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3784a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3784a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3784a-126">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
