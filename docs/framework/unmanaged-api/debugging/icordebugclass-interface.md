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
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784162"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass Arabirimi

Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder. Tür geneldir ise, `ICorDebugClass` örneklenmiş genel türü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetModule Yöntemi](icordebugclass-getmodule-method.md)|Bu sınıfı tanımlayan modülü alır.|  
|[GetStaticFieldValue Yöntemi](icordebugclass-getstaticfieldvalue-method.md)|Belirtilen statik alanın değerini alır.|  
|[GetToken Yöntemi](icordebugclass-gettoken-method.md)|Bu sınıf için `TypeDef` meta veri belirtecini alır.|  
  
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

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
