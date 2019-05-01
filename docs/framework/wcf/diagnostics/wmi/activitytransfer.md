---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964302"
---
# <a name="activitytransfer"></a><span data-ttu-id="4c340-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="4c340-102">ActivityTransfer</span></span>
<span data-ttu-id="4c340-103">Etkinlik Aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="4c340-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c340-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c340-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4c340-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c340-105">Methods</span></span>  
 <span data-ttu-id="4c340-106">ActivityTransfer sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4c340-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4c340-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4c340-107">Properties</span></span>  
 <span data-ttu-id="4c340-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4c340-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="4c340-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="4c340-109">ActivityID</span></span>  
  
- <span data-ttu-id="4c340-110">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="4c340-110">Data type: object</span></span>  
    <span data-ttu-id="4c340-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4c340-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="4c340-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="4c340-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="4c340-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="4c340-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="4c340-114">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="4c340-114">Data type: object</span></span>  
    <span data-ttu-id="4c340-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4c340-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="4c340-116">İlgili etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="4c340-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c340-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c340-117">Requirements</span></span>  
  
|<span data-ttu-id="4c340-118">MOF</span><span class="sxs-lookup"><span data-stu-id="4c340-118">MOF</span></span>|<span data-ttu-id="4c340-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4c340-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4c340-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4c340-120">Namespace</span></span>|<span data-ttu-id="4c340-121">Root\ServiceModel içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4c340-121">Defined in root\ServiceModel.</span></span>|
