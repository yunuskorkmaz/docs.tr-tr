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
ms.openlocfilehash: 5714597b5e5ca2936aad53217ae934684e75585c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125743"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass Arabirimi

Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür geneldir ise, `ICorDebugClass` örneklenmiş genel türü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Bu sınıfı tanımlayan modülü alır.|  
|[GetStaticFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Belirtilen statik alanın değerini alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Bu sınıf için `TypeDef` meta veri belirtecini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugClass` arabirimi örneği oluşturulmuş bir genel türü temsil eder. ICorDebugType arabirimi bir örneklenmiş genel türü temsil eder. Örneğin, `Hashtable<K, V>` `ICorDebugClass`tarafından temsil edilir, ancak `Hashtable<Int32, String>` `ICorDebugType`tarafından temsil edilir.  
  
 Genel olmayan türler hem `ICorDebugClass` hem de `ICorDebugType`ile temsil edilir. İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
