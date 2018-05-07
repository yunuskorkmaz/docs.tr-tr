---
title: Icordebugprocess Interface1
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
ms.openlocfilehash: 06e4e3854a850c9639e93c8db2ec8ccd567b242b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess-interface1"></a>Icordebugprocess Interface1
Yönetilen bir kodu yürüten bir işlemi temsil eder. Bu arabirim Icordebugcontroller sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Geçerli yönetilmeyen özel durumu verilen iş parçacığı üzerinde temizler.|  
|[EnableLogMessages Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Etkinleştirir ve günlük iletileri için hata ayıklayıcı göndermeyi devre dışı bırakır.|  
|[EnumerateAppDomains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Tüm uygulama etki alanlarının işleminde numaralandırır.|  
|[EnumerateObjects Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Henüz uygulanmadı.|  
|[GetHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|İşlem için bir tanıtıcı alır.|  
|[GetHelperThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Hata Ayıklayıcı'nın iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı kimliği alır.|  
|[GetID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|İşlemin işletim sistemi (OS) Kimliğini alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Henüz uygulanmadı.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Belirtilen işletim sistemi iş parçacığına sahip Icordebugthread örneği alır kimliği|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Bağlam için verilen iş parçacığı alır.|  
|[IsOSSuspended Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|İş parçacığı İşlem Durdurma hata ayıklayıcı sonucunda askıya olup olmadığını belirler.|  
|[IsTransitionStub Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Bir adresi yönetilen kod geçiş neden olacak bir saplama içinde olup olmadığını belirler.|  
|[ModifyLogSwitch Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Belirtilen günlük anahtar önem derecesi ayarlar.|  
|[ReadMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Bellek işleminden okur.|  
|[SetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Verilen iş parçacığı bağlamının ayarlar.|  
|[ThreadForFiberCookie Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Kullanım dışı.|  
|[WriteMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|İşlem bellek alanı için veri yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
