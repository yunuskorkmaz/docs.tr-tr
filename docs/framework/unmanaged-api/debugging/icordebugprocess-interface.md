---
title: Icordebugprocess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee526a79d89a9e4e3483daa07a512b6b7f920e70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess-interface1"></a>Icordebugprocess Interface1
Yönetilen bir kodu yürüten bir işlemi temsil eder. Bu arabirim Icordebugcontroller sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Geçerli yönetilmeyen özel durumu verilen iş parçacığı üzerinde temizler.|  
|[EnableLogMessages yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Etkinleştirir ve günlük iletileri için hata ayıklayıcı göndermeyi devre dışı bırakır.|  
|[EnumerateAppDomains yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Tüm uygulama etki alanlarının işleminde numaralandırır.|  
|[EnumerateObjects yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Henüz uygulanmadı.|  
|[GetHandle yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|İşlem için bir tanıtıcı alır.|  
|[Gethelperthreadıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Hata Ayıklayıcı'nın iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı kimliği alır.|  
|[GetID yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|İşlemin işletim sistemi (OS) Kimliğini alır.|  
|[GetObject yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Henüz uygulanmadı.|  
|[GetThread yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Belirtilen işletim sistemi iş parçacığına sahip Icordebugthread örneği alır kimliği|  
|[GetThreadContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Bağlam için verilen iş parçacığı alır.|  
|[Isossuspended yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|İş parçacığı İşlem Durdurma hata ayıklayıcı sonucunda askıya olup olmadığını belirler.|  
|[Istransitionstub yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Bir adresi yönetilen kod geçiş neden olacak bir saplama içinde olup olmadığını belirler.|  
|[ModifyLogSwitch yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Belirtilen günlük anahtar önem derecesi ayarlar.|  
|[ReadMemory yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Bellek işleminden okur.|  
|[SetThreadContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Verilen iş parçacığı bağlamının ayarlar.|  
|[ThreadForFiberCookie yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Kullanım dışı.|  
|[WriteMemory yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|İşlem bellek alanı için veri yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
