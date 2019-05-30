---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52a58f75ca7abd1bd1f871bcf4637bfd7eb7bdcd
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300538"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]  
  
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
