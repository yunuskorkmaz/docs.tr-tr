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
ms.openlocfilehash: 139181975d16c2cdacec10ed646cfc2b8fb31a20
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718000"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType Yöntemi

Bu sınıf için tür bildirimini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Bu sınıf için öğe türünü belirten CorElementType numaralandırması değeri: Bu ICorDebugClass2 bir değer türünü temsil ediyorsa, bu değeri ELEMENT_TYPE_VALUETYPE olarak ayarlayın. Bu bir karmaşık türü temsil ediyorsa, bu değeri ELEMENT_TYPE_CLASS olarak ayarlayın `ICorDebugClass2` .  
  
 `nTypeArgs`  
 'ndaki Tür genel ise tür parametrelerinin sayısı. Tür parametrelerinin sayısı (varsa), sınıfının gerektirdiği sayıyla eşleşmelidir.  
  
 `ppTypeArgs`  
 'ndaki Her biri bir tür parametresini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi. Sınıf genel değilse, bu değer null olur.  
  
 `ppType`  
 dışı `ICorDebugType` Tür bildirimini temsil eden nesnenin adresine yönelik bir işaretçi. Bu nesne, <xref:System.Type> Yönetilen koddaki bir nesneye eşdeğerdir.  
  
## <a name="remarks"></a>Açıklamalar  

 Sınıf genel değilse, diğer bir deyişle, tür parametreleri yoksa, `GetParameterizedType` sınıfa karşılık gelen çalışma zamanı türü nesnesini alır. Parametre, sınıf `elementType` için doğru öğe türüne ayarlanmalıdır: element_type_valuetype sınıf bir değer türüdür; Aksi takdirde, element_type_class.  
  
 Sınıf tür parametrelerini kabul ederse (örneğin, `ArrayList<T>` ), `GetParameterizedType` gibi bir örneklenmiş tür için bir tür nesnesi oluşturmak için kullanabilirsiniz `ArrayList<int>` .  
  
## <a name="background-information"></a>Arka Plan Bilgileri  

 1,0 ve 1,1 .NET Framework sürümlerinde, Meta verilerdeki her tür çalışan işlemdeki bir türle doğrudan eşleştirilebilir. Bu nedenle, meta veri türü ve çalışma zamanı türü, çalışan işlemde tek bir gösterimine sahipti. Ancak, Meta verilerdeki bir genel tür, çalışan işlemdeki türdeki birçok farklı örneklememe eşleştirilebilir. Örneğin, meta veri türü,,, vb `SortedList<K,V>` . ile eşlenir `SortedList<String, EmployeeRecord>` `SortedList<Int32, String>` `SortedList<String,Array<Int32>>` . Bu nedenle, tür örnek oluşturmayı işlemek için bir yol gerekir.  
  
 .NET Framework sürüm 2,0 `ICorDebugType` arabirimini tanıtır. Genel bir tür için, `ICorDebugClass` veya `ICorDebugClass2` nesnesi örneklenmiş türü () temsil eder `SortedList<K,V>` ve bir nesne, `ICorDebugType` çeşitli örneklenmiş türleri temsil eder. Bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi verildiğinde, `ICorDebugType` yöntemini çağırarak herhangi bir örnek oluşturma için bir nesne oluşturabilirsiniz `ICorDebugClass2::GetParameterizedType` . Ayrıca `ICorDebugType` , Int32 gibi basit bir tür için veya genel olmayan bir tür için bir nesne oluşturabilirsiniz.  
  
 `ICorDebugType`Bir türün çalışma zamanı kavramının temsil edilebilmesi için nesnenin giriş, API 'nin tamamında Ripple etkisine sahiptir. Daha önce bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi veya hatta bir değeri geçen işlevler `CorElementType` , bir nesneyi almak için genelleştirilir `ICorDebugType` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
