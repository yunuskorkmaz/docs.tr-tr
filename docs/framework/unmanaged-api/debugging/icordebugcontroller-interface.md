---
title: ICorDebugController Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 27f991c12ea7786d6146b5731848ca5ad3a37e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125366"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController Arabirimi

Kod yürütme bağlamının denetlenebileceği bir <xref:System.Diagnostics.Process> ya da <xref:System.AppDomain>bir kapsamı temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Bu yöntem artık kullanılmıyor.|  
|`ICorDebugController::CommitChanges`|Bu yöntem artık kullanılmıyor.|  
|[Continue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|[ICorDebugController:: stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)çağrısından sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.|  
|[Detach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.|  
|[EnumerateThreads Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.|  
|[HasQueuedCallbacks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.|  
|[IsRunning Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|İşlemdeki iş parçacıklarının Şu anda serbestçe çalışıp çalışmadığını gösteren bir değer alır.|  
|[SetAllThreadsDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.|  
|[Stop Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.|  
|[Terminate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Belirtilen çıkış koduyla işlemi sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugController` bir işlemi denetleriyorda kapsam, işlemin tüm iş parçacıklarını içerir. `ICorDebugController` bir uygulama etki alanını denetleriyorda kapsam, yalnızca ilgili uygulama etki alanının iş parçacıklarını içerir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
