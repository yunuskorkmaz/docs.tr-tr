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
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396697"
---
# <a name="icordebugtype-interface"></a>ICorDebugType Arabirimi
Temel veya karmaşık (yani Kullanıcı tanımlı) bir türü temsil eder. Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateTypeParameters Yöntemi](icordebugtype-enumeratetypeparameters-method.md)|Bu tarafından başvurulan sınıfın genel parametrelerine başvuran ICorDebugTypeEnum için bir arabirim işaretçisi alır <xref:System.Type> `ICorDebugType` .|  
|[GetBase Yöntemi](icordebugtype-getbase-method.md)|Bir `ICorDebugType` tane varsa, bunun başvurduğu sınıfın temel sınıfına başvuran bir arabirim işaretçisi alır `ICorDebugType` .|  
|[GetClass Yöntemi](icordebugtype-getclass-method.md)|Bu bir ICorDebugClass 'ın türü belirtilmiş oluşturucusuna başvuran bir arabirim işaretçisi alır `ICorDebugType` .|  
|[GetFirstTypeParameter Yöntemi](icordebugtype-getfirsttypeparameter-method.md)|`ICorDebugType` <xref:System.Type> Tarafından başvurulan sınıfın oluşturucusunun ilk genel parametresine başvuran bir arabirim işaretçisi alır `ICorDebugType` .|  
|[GetRank Yöntemi](icordebugtype-getrank-method.md)|Bir dizi türündeki boyut sayısını alır.|  
|[GetStaticFieldValue Yöntemi](icordebugtype-getstaticfieldvalue-method.md)|Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue için bir arabirim işaretçisi alır.|  
|[GetType Yöntemi](icordebugtype-gettype-method.md)|Bunun başvurduğu ortak dil çalışma zamanının yerel türünü açıklayan bir CorElementType değeri alır <xref:System.Type> `ICorDebugType` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Tür geneldir ise, `ICorDebugClass` örneklenmemiş türü temsil eder. `ICorDebugType`Arabirim, bir örneklenmiş genel türü temsil eder. Örneğin, Hashtable \< K, V> tarafından temsil edilir `ICorDebugClass` , ancak Hashtable \< ınt32, String> tarafından temsil edilir `ICorDebugType` .  
  
 Genel olmayan türler hem hem de ile temsil `ICorDebugClass` edilir `ICorDebugType` . İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
