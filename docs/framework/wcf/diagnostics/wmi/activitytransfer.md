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
ms.openlocfilehash: 7c1caf0ae27efce858328e5db88434253be61d50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="4ac31-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="4ac31-102">ActivityTransfer</span></span>
<span data-ttu-id="4ac31-103">Etkinlik Aktarma olayı</span><span class="sxs-lookup"><span data-stu-id="4ac31-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ac31-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4ac31-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4ac31-105">Methods</span></span>  
 <span data-ttu-id="4ac31-106">ActivityTransfer sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="4ac31-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4ac31-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4ac31-107">Properties</span></span>  
 <span data-ttu-id="4ac31-108">ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4ac31-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="4ac31-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="4ac31-109">ActivityID</span></span>  
  
-   <span data-ttu-id="4ac31-110">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="4ac31-110">Data type: object</span></span>  
    <span data-ttu-id="4ac31-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4ac31-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="4ac31-112">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="4ac31-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="4ac31-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="4ac31-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="4ac31-114">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="4ac31-114">Data type: object</span></span>  
    <span data-ttu-id="4ac31-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4ac31-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="4ac31-116">İlgili etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="4ac31-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ac31-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ac31-117">Requirements</span></span>  
  
|<span data-ttu-id="4ac31-118">MOF</span><span class="sxs-lookup"><span data-stu-id="4ac31-118">MOF</span></span>|<span data-ttu-id="4ac31-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4ac31-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4ac31-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4ac31-120">Namespace</span></span>|<span data-ttu-id="4ac31-121">İçinde tanımlanan root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="4ac31-121">Defined in root\ServiceModel.</span></span>|
