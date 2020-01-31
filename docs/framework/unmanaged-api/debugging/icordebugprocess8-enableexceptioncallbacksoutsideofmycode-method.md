---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 2c0da899b3f6f3c229c6f5e5b4cafe48fdc19742
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792165"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
[.NET Framework 4,6 ve sonraki sürümlerde desteklenir]  
  
 Belirli [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri çağırmaları türlerini etkinleştirilir veya devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `enableExceptionsOutsideOfJMC`  
 'ndaki  
  
## <a name="remarks"></a>Açıklamalar  
 `enableExceptionsOutsideOfJMC` değeri `false`:  
  
- DEBUG_EXCEPTION_FIRST_CHANCE bir özel durum, hata ayıklayıcıya geri çağırmaya neden olmaz.  
  
- Özel durum Kullanıcı koduna hiçbir şekilde (bir özel durum kaynağından bir özel durum işleyicisine yönelik yol olarak işaretlenen hiçbir yöntem içermez), bir DEBUG_EXCEPTION_CATCH_HANDLER_FOUND özel durum hata ayıklayıcıya geri çağırmaya neden olmaz.  
  
 `enableExceptionsOutsideOfJMC` varsayılan değeri `true`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess8 Arabirimi](icordebugprocess8-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
