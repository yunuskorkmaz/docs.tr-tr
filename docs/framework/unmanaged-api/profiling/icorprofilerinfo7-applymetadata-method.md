---
title: 'ICorProfilerInfo7:: ApplyMetaData yöntemi'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 2c71db25422740880d8b29576eff247d5eba5f1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686117"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="9d59f-102">ICorProfilerInfo7:: ApplyMetaData yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d59f-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>

<span data-ttu-id="9d59f-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="9d59f-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="9d59f-104">Yöntemler tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular `IMetadataEmit::Define*` .</span><span class="sxs-lookup"><span data-stu-id="9d59f-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d59f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9d59f-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d59f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d59f-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="9d59f-107">'ndaki Meta verileri değişmiş olan modülün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d59f-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d59f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d59f-108">Remarks</span></span>  

 <span data-ttu-id="9d59f-109">Meta veri değişiklikleri [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından sonra yapılmışsa, yeni meta verileri kullanmadan önce bu yöntemi çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d59f-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="9d59f-110">`ApplyMetaData` yalnızca aşağıdaki meta veri türlerinin eklenmesini destekler:</span><span class="sxs-lookup"><span data-stu-id="9d59f-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="9d59f-111">`AssemblyRef`[IMetaDataAssemblyEmit::D efineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md)' i çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="9d59f-112">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9d59f-112">method.</span></span>  
  
- <span data-ttu-id="9d59f-113">`TypeRef`[ımetadatayay::D efineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="9d59f-114">`TypeSpec`[ımetadatayay:: GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="9d59f-115">`MemberRef`[ımetadatayay::D efineMemberRef](../metadata/imetadataemit-definememberref-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="9d59f-116">`MemberSpec`[IMetaDataEmit2::D efineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="9d59f-117">`UserString`[ımetadatayay::D efineUserString](../metadata/imetadataemit-defineuserstring-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="9d59f-118">.NET Core 3,0 ile başlayarak, `ApplyMetaData` aşağıdaki türleri de destekler:</span><span class="sxs-lookup"><span data-stu-id="9d59f-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="9d59f-119">`TypeDef`[ımetadatayayma::D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) yöntemini çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="9d59f-120">`MethodDef`[ımetadatayayma::D efineMethod](../metadata/imetadataemit-definemethod-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9d59f-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="9d59f-121">Ancak, var olan bir türe sanal yöntemler eklemek desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9d59f-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="9d59f-122">Sanal yöntemler [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından önce eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9d59f-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d59f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d59f-123">Requirements</span></span>  

 <span data-ttu-id="9d59f-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d59f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d59f-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d59f-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d59f-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d59f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d59f-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d59f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d59f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d59f-128">See also</span></span>

- [<span data-ttu-id="9d59f-129">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d59f-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
