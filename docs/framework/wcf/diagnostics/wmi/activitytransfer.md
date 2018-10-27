---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034437"
---
# <a name="activitytransfer"></a><span data-ttu-id="a75d4-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="a75d4-102">ActivityTransfer</span></span>
<span data-ttu-id="a75d4-103">Etkinlik Aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="a75d4-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a75d4-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a75d4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a75d4-105">Methods</span></span>  
 <span data-ttu-id="a75d4-106">ActivityTransfer sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a75d4-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a75d4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a75d4-107">Properties</span></span>  
 <span data-ttu-id="a75d4-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a75d4-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="a75d4-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="a75d4-109">ActivityID</span></span>  
  
-   <span data-ttu-id="a75d4-110">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="a75d4-110">Data type: object</span></span>  
    <span data-ttu-id="a75d4-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a75d4-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="a75d4-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="a75d4-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="a75d4-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="a75d4-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="a75d4-114">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="a75d4-114">Data type: object</span></span>  
    <span data-ttu-id="a75d4-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a75d4-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="a75d4-116">İlgili etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="a75d4-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75d4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a75d4-117">Requirements</span></span>  
  
|<span data-ttu-id="a75d4-118">MOF</span><span class="sxs-lookup"><span data-stu-id="a75d4-118">MOF</span></span>|<span data-ttu-id="a75d4-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a75d4-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a75d4-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a75d4-120">Namespace</span></span>|<span data-ttu-id="a75d4-121">Root\ServiceModel içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a75d4-121">Defined in root\ServiceModel.</span></span>|
