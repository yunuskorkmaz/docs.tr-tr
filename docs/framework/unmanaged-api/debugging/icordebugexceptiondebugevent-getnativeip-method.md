---
title: 'Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 82dc892f3081c9f33ff7a2f363c326091f7cf039
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976037"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi
Bu özel durum ayıklama olayı için yerel yönerge işaretçisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pIP`  
 dışı Bu özel durum ayıklama olayı için yönerge işaretçisine yönelik bir işaretçi. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yönerge işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.  
  
|Olay türü|`pStackPointer` Değerin anlamı|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Hatalı yönergenin adresi.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Bir özel durum ortaya çıkarılmadığını yürütmenin sürdürüleceği [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçeve içindeki kod adresidir. Özel durum, bir `try/catch/finally` yan tümcenin catch bloğu gibi farklı kodların bu çerçevede yürütülmesi olabilir veya neden olmayabilir.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|`catch` Işleyici yürütmenin [getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçevede başlayacağı kod adresi.|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP`0 ' dır.|  
  
 Olay türü [ıcordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugExceptionDebugEvent Arabirimi](icordebugexceptiondebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
