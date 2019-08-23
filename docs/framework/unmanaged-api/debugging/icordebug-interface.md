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
ms.openlocfilehash: afbf480d69e97662b5963706bb8c192aec0325a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966291"
---
# <a name="icordebug-interface"></a>ICorDebug Arabirimi
Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamındaki uygulamalarda hata ayıklamasına imkan tanıyan yöntemler sağlar.  
  
> [!NOTE]
> Karma mod (yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (ıA64 ve AMD64 gibi) desteklenmez.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanLaunchOrAttach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Yeni bir işlemin başlatılmasını veya belirtilen işleme, geçerli makine ve çalışma zamanı yapılandırması bağlamında mümkün olup olmadığını belirler.|  
|[CreateProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.|  
|[DebugActiveProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Hata ayıklayıcıyı mevcut bir işleme iliştirir.|  
|[EnumerateProcesses Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Verilen işlem KIMLIĞINE sahip "ICorDebugProcess" nesnesini döndürür.|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|`ICorDebug` Nesnesini başlatır.|  
|[SetManagedHandler Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Yönetilen olaylar için olay işleyicisi nesnesini belirtir.|  
|[SetUnmanagedHandler Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.|  
|[Terminate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|`ICorDebug` Nesneyi sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebug`hata ayıklayıcı işlemi için bir olay işleme döngüsünü temsil eder. Hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess geri çağırması](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) , bu arabirimi serbest bırakmadan önce hata ayıklamakta olan tüm işlemlerden geri aramasını beklemesi gerekir.  
  
 `ICorDebug` Nesne, daha fazla yönetilen hata ayıklamayı denetlemek için ilk nesnedir. .NET Framework sürüm 1,0 ve 1,1 ' de, bu nesne com ' `CoClass` dan oluşturulan bir nesnedir. .NET Framework sürüm 2,0 ' de, bu nesne artık bir `CoClass` nesne değildir. Daha fazla sürüm tanıyan [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) işlevi tarafından oluşturulmalıdır. Bu yeni oluşturma işlevi `ICorDebug`, istemcilerin belirli bir uygulamasını almasını sağlar ve bu da hata ayıklama API 'sinin belirli bir sürümüne öykünür.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
