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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475647"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType Yöntemi
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
  
## <a name="parameters"></a>Parametreler  
 `elementType`  
 [in] Bu sınıf için öğe türü belirtir CorElementType sabit listesi değeri: Bu Icordebugclass2 bir değer türü temsil ediyorsa ELEMENT_TYPE_VALUETYPE için bu değeri ayarlayın. Bu değer için ELEMENT_TYPE_CLASS bu verilirse `ICorDebugClass2` karmaşık bir türü temsil eder.  
  
 `nTypeArgs`  
 [in] Tür genelse, tür parametreleri, sayısı. Tür parametreleri (varsa) sayısı, sınıf tarafından gerekli numarası aynı olmalıdır.  
  
 `ppTypeArgs`  
 [in] Bir dizi işaretçileri, her biri bir tür parametresini temsil eden bir Icordebugtype nesneye işaret eder. Genel olmayan sınıf ise bu değer null olur.  
  
 `ppType`  
 [out] Adresine bir işaretçi bir `ICorDebugType` türü bildirimini temsil eden nesne. Bu nesne değerine eşdeğer olan bir <xref:System.Type> yönetilen kodda nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Hiçbir tür parametreleri varsa, sınıf başka bir deyişle, genel olmayan, ise `GetParameterizedType` yalnızca sınıfına karşılık gelen çalışma zamanı tür nesnesi alır. `elementType` Parametre sınıfı için doğru öğe türü ayarlanmalıdır: Sınıf bir değer türü ise ELEMENT_TYPE_VALUETYPE; Aksi takdirde, ELEMENT_TYPE_CLASS.  
  
 Sınıf türü parametreleri kabul ediyorsa (örneğin, `ArrayList<T>`), kullanabileceğiniz `GetParameterizedType` gibi örneklenmiş bir tür için bir tür nesnesi oluşturmak için `ArrayList<int>`.  
  
## <a name="background-information"></a>Arka plan bilgileri  
 .NET Framework sürüm 1.0 ve 1.1, her tür meta verilerinde doğrudan bir çalışan işlem türüne eşleştirilebilir. Bu nedenle, bir meta veri türü ve çalışma zamanı türü tek bir gösterimiyse çalışan işleminde vardı. Ancak, bir genel tür meta verilerinde birçok farklı örneklemeleri çalışan işlemindeki türü eşlenebilir. Örneğin, meta veri türü `SortedList<K,V>` eşleyebilirsiniz `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`ve benzeri. Bu nedenle, tür örneği oluşturmada işlemek için bir yol gerekir.  
  
 .NET Framework sürüm 2.0 tanıtır `ICorDebugType` arabirimi. Genel bir tür için bir `ICorDebugClass` veya `ICorDebugClass2` nesne örneklenmemiş türü temsil eder (`SortedList<K,V>`) ve bir `ICorDebugType` nesne örneklenmiş çeşitli temsil eder. Verilen bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi oluşturmak için kullanabileceğiniz bir `ICorDebugType` çağırarak tüm örneklemesi için nesne `ICorDebugClass2::GetParameterizedType` yöntemi. Ayrıca oluşturabileceğiniz bir `ICorDebugType` Int32 gibi basit bir tür için veya genel olmayan bir tür için bir nesne.  
  
 Giriş `ICorDebugType` bir tür çalışma zamanı kavramını temsil etmek için nesnesi API boyunca bir dalgalanma etkisine sahiptir. Daha önce geçen işlevler bir `ICorDebugClass` veya `ICorDebugClass2` nesne veya hatta bir `CorElementType` değeri genelleştirilmiş gerçekleştirilecek bir `ICorDebugType` nesne.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
