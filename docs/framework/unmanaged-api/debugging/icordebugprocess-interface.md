---
title: ICorDebugProcess Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b99630ba60cd84254024b91dba9ef9922fd7e041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943311"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess Arabirimi
Yönetilen bir kodu yürüten bir işlemi temsil eder. Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.|  
|[EnableLogMessages Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Hata ayıklayıcıya günlük iletilerinin gönderilmesini sağlar ve devre dışı bırakır.|  
|[EnumerateAppDomains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|İşlemdeki tüm uygulama etki alanlarını numaralandırır.|  
|[EnumerateObjects Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Uygulanmadı.|  
|[GetHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|İşlem için bir tanıtıcı alır.|  
|[GetHelperThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Hata ayıklayıcının iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.|  
|[GetID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|İşlemin işletim sistemi (OS) KIMLIĞINI alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Uygulanmadı.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Belirtilen işletim sistemi iş parçacığı KIMLIĞINE sahip ICorDebugThread örneğini alır.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Verilen iş parçacığının bağlamını alır.|  
|[IsOSSuspended Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Hata ayıklayıcının işlemi durdurmasının bir sonucu olarak iş parçacığının askıya alınıp alınmadığını belirler.|  
|[IsTransitionStub Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını belirler.|  
|[ModifyLogSwitch Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Belirtilen günlük anahtarının önem derecesini ayarlar.|  
|[ReadMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|İşlemden belleği okur.|  
|[SetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Verilen iş parçacığının bağlamını ayarlar.|  
|[ThreadForFiberCookie Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Kullanım dışı.|  
|[WriteMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|İşlemdeki bir bellek alanına veri yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
