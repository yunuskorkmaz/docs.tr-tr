---
title: ICorDebugObjectValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: 2a5a618491bf2c624669728d97a690cca315bff8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724682"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue Arabirimi

Bir nesnesi içeren bir değeri temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetClass Yöntemi](icordebugobjectvalue-getclass-method.md)|<xref:System.Type>Bu başvuruda bulunan nesnenin ortak dil çalışma zamanına (CLR) yönelik bir arabirim işaretçisi alır `ICorDebugObjectValue` .|  
|[GetContext Yöntemi](icordebugobjectvalue-getcontext-method.md)|Uygulanmaz.|  
|[GetFieldValue Yöntemi](icordebugobjectvalue-getfieldvalue-method.md)|Belirtilen sınıftaki belirtilen alanın değerini temsil eden bir [ICorDebugValue](icordebugvalue-interface.md) için bir arabirim işaretçisi alır.|  
|[GetManagedCopy Yöntemi](icordebugobjectvalue-getmanagedcopy-method.md)|Kullanımdan kalktı. Bu yöntemi çağırmayın.|  
|[GetVirtualMethod Yöntemi](icordebugobjectvalue-getvirtualmethod-method.md)|Uygulanmaz.|  
|[IsValueClass Yöntemi](icordebugobjectvalue-isvalueclass-method.md)|Bu nesnenin başvurduğu nesnenin bir değer türü olup olmadığını gösteren bir değer alır `ICorDebugObjectValue` .|  
|[SetFromManagedCopy Yöntemi](icordebugobjectvalue-setfrommanagedcopy-method.md)|Kullanımdan kalktı. Bu yöntemi çağırmayın.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugObjectValue`Hata ayıklamakta olan işlem devam edene kadar geçerli kalır.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
