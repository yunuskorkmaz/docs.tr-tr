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
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861703"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="1ba15-102">ICorProfilerInfo7:: ApplyMetaData yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ba15-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="1ba15-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="1ba15-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="1ba15-104">`IMetadataEmit::Define*` yöntemleri tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular.</span><span class="sxs-lookup"><span data-stu-id="1ba15-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ba15-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba15-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ba15-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ba15-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="1ba15-107">'ndaki Meta verileri değişmiş olan modülün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1ba15-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ba15-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ba15-108">Remarks</span></span>  
 <span data-ttu-id="1ba15-109">Meta veri değişiklikleri [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından sonra yapılmışsa, yeni meta verileri kullanmadan önce bu yöntemi çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ba15-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="1ba15-110">`ApplyMetaData` yalnızca aşağıdaki meta veri türlerinin eklenmesini destekler:</span><span class="sxs-lookup"><span data-stu-id="1ba15-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="1ba15-111">[IMetaDataAssemblyEmit::D efineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)öğesini çağırarak oluşturduğunuz kayıtları `AssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="1ba15-112">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="1ba15-112">method.</span></span>  
  
- <span data-ttu-id="1ba15-113">[ımetadatayayma::D efineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metodunu çağırarak oluşturduğunuz kayıtları `TypeRef`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="1ba15-114">[ımetadatayay:: GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metodunu çağırarak oluşturduğunuz kayıtları `TypeSpec`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="1ba15-115">[ımetadatayayma::D efineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metodunu çağırarak oluşturduğunuz kayıtları `MemberRef`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="1ba15-116">[IMetaDataEmit2::D efineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metodunu çağırarak oluşturduğunuz kayıtları `MemberSpec`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="1ba15-117">[ımetadatayayma::D efineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metodunu çağırarak oluşturduğunuz kayıtları `UserString`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="1ba15-118">.NET Core 3,0 ile başlayarak `ApplyMetaData`, aşağıdaki türleri de destekler:</span><span class="sxs-lookup"><span data-stu-id="1ba15-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="1ba15-119">[ımetadatayayma::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemini çağırarak oluşturduğunuz kayıtları `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="1ba15-120">[ımetadatayayma::D efineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) metodunu çağırarak oluşturduğunuz kayıtları `MethodDef`.</span><span class="sxs-lookup"><span data-stu-id="1ba15-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="1ba15-121">Ancak, var olan bir türe sanal yöntemler eklemek desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1ba15-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="1ba15-122">Sanal yöntemler [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından önce eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1ba15-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ba15-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ba15-123">Requirements</span></span>  
 <span data-ttu-id="1ba15-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ba15-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ba15-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1ba15-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ba15-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ba15-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ba15-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ba15-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba15-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba15-128">See also</span></span>

- [<span data-ttu-id="1ba15-129">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ba15-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
