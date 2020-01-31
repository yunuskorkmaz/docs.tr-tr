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
ms.openlocfilehash: d6c923f03309da3ad8092ea6119e7d850120ee2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783797"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController Arabirimi

Kod yürütme bağlamının denetlenebileceği bir <xref:System.Diagnostics.Process> ya da <xref:System.AppDomain>bir kapsamı temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Bu yöntem artık kullanılmıyor.|  
|`ICorDebugController::CommitChanges`|Bu yöntem artık kullanılmıyor.|  
|[Continue Yöntemi](icordebugcontroller-continue-method.md)|[ICorDebugController:: stop](icordebugcontroller-stop-method.md)çağrısından sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.|  
|[Detach Yöntemi](icordebugcontroller-detach-method.md)|Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.|  
|[EnumerateThreads Yöntemi](icordebugcontroller-enumeratethreads-method.md)|İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.|  
|[HasQueuedCallbacks Yöntemi](icordebugcontroller-hasqueuedcallbacks-method.md)|Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.|  
|[IsRunning Yöntemi](icordebugcontroller-isrunning-method.md)|İşlemdeki iş parçacıklarının Şu anda serbestçe çalışıp çalışmadığını gösteren bir değer alır.|  
|[SetAllThreadsDebugState Yöntemi](icordebugcontroller-setallthreadsdebugstate-method.md)|İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.|  
|[Stop Yöntemi](icordebugcontroller-stop-method.md)|İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.|  
|[Terminate Yöntemi](icordebugcontroller-terminate-method.md)|Belirtilen çıkış koduyla işlemi sonlandırır.|  
  
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

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
