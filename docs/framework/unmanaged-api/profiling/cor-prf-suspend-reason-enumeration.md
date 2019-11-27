---
title: COR_PRF_SUSPEND_REASON Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: d2d9ca77e764fe439753f1174a42af5ef80faa59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447712"
---
# <a name="cor_prf_suspend_reason-enumeration"></a>COR_PRF_SUSPEND_REASON Numaralandırması
Çalışma zamanının askıya alınma nedenini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|Beklenmeyen bir nedenden dolayı çalışma zamanı askıya alındı.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Bir çöp toplama isteğine hizmet vermek için çalışma zamanı askıya alındı.<br /><br /> [ICorProfilerCallback:: RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve [ICorProfilerCallback:: RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırmaları arasında çöp toplama ile ilgili geri çağırmaları meydana gelir.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Çalışma zamanı, bir `AppDomain` kapatılabilen şekilde askıya alınır.<br /><br /> Çalışma zamanı askıya alındığında, çalışma zamanı hangi iş parçacıklarının kapanmakta olduğunu ve sürdürüldiklerinde iptal olarak ayarlandığını belirleyen `AppDomain`. Bu askıya alma sırasında `AppDomain`özel geri çağırma yok.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Çalışma zamanı, kod alma işleminin gerçekleşmesi için askıya alındı.<br /><br /> Kod işleme, yalnızca tam zamanında (JıT) derleyici tarafından etkin hale geldiğinde kodun etkin hale getiriliyor. `ICorProfilerCallback::RuntimeSuspendFinished` ve `ICorProfilerCallback::RuntimeResumeStarted` geri çağırmaları arasında kod geri çağırmaları oluşur. **Note:**  CLR JıT, .NET Framework sürüm 2,0 ' deki işlevleri göstermez, bu nedenle bu değer 2,0 ' de kullanılmaz.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Çalışma zamanı, kapanması için askıya alındı. İşlemi gerçekleştirmek için tüm iş parçacıklarını askıya almalıdır.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Çalışma zamanı, işlem içi hata ayıklama için askıya alındı.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Bir çöp toplama işlemine hazırlanmak için çalışma zamanı askıya alındı.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Çalışma zamanı, JıT yeniden derleme için askıya alındı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının çalışmaya devam etmesine izin verilir, çalışma zamanı yeniden girmeye çalışır ve bu noktada çalışma zamanı sürdürülene kadar da askıya alınır. Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir. Çalışma zamanının içindeki tüm iş parçacıkları, kesilebilir kodunda olmaları durumunda veya kesilebilir koduna ulaştığında askıya alınması isteniyorsa hemen askıya alınır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
