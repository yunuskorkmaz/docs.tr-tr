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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81b671721e1416ab9717442d4d7fc727b938ee2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980496"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController Arabirimi

Bir kapsamı temsil eder bir <xref:System.Diagnostics.Process> veya <xref:System.AppDomain>, hangi kod yürütme bağlamının denetlenebileceği.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Bu yöntem artık kullanılmıyor.|  
|`ICorDebugController::CommitChanges`|Bu yöntem artık kullanılmıyor.|  
|[Continue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Yönetilen iş parçacıklarının yürütülmesini çağrısı yapıldıktan sonra sürdürür [Icordebugcontroller::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.|  
|[EnumerateThreads Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Bir numaralandırıcı işlemde etkin yönetilen iş parçacıkları için alır.|  
|[HasQueuedCallbacks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Tüm yönetilen geri çağırmaları belirtilen iş parçacığı için sıraya alınmış olup olmadığını gösteren bir değer alır.|  
|[IsRunning Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|İşlemdeki iş parçacıkları şu anda özgürce çalışıp çalışmadığını gösteren bir değer alır.|  
|[SetAllThreadsDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|İşlemdeki tüm yönetilen iş parçacığı hata ayıklama durumunu ayarlar.|  
|[Stop Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Yönetilen kod işlemde çalışan tüm iş parçacıkları üzerinde işbirliği yapan Durma gerçekleştirir.|  
|[Terminate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Belirtilen çıkış kodu ile işlemi sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `ICorDebugController` olduğundan bir işlem denetleme, kapsamı işlemin tüm iş parçacıklarını içerir. Varsa `ICorDebugController` olan bir uygulama etki alanı denetleme, kapsamı yalnızca bu belirli uygulama etki alanının iş parçacıklarını içerir.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
