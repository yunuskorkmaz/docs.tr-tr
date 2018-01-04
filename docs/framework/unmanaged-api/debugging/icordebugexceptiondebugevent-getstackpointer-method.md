---
title: "ICorDebugExceptionDebugEvent::GetStackPointer yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b9096bbb494036156a528d8f9e940630f555f6a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>ICorDebugExceptionDebugEvent::GetStackPointer yöntemi
Yığın işaretçisi için bu özel durum hata ayıklama olayı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStackPointer`  
 [out] Bu özel durumun yığın işaretçisi adresini gösteren bir işaretçi olay hata ayıklama. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yığın işaretçisi anlamı, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.  
  
|Olay türü|Anlamını `pStackPointer` değeri|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Özel durum oluşturdu çerçeve yığın işaretçisi.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Oluşturulan özel durum noktasına yakın kullanıcı kodu çerçeve yığın işaretçisi.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Catch işleyicisi içeren çerçeveyi yığın işaretçisi.|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pStackPointer`olan **null**.|  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
 Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugExceptionDebugEvent Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
