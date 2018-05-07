---
title: ICorDebugClass2::GetParameterizedType Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a5b3a28c7250a16e78e199bceff7c9e64517319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType Metodu
Bu sınıf türü bildirimi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `elementType`  
 [in] Bu sınıf öğesi türünü belirtir CorElementType numaralandırması değerini: değer türü bu Icordebugclass2 temsil ediyorsa ELEMENT_TYPE_VALUETYPE için bu değeri ayarlayın. Bu değer için ELEMENT_TYPE_CLASS bu ayarlamanız `ICorDebugClass2` karmaşık bir türü temsil eder.  
  
 `nTypeArgs`  
 [in] Tür parametreleri, genel bir tür ise sayısı. Tür parametreleri (varsa) sayısı sınıfı tarafından gerekli numarası aynı olmalıdır.  
  
 `ppTypeArgs`  
 [in] Her biri bir tür parametresi temsil eden bir Icordebugtype bir nesneye işaret etmiyor dizisi işaretçisi. Sınıf genel olmayan ise, bu değer null olur.  
  
 `ppType`  
 [out] Adresine bir işaretçi bir `ICorDebugType` türü bildirimi temsil eden nesne. Bu nesne eşdeğer olan bir <xref:System.Type> yönetilen kodda nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Hiçbir tür parametreleri varsa sınıf başka bir deyişle, genel olmayan, ise `GetParameterizedType` yalnızca sınıfına karşılık gelen çalışma zamanı tür nesnesi alır. `elementType` Parametresi, sınıf için doğru öğe türü için ayarlanmalıdır: sınıf bir değer türü; ise ELEMENT_TYPE_VALUETYPE Aksi takdirde ELEMENT_TYPE_CLASS.  
  
 Tür parametreleri sınıfı kabul ediyorsa (örneğin, `ArrayList<T>`), kullanabileceğiniz `GetParameterizedType` gibi örneklenen türü için bir tür nesnesi oluşturmak için `ArrayList<int>`.  
  
## <a name="background-information"></a>Arka plan bilgileri  
 .NET Framework sürüm 1.0 ve 1.1, her tür meta verileri doğrudan çalışan işlemindeki bir türe eşleştirilebilir. Bu nedenle, meta veri türü ve bir çalışma zamanı türü tek bir gösterimi çalışan işlemde vardı. Ancak, bir genel tür meta verilerde birçok farklı örneklemesi çalışan işlemindeki türü eşlenebilir. Örneğin, meta veri türü `SortedList<K,V>` eşleyebilirsiniz `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`ve benzeri. Bu nedenle, türü örnek oluşturma işlemek için bir yönteme ihtiyacınız vardır.  
  
 .NET Framework sürüm 2.0 tanıtır `ICorDebugType` arabirimi. Genel bir tür için bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi dizilerine türünü temsil eder (`SortedList<K,V>`) ve bir `ICorDebugType` nesnesi çeşitli örneklenen türleri temsil eder. Verilen bir `ICorDebugClass` veya `ICorDebugClass2` nesne oluşturabileceğiniz bir `ICorDebugType` nesne çağırarak tüm örnek oluşturma için `ICorDebugClass2::GetParameterizedType` yöntemi. Ayrıca bir `ICorDebugType` Nesne Int32 gibi basit bir tür veya genel olmayan bir tür.  
  
 Giriş `ICorDebugType` nesne türü çalışma zamanı kavramını göstermek için API boyunca ripple etkisi vardır. Daha önce geçen işlevleri bir `ICorDebugClass` veya `ICorDebugClass2` nesne ve hatta bir `CorElementType` değeri yapılacak genelleştirilmiş bir `ICorDebugType` nesnesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
