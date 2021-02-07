---
description: 'Daha fazla bilgi edinin: ActivityTransfer'
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 28f7d1c0d1056327313e7aa6be293eb325d8f265
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758014"
---
# <a name="activitytransfer"></a>ActivityTransfer

Etkinlik aktarma olayı  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ActivityTransfer sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="activityid"></a>ActivityID  
  
- Veri türü: nesne  
    Erişim türü: salt okunurdur  
  
- Etkinlik Kimliği  
  
### <a name="relatedactivityid"></a>RelatedActivityId  
  
- Veri türü: nesne  
    Erişim türü: salt okunurdur  
  
- İlgili etkinlik KIMLIĞI  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel. içinde tanımlı|
