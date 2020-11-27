---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 0409277821a7cca3f97fcec1bb383aba9583a1f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262222"
---
# <a name="wsat_tracerecord"></a>WSAT_TraceRecord

WSAT_TraceRecord  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 WSAT_TraceRecord sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="activityid"></a>ActivityID  

 Veri türü: nesne  
Erişim türü: salt okunurdur  
  
 İzleme kaydının etkinlik KIMLIĞI.  
  
### <a name="eventid"></a>EventID  

 Veri türü: Sint32  
Erişim türü: salt okunurdur  
  
 İzleme kaydının olay KIMLIĞI.  
  
### <a name="tracerecord"></a>Izleme kaydı  

 Veri türü: dize  
Erişim türü: salt okunurdur  
  
 İzleme kaydı  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|
