---
title: ICorDebugClass2::GetParameterizedType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.GetParameterizedType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9cbb755bd8f52482f7eece6e9d236f29cadc419
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="c1fdc-102">ICorDebugClass2::GetParameterizedType Metodu</span><span class="sxs-lookup"><span data-stu-id="c1fdc-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="c1fdc-103">Bu sınıf türü bildirimi alır.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1fdc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1fdc-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1fdc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1fdc-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="c1fdc-106">[in] Bu sınıf öğesi türünü belirtir CorElementType numaralandırması değerini: değer türü bu Icordebugclass2 temsil ediyorsa ELEMENT_TYPE_VALUETYPE için bu değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="c1fdc-107">Bu değer için ELEMENT_TYPE_CLASS bu ayarlamanız `ICorDebugClass2` karmaşık bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="c1fdc-108">[in] Tür parametreleri, genel bir tür ise sayısı.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="c1fdc-109">Tür parametreleri (varsa) sayısı sınıfı tarafından gerekli numarası aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="c1fdc-110">[in] Her biri bir tür parametresi temsil eden bir Icordebugtype bir nesneye işaret etmiyor dizisi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="c1fdc-111">Sınıf genel olmayan ise, bu değer null olur.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="c1fdc-112">[out] Adresine bir işaretçi bir `ICorDebugType` türü bildirimi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="c1fdc-113">Bu nesne eşdeğer olan bir <xref:System.Type> yönetilen kodda nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1fdc-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1fdc-114">Remarks</span></span>  
 <span data-ttu-id="c1fdc-115">Hiçbir tür parametreleri varsa sınıf başka bir deyişle, genel olmayan, ise `GetParameterizedType` yalnızca sınıfına karşılık gelen çalışma zamanı tür nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="c1fdc-116">`elementType` Parametresi, sınıf için doğru öğe türü için ayarlanmalıdır: sınıf bir değer türü; ise ELEMENT_TYPE_VALUETYPE Aksi takdirde ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="c1fdc-117">Tür parametreleri sınıfı kabul ediyorsa (örneğin, `ArrayList<T>`), kullanabileceğiniz `GetParameterizedType` gibi örneklenen türü için bir tür nesnesi oluşturmak için `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="c1fdc-118">Arka plan bilgileri</span><span class="sxs-lookup"><span data-stu-id="c1fdc-118">Background Information</span></span>  
 <span data-ttu-id="c1fdc-119">.NET Framework sürüm 1.0 ve 1.1, her tür meta verileri doğrudan çalışan işlemindeki bir türe eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="c1fdc-120">Bu nedenle, meta veri türü ve bir çalışma zamanı türü tek bir gösterimi çalışan işlemde vardı.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="c1fdc-121">Ancak, bir genel tür meta verilerde birçok farklı örneklemesi çalışan işlemindeki türü eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="c1fdc-122">Örneğin, meta veri türü `SortedList<K,V>` eşleyebilirsiniz `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="c1fdc-123">Bu nedenle, türü örnek oluşturma işlemek için bir yönteme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="c1fdc-124">.NET Framework sürüm 2.0 tanıtır `ICorDebugType` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="c1fdc-125">Genel bir tür için bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi dizilerine türünü temsil eder (`SortedList<K,V>`) ve bir `ICorDebugType` nesnesi çeşitli örneklenen türleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="c1fdc-126">Verilen bir `ICorDebugClass` veya `ICorDebugClass2` nesne oluşturabileceğiniz bir `ICorDebugType` nesne çağırarak tüm örnek oluşturma için `ICorDebugClass2::GetParameterizedType` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="c1fdc-127">Ayrıca bir `ICorDebugType` Nesne Int32 gibi basit bir tür veya genel olmayan bir tür.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="c1fdc-128">Giriş `ICorDebugType` nesne türü çalışma zamanı kavramını göstermek için API boyunca ripple etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="c1fdc-129">Daha önce geçen işlevleri bir `ICorDebugClass` veya `ICorDebugClass2` nesne ve hatta bir `CorElementType` değeri yapılacak genelleştirilmiş bir `ICorDebugType` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c1fdc-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1fdc-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1fdc-130">Requirements</span></span>  
 <span data-ttu-id="c1fdc-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1fdc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1fdc-132">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1fdc-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1fdc-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1fdc-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1fdc-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1fdc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
