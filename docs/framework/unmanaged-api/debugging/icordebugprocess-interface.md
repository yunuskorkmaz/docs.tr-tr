---
description: ': ICorDebugProcess arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7172ee12bf450235db1c18601c8ff7de51435520
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746795"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess Arabirimi

Yönetilen bir kodu yürüten bir işlemi temsil eder. Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](icordebugprocess-clearcurrentexception-method.md)|Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.|  
|[EnableLogMessages Yöntemi](icordebugprocess-enablelogmessages-method.md)|Hata ayıklayıcıya günlük iletilerinin gönderilmesini sağlar ve devre dışı bırakır.|  
|[EnumerateAppDomains Yöntemi](icordebugprocess-enumerateappdomains-method.md)|İşlemdeki tüm uygulama etki alanlarını numaralandırır.|  
|[EnumerateObjects Yöntemi](icordebugprocess-enumerateobjects-method.md)|Uygulanmaz.|  
|[GetHandle Yöntemi](icordebugprocess-gethandle-method.md)|İşlem için bir tanıtıcı alır.|  
|[GetHelperThreadID Yöntemi](icordebugprocess-gethelperthreadid-method.md)|Hata ayıklayıcının iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.|  
|[GetID Yöntemi](icordebugprocess-getid-method.md)|İşlemin işletim sistemi (OS) KIMLIĞINI alır.|  
|[GetObject Metodu](icordebugprocess-getobject-method.md)|Uygulanmaz.|  
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

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
