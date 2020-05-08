---
title: ICorDebugExceptionDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: dfa65aa1b63c996068e75ff1165111d5fcfe77eb
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976011"
---
# <a name="icordebugexceptiondebugevent-interface"></a>ICorDebugExceptionDebugEvent Arabirimi
Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetFlags Yöntemi](icordebugexceptiondebugevent-getflags-method.md)|Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.|  
|[GetNativeIP Yöntemi](icordebugexceptiondebugevent-getnativeip-method.md)|Bu özel durum ayıklama olayı için yerel arabirim işaretçisini alır.|  
|[GetStackPointer Yöntemi](icordebugexceptiondebugevent-getstackpointer-method.md)|Bu özel durum ayıklama olayının yığın işaretçisini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugExceptionDebugEvent` Arabirim aşağıdaki olay türleri tarafından uygulanır:  
  
- [MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)  
  
- [MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)  
  
- [MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)  
  
- [MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. .NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
