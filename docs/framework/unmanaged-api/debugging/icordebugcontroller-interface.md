---
title: Icordebugcontroller Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController
helpviewer_keywords: ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a>Icordebugcontroller Interface1
Bir kapsamı ya da temsil eden bir <xref:System.Diagnostics.Process> veya bir <xref:System.AppDomain>, hangi kod yürütme bağlamı denetlenebilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Bu yöntem artık kullanılmıyor.|  
|`ICorDebugController::CommitChanges`|Bu yöntem artık kullanılmıyor.|  
|[Continue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Yönetilen iş parçacığı yürütülmesi için bir çağrı sonra sürdürür [Icordebugcontroller::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.|  
|[EnumerateThreads Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Bir numaralandırıcı etkin yönetilen iş parçacığı için işlem sırasında alır.|  
|[HasQueuedCallbacks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Tüm yönetilen geri aramalar için belirtilen iş parçacığı sıraya alınmış olup olmadığını belirten bir değer alır.|  
|[IsRunning Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|İşlemdeki iş parçacıklarının ücretsiz olarak çalışmakta olan olup olmadığını belirten bir değer alır.|  
|[SetAllThreadsDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Tüm yönetilen iş parçacığı hata ayıklama durumunu işleminde ayarlar.|  
|[Stop Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Yönetilen kod işlemde çalışan tüm iş parçacıklarının işbirlikçi Dur gerçekleştirir.|  
|[Terminate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Belirtilen çıkış kodu ile işlemi sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `ICorDebugController` olduğundan bir işlem denetleme, kapsam işlemin tüm iş parçacıklarının içerir. Varsa `ICorDebugController` olan uygulama etki alanı denetleme, kapsamı yalnızca bu belirli uygulama etki alanı iş parçacıklarının içerir.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
