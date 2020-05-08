---
title: 'Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 4f84183dfc23ebc0d0fee9feeb21329c217b9cca
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976024"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi
Bu özel durum ayıklama olayının yığın işaretçisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStackPointer`  
 dışı Bu özel durum ayıklama olayı için yığın işaretçisinin adresine yönelik bir işaretçi. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yığın işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.  
  
|Olay türü|`pStackPointer` Değerin anlamı|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Özel durumu oluşturan çerçeve için yığın işaretçisi.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Kullanıcı kodu çerçevesinin yığın işaretçisi, oluşturulan özel durumun noktasına en yakın.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|Catch işleyicisini içeren çerçeve için yığın işaretçisi.|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pStackPointer`**null**.|  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
 Olay türü [ıcordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugExceptionDebugEvent Arabirimi](icordebugexceptiondebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
