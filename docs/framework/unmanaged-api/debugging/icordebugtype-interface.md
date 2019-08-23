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
ms.openlocfilehash: b830af5d59c0eb177d815451ecedbdc14121aaad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964756"
---
# <a name="icordebugtype-interface"></a>ICorDebugType Arabirimi
Temel veya karmaşık (yani Kullanıcı tanımlı) bir türü temsil eder. Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateTypeParameters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<xref:System.Type> Bu`ICorDebugType`tarafından başvurulan sınıfın genel parametrelerine başvuran ICorDebugTypeEnum için bir arabirim işaretçisi alır.|  
|[GetBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Bir tane varsa, bunun `ICorDebugType` `ICorDebugType`başvurduğu sınıfın temel sınıfına başvuran bir arabirim işaretçisi alır.|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Bu `ICorDebugType`bir ICorDebugClass 'ın türü belirtilmiş oluşturucusuna başvuran bir arabirim işaretçisi alır.|  
|[GetFirstTypeParameter Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Tarafından `ICorDebugType` başvurulansınıfın<xref:System.Type> oluşturucusunun ilk genel parametresine başvuran bir arabirim işaretçisi alır. `ICorDebugType`|  
|[GetRank Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Bir dizi türündeki boyut sayısını alır.|  
|[GetStaticFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue için bir arabirim işaretçisi alır.|  
|[GetType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<xref:System.Type> Bunun`ICorDebugType`başvurduğu ortak dil çalışma zamanının yerel türünü açıklayan bir CorElementType değeri alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tür geneldir ise, `ICorDebugClass` örneklenmemiş türü temsil eder. Arabirim `ICorDebugType` , bir örneklenmiş genel türü temsil eder. Örneğin, Hashtable\<K, V > tarafından `ICorDebugClass`temsil edilir, ancak Hashtable\<Int32, String > tarafından `ICorDebugType`temsil edilir.  
  
 Genel olmayan türler hem hem de `ICorDebugClass` `ICorDebugType`ile temsil edilir. İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
