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
# <a name="activitytransfer"></a>ActivityTransfer
Etkinlik Aktarma olayı  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ActivityTransfer sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ActivityTransfer sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="activityid"></a>Etkinlik Kimliği  
  
-   Veri türü: nesne  
    Erişim türü: salt okunur  
  
-   Etkinlik Kimliği  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   Veri türü: nesne  
    Erişim türü: salt okunur  
  
-   İlgili etkinlik kimliği  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlanır.|
