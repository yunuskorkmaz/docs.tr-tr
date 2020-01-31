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
ms.openlocfilehash: e104f8c522af2ee4cd42332b7459f4a2fd185511
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792684"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue Arabirimi

Bir nesnesi içeren bir değeri temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetClass Yöntemi](icordebugobjectvalue-getclass-method.md)|Bu `ICorDebugObjectValue` başvurduğu nesnenin ortak dil çalışma zamanı (CLR) <xref:System.Type> için bir arabirim işaretçisi alır.|  
|[GetContext Yöntemi](icordebugobjectvalue-getcontext-method.md)|Uygulanmadı.|  
|[GetFieldValue Yöntemi](icordebugobjectvalue-getfieldvalue-method.md)|Belirtilen sınıftaki belirtilen alanın değerini temsil eden bir [ICorDebugValue](icordebugvalue-interface.md) için bir arabirim işaretçisi alır.|  
|[GetManagedCopy Yöntemi](icordebugobjectvalue-getmanagedcopy-method.md)|{1&gt;Artık kullanılmıyor.&lt;1} Bu yöntemi çağırmayın.|  
|[GetVirtualMethod Yöntemi](icordebugobjectvalue-getvirtualmethod-method.md)|Uygulanmadı.|  
|[IsValueClass Yöntemi](icordebugobjectvalue-isvalueclass-method.md)|Bu `ICorDebugObjectValue` başvurduğu nesnenin bir değer türü olup olmadığını gösteren bir değer alır.|  
|[SetFromManagedCopy Yöntemi](icordebugobjectvalue-setfrommanagedcopy-method.md)|{1&gt;Artık kullanılmıyor.&lt;1} Bu yöntemi çağırmayın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklamakta olan işlem devam edene kadar `ICorDebugObjectValue` geçerli kalır.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
