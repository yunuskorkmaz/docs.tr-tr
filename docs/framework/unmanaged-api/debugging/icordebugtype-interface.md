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
ms.openlocfilehash: 4f3f553ed5dc93433610365e0dae5bee54863de5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129620"
---
# <a name="icordebugtype-interface"></a>ICorDebugType Arabirimi
Temel veya karmaşık (yani Kullanıcı tanımlı) bir türü temsil eder. Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateTypeParameters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Bu `ICorDebugType`tarafından başvurulan sınıfın genel <xref:System.Type> parametrelerine başvuran bir ICorDebugTypeEnum için bir arabirim işaretçisi alır.|  
|[GetBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Bu `ICorDebugType`tarafından başvurulan sınıfın temel sınıfına başvuran bir `ICorDebugType` için bir arabirim işaretçisi alır, varsa.|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Bu `ICorDebugType`türü belirtilmiş oluşturucuya başvuran bir ICorDebugClass için bir arabirim işaretçisi alır.|  
|[GetFirstTypeParameter Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Bu `ICorDebugType`tarafından başvurulan sınıfın oluşturucusunun ilk genel <xref:System.Type> parametresine başvuran bir `ICorDebugType` için bir arabirim işaretçisi alır.|  
|[GetRank Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Bir dizi türündeki boyut sayısını alır.|  
|[GetStaticFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue için bir arabirim işaretçisi alır.|  
|[GetType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Bu `ICorDebugType`başvurduğu ortak dil çalışma zamanının yerel türünü tanımlayan bir CorElementType değeri alır <xref:System.Type>.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tür geneldir ise `ICorDebugClass` örneklenmiş türü temsil eder. `ICorDebugType` arabirimi bir örneklenmiş genel türü temsil eder. Örneğin, Hashtable\<K, V > `ICorDebugClass`tarafından temsil edilebilir, ancak Hashtable\<Int32, String > ise `ICorDebugType`olarak temsil edilir.  
  
 Genel olmayan türler hem `ICorDebugClass` hem de `ICorDebugType`ile temsil edilir. İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
