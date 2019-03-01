---
title: ICorDebugClass Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9beb8930143cbb0cc7dd8dd68a65b42d92563e31
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972059"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass Arabirimi

Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür genelse, `ICorDebugClass` örneklenmemiş genel türü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Bu sınıfı tanımlayan modül alır.|  
|[GetStaticFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Belirtilen statik alan değerini alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Alır `TypeDef` Bu sınıf için meta veri belirteci.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugClass` Arabirimi bir örneklenmemiş genel türü temsil eder. Icordebugtype arabirimi örneklenmiş bir genel türü temsil eder. Örneğin, `Hashtable<K, V>` tarafından temsil edilir `ICorDebugClass`bilgileriyse `Hashtable<Int32, String>` tarafından temsil edilir `ICorDebugType`.  
  
 Genel olmayan türler tarafından temsil edilir `ICorDebugClass` ve `ICorDebugType`. İkinci arabirim tür örneği oluşturmada ile uğraşmak için .NET Framework sürüm 2.0 kullanılmaya başlandı.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
