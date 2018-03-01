---
title: ICorDebug Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ed0b3a8b42157f6a4fcbc6b4a05a416da736147
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebug-interface"></a>ICorDebug Arabirimi
Geliştiricilerin uygulamalarında ortak dil çalışma zamanı (CLR) ortamında hata ayıklamak yöntemleri sağlar.  
  
> [!NOTE]
>  Karışık mod (yönetilen ve yerel kodu) hata ayıklama Windows 95, Windows 98 veya Windows ME ya da (örneğin, IA64 ve AMD64) x86 olmayan platformlarda desteklenmiyor.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanLaunchOrAttach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Yeni bir işlem başlatılıyor veya verilen işlemine iliştirme geçerli makine ve çalışma zamanı yapılandırma bağlamında mümkün olup olmadığını belirler.|  
|[CreateProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Hata ayıklayıcı denetiminde birincil kendi iş parçacığı ve bir işlem başlatır.|  
|[DebugActiveProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Hata ayıklayıcı varolan bir işlemi ekler.|  
|[EnumerateProcesses Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Ayıklanacak işlemleri için bir numaralandırıcı alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Belirtilen işlem kimliğiyle "ICorDebugProcess" nesnesi döndürür|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Başlatır `ICorDebug` nesnesi.|  
|[SetManagedHandler Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Yönetilen olayları için olay işleyici nesnesi belirtir.|  
|[SetUnmanagedHandler Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Yönetilmeyen olayları için olay işleyici nesnesi belirtir.|  
|[Terminate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Sonlandırır `ICorDebug` nesnesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebug`hata ayıklayıcı işlem için bir olay işleme döngüye temsil eder. Hata ayıklayıcı beklemelisiniz [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) bu arabirim bırakmadan önce ayıklanacak tüm işlemlerden geri çağırma.  
  
 `ICorDebug` Nesnesidir tüm daha fazla yönetilen hata ayıklama denetlemek için ilk nesne. .NET Framework sürüm 1.0 ve 1.1, bu nesne olan bir `CoClass` COM'dan oluşturulan nesne .NET Framework sürüm 2. 0'da, bu nesne artık değil bir `CoClass` nesnesi. Tarafından oluşturulmalıdır [Createdebuggingınterfacefromversion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) sürüm daha kullanmayan işlevi. İstemcilerin, belirli bir uygulamasına almak bu yeni oluşturma işlevi sağlar `ICorDebug`, hangi ayrıca öykünür hata ayıklama API'si belirli bir sürümü.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
