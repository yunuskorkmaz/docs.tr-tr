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
ms.openlocfilehash: 329bcee441b395982a8a8b539c0a938fa8170b14
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894052"
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
 'ndaki Bu sınıf için öğe türünü belirten CorElementType numaralandırması değeri: Bu ICorDebugClass2 bir değer türünü temsil ediyorsa, bu değeri ELEMENT_TYPE_VALUETYPE olarak ayarlayın. Bu `ICorDebugClass2` bir karmaşık türü temsil ediyorsa, bu değeri element_type_class olarak ayarlayın.  
  
 `nTypeArgs`  
 'ndaki Tür genel ise tür parametrelerinin sayısı. Tür parametrelerinin sayısı (varsa), sınıfının gerektirdiği sayıyla eşleşmelidir.  
  
 `ppTypeArgs`  
 'ndaki Her biri bir tür parametresini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi. Sınıf genel değilse, bu değer null olur.  
  
 `ppType`  
 dışı Tür bildirimini temsil eden `ICorDebugType` nesnenin adresine yönelik bir işaretçi. Bu nesne, Yönetilen koddaki bir <xref:System.Type> nesneye eşdeğerdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf genel değilse, diğer bir deyişle, tür parametreleri yoksa, `GetParameterizedType` sınıfa karşılık gelen çalışma zamanı türü nesnesini alır. `elementType` Parametresi, sınıf için doğru öğe türüne ayarlanmalıdır: sınıf bir değer türü ise element_type_valuetype; Aksi takdirde, ELEMENT_TYPE_CLASS.  
  
 Sınıf tür parametrelerini kabul ederse (örneğin, `ArrayList<T>`), gibi `GetParameterizedType` `ArrayList<int>`bir örneklenmiş tür için bir tür nesnesi oluşturmak için kullanabilirsiniz.  
  
## <a name="background-information"></a>Arka Plan Bilgileri  
 1,0 ve 1,1 .NET Framework sürümlerinde, Meta verilerdeki her tür çalışan işlemdeki bir türle doğrudan eşleştirilebilir. Bu nedenle, meta veri türü ve çalışma zamanı türü, çalışan işlemde tek bir gösterimine sahipti. Ancak, Meta verilerdeki bir genel tür, çalışan işlemdeki türdeki birçok farklı örneklememe eşleştirilebilir. Örneğin, meta veri `SortedList<K,V>` türü, `SortedList<String, EmployeeRecord>` `SortedList<Int32, String>` `SortedList<String,Array<Int32>>`,, vb. ile eşlenir. Bu nedenle, tür örnek oluşturmayı işlemek için bir yol gerekir.  
  
 .NET Framework sürüm 2,0 `ICorDebugType` arabirimini tanıtır. Genel bir tür için `ICorDebugClass` , veya `ICorDebugClass2` nesnesi örneklenmiş türü (`SortedList<K,V>`) temsil eder ve bir `ICorDebugType` nesne, çeşitli örneklenmiş türleri temsil eder. Bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi verildiğinde, `ICorDebugType` `ICorDebugClass2::GetParameterizedType` yöntemini çağırarak herhangi bir örnek oluşturma için bir nesne oluşturabilirsiniz. Ayrıca, Int32 gibi basit `ICorDebugType` bir tür için veya genel olmayan bir tür için bir nesne oluşturabilirsiniz.  
  
 Bir türün çalışma zamanı `ICorDebugType` kavramının temsil edilebilmesi için nesnenin GIRIŞ, API 'nin tamamında Ripple etkisine sahiptir. `ICorDebugClass` Daha önce bir `ICorDebugClass2` veya nesnesi veya hatta bir `CorElementType` değeri geçen işlevler, bir `ICorDebugType` nesneyi almak için genelleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
