---
title: ICorDebug Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05c95d47d57525aa2aebe16d536b771042600000
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509733"
---
# <a name="icordebug-interface"></a>ICorDebug Arabirimi
Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
> [!NOTE]
>  Karma mod (yönetilen ve yerel kod) hata ayıklaması, Windows 95, Windows 98 veya Windows ME veya x86 olmayan platformları (örneğin, IA64 ve AMD64 gibi) üzerinde desteklenmiyor.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanLaunchOrAttach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Yeni bir işlem başlatılıyor veya belirtilen işleme iliştirdikten geçerli makine ve çalışma zamanı yapılandırma bağlamında mümkün olup olmadığını belirler.|  
|[CreateProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Bir işlem ve onun birincil iş parçacığı hata ayıklayıcının denetiminin altında başlatır.|  
|[DebugActiveProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Hata ayıklayıcı, varolan bir sürece ekler.|  
|[EnumerateProcesses Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Hatası ayıklanmakta işlemler için bir numaralandırıcı alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Belirtilen işlem kimliğiyle "ICorDebugProcess" nesneyi döndürür|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Başlatır `ICorDebug` nesne.|  
|[SetManagedHandler Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Yönetilen olaylar için olay işleyicisi nesnesini belirtir.|  
|[SetUnmanagedHandler Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.|  
|[Terminate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Sonlandırır `ICorDebug` nesne.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebug` hata ayıklayıcı işleme için bir olay işleme döngüsünü temsil eder. Hata ayıklayıcı beklemelisiniz [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) serbest bırakmadan önce bu arabirimi hata ayıklaması yapılan tüm işlemlerden geri çağırma.  
  
 `ICorDebug` Nesnedir tüm daha fazla yönetilen hata ayıklama denetlemek için ilk nesne. .NET Framework sürüm 1.0 ve 1.1, bu nesne olduğu bir `CoClass` COM'dan oluşturulan nesne .NET Framework sürüm 2. 0'da, bu nesne artık değil bir `CoClass` nesne. Tarafından oluşturulmalıdır [Createdebuggingınterfacefromversion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) sürümü daha duyarlı işlevi. Bu yeni oluşturma işlevi özel uygulanışı almak istemcileri etkinleştirir `ICorDebug`, hangi ayrıca öykünür belirli bir hata ayıklama API sürümü.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
