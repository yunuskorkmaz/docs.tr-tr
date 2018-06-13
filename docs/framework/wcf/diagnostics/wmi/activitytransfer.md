---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484194"
---
# <a name="activitytransfer"></a><span data-ttu-id="2f982-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="2f982-102">ActivityTransfer</span></span>
<span data-ttu-id="2f982-103">Etkinlik Aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="2f982-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f982-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f982-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2f982-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2f982-105">Methods</span></span>  
 <span data-ttu-id="2f982-106">ActivityTransfer sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="2f982-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2f982-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2f982-107">Properties</span></span>  
 <span data-ttu-id="2f982-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2f982-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="2f982-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="2f982-109">ActivityID</span></span>  
  
-   <span data-ttu-id="2f982-110">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="2f982-110">Data type: object</span></span>  
    <span data-ttu-id="2f982-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2f982-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="2f982-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="2f982-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="2f982-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="2f982-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="2f982-114">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="2f982-114">Data type: object</span></span>  
    <span data-ttu-id="2f982-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2f982-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="2f982-116">İlgili etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="2f982-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f982-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f982-117">Requirements</span></span>  
  
|<span data-ttu-id="2f982-118">MOF</span><span class="sxs-lookup"><span data-stu-id="2f982-118">MOF</span></span>|<span data-ttu-id="2f982-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2f982-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2f982-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2f982-120">Namespace</span></span>|<span data-ttu-id="2f982-121">İçinde tanımlanan root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="2f982-121">Defined in root\ServiceModel.</span></span>|
