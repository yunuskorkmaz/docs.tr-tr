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
ms.openlocfilehash: 0ca66f001d04bc86b64e0fe2d1cd37559e4fc633
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785110"
---
# <a name="icordebug-interface"></a>ICorDebug Arabirimi
Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamındaki uygulamalarda hata ayıklamasına imkan tanıyan yöntemler sağlar.  
  
> [!NOTE]
> Karma mod (yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (ıA64 ve AMD64 gibi) desteklenmez.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanLaunchOrAttach Yöntemi](icordebug-canlaunchorattach-method.md)|Yeni bir işlemin başlatılmasını veya belirtilen işleme, geçerli makine ve çalışma zamanı yapılandırması bağlamında mümkün olup olmadığını belirler.|  
|[CreateProcess Yöntemi](icordebug-createprocess-method.md)|Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.|  
|[DebugActiveProcess Yöntemi](icordebug-debugactiveprocess-method.md)|Hata ayıklayıcıyı mevcut bir işleme iliştirir.|  
|[EnumerateProcesses Yöntemi](icordebug-enumerateprocesses-method.md)|Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.|  
|[GetProcess Yöntemi](icordebug-getprocess-method.md)|Verilen işlem KIMLIĞINE sahip "ICorDebugProcess" nesnesini döndürür.|  
|[Initialize Yöntemi](icordebug-initialize-method.md)|`ICorDebug` nesnesini başlatır.|  
|[SetManagedHandler Yöntemi](icordebug-setmanagedhandler-method.md)|Yönetilen olaylar için olay işleyicisi nesnesini belirtir.|  
|[SetUnmanagedHandler Yöntemi](icordebug-setunmanagedhandler-method.md)|Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.|  
|[Terminate Yöntemi](icordebug-terminate-method.md)|`ICorDebug` nesnesini sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebug` bir hata ayıklayıcı işlemi için bir olay işleme döngüsünü temsil eder. Hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess geri çağırması](icordebugmanagedcallback-exitprocess-method.md) , bu arabirimi serbest bırakmadan önce hata ayıklamakta olan tüm işlemlerden geri aramasını beklemesi gerekir.  
  
 `ICorDebug` nesnesi, daha fazla yönetilen hata ayıklamayı denetlemek için ilk nesnedir. Bu nesne, 1,0 ve 1,1 .NET Framework sürümlerinde, COM tarafından oluşturulan bir `CoClass` nesnesidir. .NET Framework sürüm 2,0 ' de, bu nesne artık `CoClass` bir nesne değildir. Daha fazla sürüm tanıyan [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) işlevi tarafından oluşturulmalıdır. Bu yeni oluşturma işlevi, istemcilerin belirli bir `ICorDebug`uygulamasını almasını sağlar ve bu da hata ayıklama API 'sinin belirli bir sürümüne öykünür.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
