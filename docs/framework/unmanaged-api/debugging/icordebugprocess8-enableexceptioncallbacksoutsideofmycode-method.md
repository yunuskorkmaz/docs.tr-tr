---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08937e87b8bd2249b8608f8ec1ed1f7734961b3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948570"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
[Desteklenen [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] ve sonraki sürümlerinde]  
  
 Etkinleştirir veya belirli türlerdeki devre dışı bırakır [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalarını.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `enableExceptionsOutsideOfJMC` olduğu `false`:  
  
- DEBUG_EXCEPTION_FIRST_CHANCE özel durumu bir geri çağırma içinde hata ayıklayıcıya neden olmaz.  
  
- Varsa özel durumun hiç kullanıcı kodu çıkışları DEBUG_EXCEPTION_CATCH_HANDLER_FOUND özel durum geri aramada hata ayıklayıcıyı oluşturmayacaktır (diğer bir deyişle, bir özel durum işleyicisi bir özel durum kaynaktan yolunu JustMyCode ya da JMC işaretlenmiş bir yöntemi yok).  
  
 Varsayılan değer olan `enableExceptionsOutsideOfJMC` olduğu `true`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess8 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
