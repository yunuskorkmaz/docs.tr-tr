---
title: 'Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788679"
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
  
|Olay türü|`pStackPointer` değerinin anlamı|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Hatalı yönergenin adresi.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Bir özel durum ortaya çıkarılmadığını yürütmenin sürdürüleceği [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçeve içindeki kod adresidir. Özel durum, `try/catch/finally` yan tümcesinin catch bloğu gibi farklı kodların bu çerçevede yürütülmesi olabilir veya neden olmayabilir.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|`catch` Handler yürütmesinin, [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçevede başlayacağı kod adresi.|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP` 0 ' dır.|  
  
 Olay türü [ıcordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugExceptionDebugEvent Arabirimi](icordebugexceptiondebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
