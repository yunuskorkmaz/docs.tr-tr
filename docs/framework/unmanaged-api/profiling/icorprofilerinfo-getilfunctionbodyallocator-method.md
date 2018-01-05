---
title: ICorProfilerInfo::GetILFunctionBodyAllocator Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBodyAllocator
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1feec20f0ddc4f6029490e06d4729b3fdaa7fa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="2c794-102">ICorProfilerInfo::GetILFunctionBodyAllocator Metodu</span><span class="sxs-lookup"><span data-stu-id="2c794-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="2c794-103">Microsoft Ara dili (MSIL) kodda bir yöntemin gövdesi değiştirme için kullanılacak bellek ayırmak için bir yöntem sağlayan bir arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="2c794-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c794-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c794-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c794-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c794-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2c794-106">[in] Yöntemi içinde bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="2c794-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="2c794-107">[out] Bir işaretçi bir [Imethodmalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirimi bellek ayırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c794-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c794-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c794-108">Remarks</span></span>  
 <span data-ttu-id="2c794-109">MSIL kod yöntemi gövdesinde modülü 4 GB içinde izlediğini anlamına gelir yüklenen modülün göre göreli sanal adres (RAV) olarak yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c794-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="2c794-110">Bir yöntemin gövdesi değiştirilecek bir aracı kolaylaştırmak için `GetILFunctionBodyAllocator` yöntemi, belleğin sağlar bu aralıkta ayrılır.</span><span class="sxs-lookup"><span data-stu-id="2c794-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c794-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c794-111">Requirements</span></span>  
 <span data-ttu-id="2c794-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c794-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c794-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c794-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c794-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c794-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c794-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c794-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c794-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c794-116">See Also</span></span>  
 [<span data-ttu-id="2c794-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c794-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
