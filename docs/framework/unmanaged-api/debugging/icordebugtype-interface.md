---
title: Icordebugtype Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 503d0debef2ec1bebd674234051db8101dcb0de2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype-interface1"></a>Icordebugtype Interface1
(Kullanıcı tanımlı olan) bir türü, temel veya karmaşık temsil eder. Tür genel, ise `ICorDebugType` oluşturulmuş genel türünü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateTypeParameters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Arabirim işaretçisi genel başvuruda bulunan bir Icordebugtypeenum alır <xref:System.Type> bu tarafından başvurulan sınıfı parametrelerinin `ICorDebugType`.|  
|[GetBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Bir arabirim işaretçisi alır bir `ICorDebugType` bu tarafından başvurulan sınıfın temel sınıf başvuran `ICorDebugType`, varsa.|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Bu yazılan Oluşturucusu başvuruda bulunan bir Icordebugclass arabirimi işaretçisi alır `ICorDebugType`.|  
|[GetFirstTypeParameter Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Bir arabirim işaretçisi alır bir `ICorDebugType` ilk genel başvuran <xref:System.Type> parametresi bu tarafından başvurulan sınıf için `ICorDebugType`.|  
|[GetRank Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Dimensions sayısı bir dizi türünü alır.|  
|[GetStaticFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Arabirim işaretçisi belirtilen alanı tarafından başvurulan statik alanın değerini içeren bir Icordebugvalue için belirtilen yığın çerçevesinde belirtecini alır.|  
|[GetType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Ortak dil çalışma zamanı yerel türünü tanımlayan bir CorElementType değeri alır <xref:System.Type> bu tarafından başvurulan `ICorDebugType`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tür genel, ise `ICorDebugClass` dizilerine türünü temsil eder. `ICorDebugType` Arabirimi bir oluşturulmuş genel tür temsil eder. Örneğin, Hashtable\<K, V > gösterdiği `ICorDebugClass`, ancak Hashtable\<Int32, dize > gösterdiği `ICorDebugType`.  
  
 Olmayan genel türleri temsil edilen her ikisi için de `ICorDebugClass` ve `ICorDebugType`. İkinci arabirim türü örnek oluşturma ile mücadele etmek için .NET Framework sürüm 2.0 sunulmuştur.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
