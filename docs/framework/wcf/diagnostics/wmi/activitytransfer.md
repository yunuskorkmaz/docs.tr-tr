---
description: 'Daha fazla bilgi edinin: ActivityTransfer'
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 28f7d1c0d1056327313e7aa6be293eb325d8f265
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758014"
---
# <a name="activitytransfer"></a><span data-ttu-id="24331-103">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="24331-103">ActivityTransfer</span></span>

<span data-ttu-id="24331-104">Etkinlik aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="24331-104">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24331-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="24331-105">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="24331-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="24331-106">Methods</span></span>  

 <span data-ttu-id="24331-107">ActivityTransfer sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="24331-107">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="24331-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="24331-108">Properties</span></span>  

 <span data-ttu-id="24331-109">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="24331-109">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="24331-110">ActivityID</span><span class="sxs-lookup"><span data-stu-id="24331-110">ActivityID</span></span>  
  
- <span data-ttu-id="24331-111">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="24331-111">Data type: object</span></span>  
    <span data-ttu-id="24331-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="24331-112">Access type: Read-only</span></span>  
  
- <span data-ttu-id="24331-113">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="24331-113">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="24331-114">RelatedActivityId</span><span class="sxs-lookup"><span data-stu-id="24331-114">RelatedActivityID</span></span>  
  
- <span data-ttu-id="24331-115">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="24331-115">Data type: object</span></span>  
    <span data-ttu-id="24331-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="24331-116">Access type: Read-only</span></span>  
  
- <span data-ttu-id="24331-117">İlgili etkinlik KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="24331-117">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24331-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24331-118">Requirements</span></span>  
  
|<span data-ttu-id="24331-119">MOF</span><span class="sxs-lookup"><span data-stu-id="24331-119">MOF</span></span>|<span data-ttu-id="24331-120">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="24331-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="24331-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="24331-121">Namespace</span></span>|<span data-ttu-id="24331-122">Root\ServiceModel. içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="24331-122">Defined in root\ServiceModel.</span></span>|
