---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662819"
---
# <a name="activitytransfer"></a><span data-ttu-id="c98b8-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="c98b8-102">ActivityTransfer</span></span>
<span data-ttu-id="c98b8-103">Etkinlik Aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="c98b8-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c98b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c98b8-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c98b8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c98b8-105">Methods</span></span>  
 <span data-ttu-id="c98b8-106">ActivityTransfer sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="c98b8-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c98b8-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c98b8-107">Properties</span></span>  
 <span data-ttu-id="c98b8-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c98b8-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="c98b8-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="c98b8-109">ActivityID</span></span>  
  
- <span data-ttu-id="c98b8-110">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="c98b8-110">Data type: object</span></span>  
    <span data-ttu-id="c98b8-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c98b8-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="c98b8-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="c98b8-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="c98b8-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="c98b8-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="c98b8-114">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="c98b8-114">Data type: object</span></span>  
    <span data-ttu-id="c98b8-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c98b8-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="c98b8-116">İlgili etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="c98b8-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c98b8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c98b8-117">Requirements</span></span>  
  
|<span data-ttu-id="c98b8-118">MOF</span><span class="sxs-lookup"><span data-stu-id="c98b8-118">MOF</span></span>|<span data-ttu-id="c98b8-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c98b8-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c98b8-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="c98b8-120">Namespace</span></span>|<span data-ttu-id="c98b8-121">Root\ServiceModel içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c98b8-121">Defined in root\ServiceModel.</span></span>|
