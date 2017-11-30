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
# <a name="activitytransfer"></a>ActivityTransfer
Etkinlik Aktarma olayı  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ActivityTransfer sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="activityid"></a>Etkinlik Kimliği  
  
-   Veri türü: nesnesi  
    Erişim türüne: salt okunur  
  
-   Etkinlik Kimliği  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   Veri türü: nesnesi  
    Erişim türüne: salt okunur  
  
-   İlgili etkinlik kimliği  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel.|
