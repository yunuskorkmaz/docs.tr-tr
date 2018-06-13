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
