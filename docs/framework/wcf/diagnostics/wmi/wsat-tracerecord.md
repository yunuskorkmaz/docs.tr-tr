---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 WSAT_TraceRecord sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="activityid"></a>Etkinlik Kimliği  
 Veri türü: nesnesi  
Erişim türüne: salt okunur  
  
 İzleme kaydı etkinlik kimliği.  
  
### <a name="eventid"></a>Olay Kimliği  
 Veri türü: SINT32  
Erişim türüne: salt okunur  
  
 İzleme kaydı olay kimliği.  
  
### <a name="tracerecord"></a>TraceRecord  
 Veri türü: dize  
Erişim türüne: salt okunur  
  
 İzleme kaydı  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|
