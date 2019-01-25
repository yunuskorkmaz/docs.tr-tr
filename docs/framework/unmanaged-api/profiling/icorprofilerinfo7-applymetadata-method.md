---
title: ICorProfilerInfo7::ApplyMetaData yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 7209314f9cf3170ba0b577395a5134f9549475e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536574"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="f66f3-102">ICorProfilerInfo7::ApplyMetaData yöntemi</span><span class="sxs-lookup"><span data-stu-id="f66f3-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="f66f3-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="f66f3-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="f66f3-104">Yeni tarafından tanımlanan meta veriler geçerli `IMetadataEmit::Define*` Belirtilen modül için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f66f3-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66f3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f66f3-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f66f3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f66f3-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="f66f3-107">[in] Modül, meta verileri değiştirildi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f66f3-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f66f3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f66f3-108">Remarks</span></span>  
 <span data-ttu-id="f66f3-109">Sonra meta verileri değişiklikler yapılırsa [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri yeni meta veriler kullanmadan önce bu yöntemini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f66f3-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="f66f3-110">`ApplyMetaData` Yalnızca şu meta veri türleri eklemeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="f66f3-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="f66f3-111">`AssemblyRef` çağırarak denetlediği oluşturma records [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="f66f3-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="f66f3-112">yöntem.</span><span class="sxs-lookup"><span data-stu-id="f66f3-112">method.</span></span>  
  
-   <span data-ttu-id="f66f3-113">`TypeRef` çağırarak denetlediği oluşturma records [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f66f3-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="f66f3-114">`TypeSpec` çağırarak denetlediği oluşturma records [Imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f66f3-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="f66f3-115">`MemberRef` çağırarak denetlediği oluşturma records [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f66f3-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="f66f3-116">`MemberSpec` çağırarak denetlediği oluşturma records [Imetadataemit2::definemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f66f3-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="f66f3-117">`UserString` çağırarak denetlediği oluşturma records [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f66f3-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f66f3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f66f3-118">Requirements</span></span>  
 <span data-ttu-id="f66f3-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f66f3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f66f3-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f66f3-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f66f3-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f66f3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f66f3-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f66f3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66f3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f66f3-123">See also</span></span>
- [<span data-ttu-id="f66f3-124">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f66f3-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
