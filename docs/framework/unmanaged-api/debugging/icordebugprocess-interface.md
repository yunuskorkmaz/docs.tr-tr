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
ms.openlocfilehash: 46d96d66f16cd956d8fab1afe00486d564e37953
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775570"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess Arabirimi
Yönetilen bir kodu yürüten bir işlemi temsil eder. Icordebugcontroller öğesinin arabirimidir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Verilen iş parçacığı üzerinde geçerli yönetilmeyen özel durum temizler.|  
|[EnableLogMessages Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Etkinleştirir ve günlük iletilerini göndermek için hata ayıklayıcı devre dışı bırakır.|  
|[EnumerateAppDomains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Tüm uygulama etki alanlarının işleminde sıralar.|  
|[EnumerateObjects Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Henüz uygulanmadı.|  
|[GetHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|İşlem için bir tanıtıcı alır.|  
|[GetHelperThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Hata Ayıklayıcı'nın iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı Kimliğini alır.|  
|[GetID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|İşletim sistemi (OS) işlem Kimliğini alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Henüz uygulanmadı.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Belirtilen işletim sistemi iş parçacığı Icordebugthread örneği alır kimliği|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Verilen iş parçacığı için bağlamı alır.|  
|[IsOSSuspended Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|İşlem durdurulurken bir hata ayıklayıcı sonucunda iş parçacığını askıya olup olmadığını belirler.|  
|[IsTransitionStub Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Adres yönetilen koda geçiş neden olacak bir saplama içinde olup olmadığını belirler.|  
|[ModifyLogSwitch Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Belirtilen log anahtarı önem düzeyini ayarlar.|  
|[ReadMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Bellek işlemden okur.|  
|[SetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Verilen iş parçacığı bağlamını ayarlar.|  
|[ThreadForFiberCookie Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Kullanım dışı.|  
|[WriteMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Belleği işlemdeki veri yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
