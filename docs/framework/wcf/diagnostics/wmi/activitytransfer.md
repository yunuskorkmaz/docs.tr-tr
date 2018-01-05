---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f3db50a32fabc117c79eef5ac086a7798f86ed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="2835e-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="2835e-102">ActivityTransfer</span></span>
<span data-ttu-id="2835e-103">Etkinlik Aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="2835e-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2835e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2835e-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2835e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2835e-105">Methods</span></span>  
 <span data-ttu-id="2835e-106">ActivityTransfer sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="2835e-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2835e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2835e-107">Properties</span></span>  
 <span data-ttu-id="2835e-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2835e-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="2835e-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="2835e-109">ActivityID</span></span>  
  
-   <span data-ttu-id="2835e-110">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="2835e-110">Data type: object</span></span>  
    <span data-ttu-id="2835e-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2835e-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="2835e-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="2835e-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="2835e-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="2835e-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="2835e-114">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="2835e-114">Data type: object</span></span>  
    <span data-ttu-id="2835e-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2835e-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="2835e-116">İlgili etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="2835e-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2835e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2835e-117">Requirements</span></span>  
  
|<span data-ttu-id="2835e-118">MOF</span><span class="sxs-lookup"><span data-stu-id="2835e-118">MOF</span></span>|<span data-ttu-id="2835e-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2835e-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2835e-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2835e-120">Namespace</span></span>|<span data-ttu-id="2835e-121">İçinde tanımlanan root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="2835e-121">Defined in root\ServiceModel.</span></span>|
