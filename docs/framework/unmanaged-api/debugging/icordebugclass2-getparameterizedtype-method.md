---
title: ICorDebugClass2::GetParameterizedType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
ms.openlocfilehash: 64537ab97c1256cc6f963999b027bafc25cbbccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125738"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType Yöntemi
Bu sınıf için tür bildirimini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `elementType`  
 'ndaki Bu sınıf için öğe türünü belirten CorElementType numaralandırması değeri: Bu ICorDebugClass2 bir değer türünü temsil ediyorsa, bu değeri ELEMENT_TYPE_VALUETYPE olarak ayarlayın. Bu `ICorDebugClass2` karmaşık bir türü temsil ediyorsa, bu değeri ELEMENT_TYPE_CLASS olarak ayarlayın.  
  
 `nTypeArgs`  
 'ndaki Tür genel ise tür parametrelerinin sayısı. Tür parametrelerinin sayısı (varsa), sınıfının gerektirdiği sayıyla eşleşmelidir.  
  
 `ppTypeArgs`  
 'ndaki Her biri bir tür parametresini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi. Sınıf genel değilse, bu değer null olur.  
  
 `ppType`  
 dışı Tür bildirimini temsil eden bir `ICorDebugType` nesnesinin adresine yönelik bir işaretçi. Bu nesne, Yönetilen koddaki <xref:System.Type> nesnesine eşdeğerdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf genel değilse, yani tür parametreleri yoksa, `GetParameterizedType` yalnızca sınıfa karşılık gelen çalışma zamanı türü nesnesini alır. Sınıf bir değer türünde ise `elementType` parametresi, sınıf için doğru öğe türüne ayarlanmalıdır: ELEMENT_TYPE_VALUETYPE; Aksi takdirde, ELEMENT_TYPE_CLASS.  
  
 Sınıf tür parametrelerini kabul ediyorsa (örneğin, `ArrayList<T>`), `ArrayList<int>`gibi bir örneklenmiş tür için bir tür nesnesi oluşturmak üzere `GetParameterizedType` kullanabilirsiniz.  
  
## <a name="background-information"></a>Arka Plan Bilgileri  
 1,0 ve 1,1 .NET Framework sürümlerinde, Meta verilerdeki her tür çalışan işlemdeki bir türle doğrudan eşleştirilebilir. Bu nedenle, meta veri türü ve çalışma zamanı türü, çalışan işlemde tek bir gösterimine sahipti. Ancak, Meta verilerdeki bir genel tür, çalışan işlemdeki türdeki birçok farklı örneklememe eşleştirilebilir. Örneğin, `SortedList<K,V>` meta veri türü `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`vb. ile eşleyebilirsiniz. Bu nedenle, tür örnek oluşturmayı işlemek için bir yol gerekir.  
  
 .NET Framework sürüm 2,0 `ICorDebugType` arabirimini tanıtır. Genel bir tür için, bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi örneklenmiş türü (`SortedList<K,V>`) temsil eder ve bir `ICorDebugType` nesnesi çeşitli örneklenmiş türleri temsil eder. `ICorDebugClass` veya `ICorDebugClass2` nesnesi verildiğinde, `ICorDebugClass2::GetParameterizedType` yöntemini çağırarak herhangi bir örnekleme için `ICorDebugType` nesnesi oluşturabilirsiniz. Ayrıca, Int32 gibi basit bir tür için veya genel olmayan bir tür için `ICorDebugType` bir nesne oluşturabilirsiniz.  
  
 Bir türün çalışma zamanı kavramının temsil edilebilmesi için `ICorDebugType` nesnesine giriş, API 'nin tamamında Ripple etkisine sahiptir. Daha önce bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi geçen veya hatta `CorElementType` değeri `ICorDebugType` bir nesne almak için genelleştirilmiş işlevlerdir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
