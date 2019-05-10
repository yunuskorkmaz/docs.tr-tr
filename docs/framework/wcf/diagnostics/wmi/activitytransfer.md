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
  
- Veri türü: nesne  
    Erişim türü: salt okunur  
  
- Etkinlik Kimliği  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- Veri türü: nesne  
    Erişim türü: salt okunur  
  
- İlgili etkinlik kimliği  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlanır.|
