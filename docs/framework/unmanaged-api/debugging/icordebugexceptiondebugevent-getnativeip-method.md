---
description: ': Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 89bda36efc59e2462634c3d8a3a5835c9d4b3354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693466"
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
  
|Olay türü|Değerin anlamı `pStackPointer`|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Hatalı yönergenin adresi.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Bir özel durum ortaya çıkarılmadığını yürütmenin sürdürüleceği [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçeve içindeki kod adresidir. Özel durum, bir yan tümcenin catch bloğu gibi farklı kodların bu çerçevede yürütülmesi olabilir veya neden olmayabilir `try/catch/finally` .|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|`catch`İşleyici yürütmenin [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçevede başlayacağı kod adresi.|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP` 0 ' dır.|  
  
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
