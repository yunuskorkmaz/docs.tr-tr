---
title: ICorProfilerInfo7::ApplyMetaData yöntemi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f261b02dd19ead0d6803cae543f39a06c99f033
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586694"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="15282-102">ICorProfilerInfo7::ApplyMetaData yöntemi</span><span class="sxs-lookup"><span data-stu-id="15282-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="15282-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="15282-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="15282-104">Yeni tarafından tanımlanan meta veriler geçerli `IMetadataEmit::Define*` Belirtilen modül için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="15282-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15282-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15282-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15282-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15282-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="15282-107">[in] Modül, meta verileri değiştirildi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="15282-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15282-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15282-108">Remarks</span></span>  
 <span data-ttu-id="15282-109">Sonra meta verileri değişiklikler yapılırsa [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri yeni meta veriler kullanmadan önce bu yöntemini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15282-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="15282-110">`ApplyMetaData` Yalnızca şu meta veri türleri eklemeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="15282-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="15282-111">`AssemblyRef` çağırarak denetlediği oluşturma records [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="15282-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="15282-112">yöntem.</span><span class="sxs-lookup"><span data-stu-id="15282-112">method.</span></span>  
  
- <span data-ttu-id="15282-113">`TypeRef` çağırarak denetlediği oluşturma records [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15282-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="15282-114">`TypeSpec` çağırarak denetlediği oluşturma records [Imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15282-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="15282-115">`MemberRef` çağırarak denetlediği oluşturma records [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15282-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="15282-116">`MemberSpec` çağırarak denetlediği oluşturma records [Imetadataemit2::definemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15282-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="15282-117">`UserString` çağırarak denetlediği oluşturma records [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15282-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="15282-118">.NET Core 3.0 ile başlayan `ApplyMetaData` ayrıca aşağıdaki türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="15282-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="15282-119">`TypeDef` çağırarak denetlediği oluşturma records [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15282-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="15282-120">`MethodDef` çağırarak denetlediği oluşturma records [Imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15282-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="15282-121">Ancak, sanal yöntemleri mevcut türü için ekleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="15282-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="15282-122">Sanal yöntemler eklendi, önce [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="15282-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="15282-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15282-123">Requirements</span></span>  
 <span data-ttu-id="15282-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15282-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15282-125">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15282-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15282-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15282-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15282-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15282-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15282-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15282-128">See also</span></span>

- [<span data-ttu-id="15282-129">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15282-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
