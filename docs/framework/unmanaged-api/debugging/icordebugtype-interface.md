---
title: ICorDebugType Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74863af1096f8600b8095e593c1f3c820c512e9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166809"
---
# <a name="icordebugtype-interface"></a>ICorDebugType Arabirimi
(Kullanıcı tanımlı olan) bir türü, basit veya karmaşık temsil eder. Tür genelse, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateTypeParameters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Genel başvuran bir Icordebugtypeenum bir arabirim işaretçisi alır <xref:System.Type> bu tarafından başvurulan sınıfın parametrelerinin `ICorDebugType`.|  
|[GetBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Bir arabirim işaretçisi alır bir `ICorDebugType` bu tarafından başvurulan sınıfın temel sınıfına başvuran `ICorDebugType`, varsa.|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Bu yazılı oluşturucusuna başvuran bir Icordebugclass bir arabirim işaretçisi alır `ICorDebugType`.|  
|[GetFirstTypeParameter Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Bir arabirim işaretçisi alır bir `ICorDebugType` ilk genel başvuran <xref:System.Type> bu tarafından başvurulan sınıfın oluşturucusu için parametresi `ICorDebugType`.|  
|[GetRank Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Bir dizi türü boyut sayısını alır.|  
|[GetStaticFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Bir arabirim işaretçisi için belirtilen alan tarafından başvurulan statik alanı değerini içeren bir Icordebugvalue belirtilen yığın çerçevesinde belirtecini alır.|  
|[GetType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Ortak dil çalışma zamanı yerel türünü açıklayan bir CorElementType değerini alır <xref:System.Type> bu tarafından başvurulan `ICorDebugType`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tür genelse, `ICorDebugClass` örneklenmemiş türü temsil eder. `ICorDebugType` Arabirimi örneklenmiş bir genel türü temsil eder. Örneğin, karma tablosu\<K, V > tarafından temsil edilir `ICorDebugClass`bilgileriyse Hashtable\<Int32, String > tarafından temsil edilir `ICorDebugType`.  
  
 Genel olmayan türler tarafından temsil edilir `ICorDebugClass` ve `ICorDebugType`. İkinci arabirim tür örneği oluşturmada ile uğraşmak için .NET Framework sürüm 2.0 kullanılmaya başlandı.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
