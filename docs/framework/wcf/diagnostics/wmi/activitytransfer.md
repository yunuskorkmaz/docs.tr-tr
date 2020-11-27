---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: f1978881517fe5010ccc0f5192b21bd6688f063a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291121"
---
# <a name="activitytransfer"></a><span data-ttu-id="d0e9a-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="d0e9a-102">ActivityTransfer</span></span>

<span data-ttu-id="d0e9a-103">Etkinlik aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="d0e9a-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e9a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0e9a-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d0e9a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0e9a-105">Methods</span></span>  

 <span data-ttu-id="d0e9a-106">ActivityTransfer sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0e9a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d0e9a-107">Properties</span></span>  

 <span data-ttu-id="d0e9a-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d0e9a-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="d0e9a-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="d0e9a-109">ActivityID</span></span>  
  
- <span data-ttu-id="d0e9a-110">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="d0e9a-110">Data type: object</span></span>  
    <span data-ttu-id="d0e9a-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d0e9a-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="d0e9a-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="d0e9a-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="d0e9a-113">RelatedActivityId</span><span class="sxs-lookup"><span data-stu-id="d0e9a-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="d0e9a-114">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="d0e9a-114">Data type: object</span></span>  
    <span data-ttu-id="d0e9a-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d0e9a-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="d0e9a-116">İlgili etkinlik KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="d0e9a-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e9a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0e9a-117">Requirements</span></span>  
  
|<span data-ttu-id="d0e9a-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d0e9a-118">MOF</span></span>|<span data-ttu-id="d0e9a-119">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0e9a-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0e9a-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d0e9a-120">Namespace</span></span>|<span data-ttu-id="d0e9a-121">Root\ServiceModel. içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="d0e9a-121">Defined in root\ServiceModel.</span></span>|
