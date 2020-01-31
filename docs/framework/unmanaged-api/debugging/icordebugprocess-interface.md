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
ms.openlocfilehash: b2429052173a187297b67c756213e5d27a79298b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792598"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess Arabirimi
Yönetilen bir kodu yürüten bir işlemi temsil eder. Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](icordebugprocess-clearcurrentexception-method.md)|Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.|  
|[EnableLogMessages Yöntemi](icordebugprocess-enablelogmessages-method.md)|Hata ayıklayıcıya günlük iletilerinin gönderilmesini sağlar ve devre dışı bırakır.|  
|[EnumerateAppDomains Yöntemi](icordebugprocess-enumerateappdomains-method.md)|İşlemdeki tüm uygulama etki alanlarını numaralandırır.|  
|[EnumerateObjects Yöntemi](icordebugprocess-enumerateobjects-method.md)|Uygulanmadı.|  
|[GetHandle Yöntemi](icordebugprocess-gethandle-method.md)|İşlem için bir tanıtıcı alır.|  
|[GetHelperThreadID Yöntemi](icordebugprocess-gethelperthreadid-method.md)|Hata ayıklayıcının iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.|  
|[GetID Yöntemi](icordebugprocess-getid-method.md)|İşlemin işletim sistemi (OS) KIMLIĞINI alır.|  
|[GetObject Yöntemi](icordebugprocess-getobject-method.md)|Uygulanmadı.|  
|[GetThread Yöntemi](icordebugprocess-getthread-method.md)|Belirtilen işletim sistemi iş parçacığı KIMLIĞINE sahip ICorDebugThread örneğini alır.|  
|[GetThreadContext Yöntemi](icordebugprocess-getthreadcontext-method.md)|Verilen iş parçacığının bağlamını alır.|  
|[IsOSSuspended Yöntemi](icordebugprocess-isossuspended-method.md)|Hata ayıklayıcının işlemi durdurmasının bir sonucu olarak iş parçacığının askıya alınıp alınmadığını belirler.|  
|[IsTransitionStub Yöntemi](icordebugprocess-istransitionstub-method.md)|Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını belirler.|  
|[ModifyLogSwitch Yöntemi](icordebugprocess-modifylogswitch-method.md)|Belirtilen günlük anahtarının önem derecesini ayarlar.|  
|[ReadMemory Yöntemi](icordebugprocess-readmemory-method.md)|İşlemden belleği okur.|  
|[SetThreadContext Yöntemi](icordebugprocess-setthreadcontext-method.md)|Verilen iş parçacığının bağlamını ayarlar.|  
|[ThreadForFiberCookie Yöntemi](icordebugprocess-threadforfibercookie-method.md)|Kullanım dışı.|  
|[WriteMemory Yöntemi](icordebugprocess-writememory-method.md)|İşlemdeki bir bellek alanına veri yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
