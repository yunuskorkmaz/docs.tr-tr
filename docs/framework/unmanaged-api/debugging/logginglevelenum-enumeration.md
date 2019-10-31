---
title: LoggingLevelEnum Numaralandırması
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 01e1eafd9955a0876f77e34eb73c2a3fc6d815c2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139212"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum Numaralandırması
Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`LTraceLevel0`|İleti bir izleme düzeyi 0 ' dır.|  
|`LTraceLevel1`|İleti bir izleme düzeyi 1 ' dir.|  
|`LTraceLevel2`|İleti bir izleme düzeyi 2 ' dir.|  
|`LTraceLevel3`|İleti bir izleme düzeyi 3 ' dir.|  
|`LTraceLevel4`|İleti bir izleme düzeyi 4 ' dir.|  
|`LStatusLevel0`|İleti bir durum düzeyi 0 ' dır.|  
|`LStatusLevel1`|İleti bir durum düzeyi 1 ' dir.|  
|`LStatusLevel2`|İleti bir durum düzeyi 2 ' dir.|  
|`LStatusLevel3`|İleti bir durum düzeyi 3 ' dir.|  
|`LStatusLevel4`|İleti bir durum düzeyi 4 ' dir.|  
|`LWarningLevel`|İleti bir uyarı düzeyidir.|  
|`LErrorLevel`|İleti bir hata düzeyidir.|  
|`LPanicLevel`|İleti bir panik düzeyidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR), hata ayıklayıcıya yönetilen bir iş parçacığının günlüğe kaydettiği bir olay olduğunu bildirmek için [ICorDebugManagedCallback:: LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) yöntemini çağırır. CLR, yönetilen iş parçacığının olay günlüğüne yazdığı iletinin önem derecesini belirtmek için `LoggingLevelEnum` numaralandırması değerini geçirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.EventLog>
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
