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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acbc346da940caf933868a03295744132bda4733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="054aa-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="054aa-102">ActivityTransfer</span></span>
<span data-ttu-id="054aa-103">Etkinlik Aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="054aa-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="054aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="054aa-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="054aa-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="054aa-105">Methods</span></span>  
 <span data-ttu-id="054aa-106">ActivityTransfer sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="054aa-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="054aa-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="054aa-107">Properties</span></span>  
 <span data-ttu-id="054aa-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="054aa-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="054aa-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="054aa-109">ActivityID</span></span>  
  
-   <span data-ttu-id="054aa-110">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="054aa-110">Data type: object</span></span>  
    <span data-ttu-id="054aa-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="054aa-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="054aa-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="054aa-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="054aa-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="054aa-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="054aa-114">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="054aa-114">Data type: object</span></span>  
    <span data-ttu-id="054aa-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="054aa-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="054aa-116">İlgili etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="054aa-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="054aa-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="054aa-117">Requirements</span></span>  
  
|<span data-ttu-id="054aa-118">MOF</span><span class="sxs-lookup"><span data-stu-id="054aa-118">MOF</span></span>|<span data-ttu-id="054aa-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="054aa-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="054aa-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="054aa-120">Namespace</span></span>|<span data-ttu-id="054aa-121">İçinde tanımlanan root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="054aa-121">Defined in root\ServiceModel.</span></span>|
