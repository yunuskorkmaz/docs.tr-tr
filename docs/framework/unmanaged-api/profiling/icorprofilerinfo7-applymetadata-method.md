---
title: "ICorProfilerInfo7::ApplyMetaData yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ICorProfilerInfo7.ApplyMetaData
api_location: mscorwks.dll
api_type: COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3724555df58392e5ab59ccb4f52dd2de860b8d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="774b1-102">ICorProfilerInfo7::ApplyMetaData yöntemi</span><span class="sxs-lookup"><span data-stu-id="774b1-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="774b1-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="774b1-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="774b1-104">Yeni tarafından tanımlanan meta verilerine uygulanır `IMetadataEmit::Define*` Belirtilen modül yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="774b1-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="774b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="774b1-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="774b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="774b1-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="774b1-107">[in] Meta verileri değiştirildi modülü tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="774b1-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="774b1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="774b1-108">Remarks</span></span>  
 <span data-ttu-id="774b1-109">Meta veri değişiklikleri sonra yapılırsa [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri arama, yeni meta kullanmadan önce bu yöntem çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="774b1-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="774b1-110">`ApplyMetaData`Yalnızca şu meta veri türleri ekleme destekler:</span><span class="sxs-lookup"><span data-stu-id="774b1-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="774b1-111">`AssemblyRef`çağırarak oluşturduğunuz kayıtları [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="774b1-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="774b1-112">yöntem.</span><span class="sxs-lookup"><span data-stu-id="774b1-112">method.</span></span>  
  
-   <span data-ttu-id="774b1-113">`TypeRef`çağırarak oluşturduğunuz kayıtları [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="774b1-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="774b1-114">`TypeSpec`çağırarak oluşturduğunuz kayıtları [Imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="774b1-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="774b1-115">`MemberRef`çağırarak oluşturduğunuz kayıtları [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="774b1-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="774b1-116">`MemberSpec`çağırarak oluşturduğunuz kayıtları [Imetadataemit2::definemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="774b1-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="774b1-117">`UserString`çağırarak oluşturduğunuz kayıtları [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="774b1-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="774b1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="774b1-118">Requirements</span></span>  
 <span data-ttu-id="774b1-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="774b1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="774b1-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="774b1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="774b1-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="774b1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="774b1-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="774b1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="774b1-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="774b1-123">See Also</span></span>  
 [<span data-ttu-id="774b1-124">ICorProfilerInfo7 arabirimi</span><span class="sxs-lookup"><span data-stu-id="774b1-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
