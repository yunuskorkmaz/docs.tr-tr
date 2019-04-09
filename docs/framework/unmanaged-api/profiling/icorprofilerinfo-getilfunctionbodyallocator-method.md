---
title: ICorProfilerInfo::GetILFunctionBodyAllocator Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cd66a895f99d62e8deaa45afab12d963aee2901
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109128"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="0864f-102">ICorProfilerInfo::GetILFunctionBodyAllocator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0864f-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="0864f-103">Bir yöntem gövdesi bir yöntemin Microsoft Ara dil (MSIL) kodu değiştirme için kullanılacak bellek ayırmak için sağlayan bir arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="0864f-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0864f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0864f-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0864f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0864f-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="0864f-106">[in] Yöntem bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="0864f-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="0864f-107">[out] Bir işaretçi bir [Imethodmalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirimi bellek ayırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="0864f-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0864f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0864f-108">Remarks</span></span>  
 <span data-ttu-id="0864f-109">MSIL kodunun bir yöntem gövdesinde bir göreli sanal adres (RVA) göre 4 GB içinde modül izlediğini anlamına gelir yüklenen modül olarak yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="0864f-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="0864f-110">Bir yöntem gövdesi takas etmek bir araç kolaylaştırmak için `GetILFunctionBodyAllocator` yöntemi sağlar, bellek bu aralıkta ayrılır.</span><span class="sxs-lookup"><span data-stu-id="0864f-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0864f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0864f-111">Requirements</span></span>  
 <span data-ttu-id="0864f-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0864f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0864f-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0864f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0864f-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0864f-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0864f-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0864f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0864f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0864f-116">See also</span></span>

- [<span data-ttu-id="0864f-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0864f-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
