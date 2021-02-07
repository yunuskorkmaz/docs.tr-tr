---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo7:: ApplyMetaData yöntemi'
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
ms.openlocfilehash: 3a4554357ede85d936e8bf9c87c6b9c096dab188
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737135"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="9ac36-103">ICorProfilerInfo7:: ApplyMetaData yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ac36-103">ICorProfilerInfo7::ApplyMetaData Method</span></span>

<span data-ttu-id="9ac36-104">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="9ac36-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="9ac36-105">Yöntemler tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular `IMetadataEmit::Define*` .</span><span class="sxs-lookup"><span data-stu-id="9ac36-105">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac36-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ac36-106">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac36-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ac36-107">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="9ac36-108">'ndaki Meta verileri değişmiş olan modülün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9ac36-108">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac36-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ac36-109">Remarks</span></span>  

 <span data-ttu-id="9ac36-110">Meta veri değişiklikleri [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından sonra yapılmışsa, yeni meta verileri kullanmadan önce bu yöntemi çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ac36-110">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="9ac36-111">`ApplyMetaData` yalnızca aşağıdaki meta veri türlerinin eklenmesini destekler:</span><span class="sxs-lookup"><span data-stu-id="9ac36-111">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="9ac36-112">`AssemblyRef`[IMetaDataAssemblyEmit::D efineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md)' i çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-112">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="9ac36-113">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9ac36-113">method.</span></span>  
  
- <span data-ttu-id="9ac36-114">`TypeRef`[ımetadatayay::D efineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-114">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="9ac36-115">`TypeSpec`[ımetadatayay:: GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-115">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="9ac36-116">`MemberRef`[ımetadatayay::D efineMemberRef](../metadata/imetadataemit-definememberref-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-116">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="9ac36-117">`MemberSpec`[IMetaDataEmit2::D efineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-117">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="9ac36-118">`UserString`[ımetadatayay::D efineUserString](../metadata/imetadataemit-defineuserstring-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-118">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="9ac36-119">.NET Core 3,0 ile başlayarak, `ApplyMetaData` aşağıdaki türleri de destekler:</span><span class="sxs-lookup"><span data-stu-id="9ac36-119">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="9ac36-120">`TypeDef`[ımetadatayayma::D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) yöntemini çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-120">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="9ac36-121">`MethodDef`[ımetadatayayma::D efineMethod](../metadata/imetadataemit-definemethod-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="9ac36-121">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="9ac36-122">Ancak, var olan bir türe sanal yöntemler eklemek desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9ac36-122">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="9ac36-123">Sanal yöntemler [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından önce eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9ac36-123">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ac36-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ac36-124">Requirements</span></span>  

 <span data-ttu-id="9ac36-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ac36-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac36-126">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ac36-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ac36-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9ac36-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ac36-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac36-128">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac36-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ac36-129">See also</span></span>

- [<span data-ttu-id="9ac36-130">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ac36-130">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
