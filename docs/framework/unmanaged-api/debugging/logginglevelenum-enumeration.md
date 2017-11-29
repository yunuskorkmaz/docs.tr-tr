---
title: "LoggingLevelEnum Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoggingLevelEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: LoggingLevelEnum
helpviewer_keywords: LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f6041f429c057cea9607df34ec5691be84e2d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum Numaralandırması
Yönetilen iş parçacığı bir olayı günlüğe kaydettiğinde, olay günlüğüne yazılır açıklayıcı bir ileti önem düzeyini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`LTraceLevel0`|İleti izleme düzeyi 0 ' dir.|  
|`LTraceLevel1`|İleti izleme düzeyini 1 ' dir.|  
|`LTraceLevel2`|İleti izleme düzeyini 2 ' dir.|  
|`LTraceLevel3`|İleti izleme düzeyi 3 ' dir.|  
|`LTraceLevel4`|İzleme düzeyi 4 iletisidir.|  
|`LStatusLevel0`|İleti durumu düzeyi 0 ' dir.|  
|`LStatusLevel1`|İleti durumu düzeyi 1 ' dir.|  
|`LStatusLevel2`|Durum Düzey 2 iletisidir.|  
|`LStatusLevel3`|İleti durumu düzeyi 3 ' dir.|  
|`LStatusLevel4`|İleti bir durum 4 düzeydir.|  
|`LWarningLevel`|Uyarı düzeyi iletisidir.|  
|`LErrorLevel`|Bir hata düzeyi iletisidir.|  
|`LPanicLevel`|İleti bir Panik düzeydir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) çağırır [Icordebugmanagedcallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) hata ayıklayıcı yönetilen iş parçacığı günlüğe bir olay olduğunu bildirmek için yöntem. CLR değerini iletir `LoggingLevelEnum` yönetilen iş parçacığı olay günlüğüne yazan ileti önem düzeyini belirtmek için numaralandırması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.EventLog>  
 [Hata ayıklama numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
