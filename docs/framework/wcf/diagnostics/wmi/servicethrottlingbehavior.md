---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 3bcf205964a22cdb418d0158e5ee6439169538ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273990"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="63964-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="63964-102">ServiceThrottlingBehavior</span></span>

<span data-ttu-id="63964-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="63964-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63964-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="63964-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="63964-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="63964-105">Methods</span></span>  

 <span data-ttu-id="63964-106">Servicekısıtlar Lingbehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="63964-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="63964-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="63964-107">Properties</span></span>  

 <span data-ttu-id="63964-108">Servicekısıtlar Lingbehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="63964-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="63964-109">Maxconcurrentçağrıları</span><span class="sxs-lookup"><span data-stu-id="63964-109">MaxConcurrentCalls</span></span>  

 <span data-ttu-id="63964-110">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="63964-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="63964-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="63964-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63964-112">ServiceHost içindeki tüm Dispatcher nesnelerinde etkin olarak işlenen en fazla ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="63964-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="63964-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="63964-113">MaxConcurrentInstances</span></span>  

 <span data-ttu-id="63964-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="63964-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="63964-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="63964-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63964-116">Tek seferde yürütebilmesi için en fazla hizmet nesnesi sayısı.</span><span class="sxs-lookup"><span data-stu-id="63964-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="63964-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="63964-117">MaxConcurrentSessions</span></span>  

 <span data-ttu-id="63964-118">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="63964-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="63964-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="63964-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63964-120">Bir konağın bir anda kabul edebileceği en fazla oturum sayısı.</span><span class="sxs-lookup"><span data-stu-id="63964-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63964-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63964-121">Requirements</span></span>  
  
|<span data-ttu-id="63964-122">MOF</span><span class="sxs-lookup"><span data-stu-id="63964-122">MOF</span></span>|<span data-ttu-id="63964-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63964-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="63964-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="63964-124">Namespace</span></span>|<span data-ttu-id="63964-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="63964-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63964-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63964-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
