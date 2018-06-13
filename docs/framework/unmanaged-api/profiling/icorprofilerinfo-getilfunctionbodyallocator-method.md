---
title: ICorProfilerInfo::GetILFunctionBodyAllocator Metodu
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
ms.openlocfilehash: 00a3afab4d5f6151bcd0efd2b658d4cd7fa8f1e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462208"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="eb40a-102">ICorProfilerInfo::GetILFunctionBodyAllocator Metodu</span><span class="sxs-lookup"><span data-stu-id="eb40a-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="eb40a-103">Microsoft Ara dili (MSIL) kodda bir yöntemin gövdesi değiştirme için kullanılacak bellek ayırmak için bir yöntem sağlayan bir arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="eb40a-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb40a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb40a-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb40a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb40a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="eb40a-106">[in] Yöntemi içinde bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="eb40a-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="eb40a-107">[out] Bir işaretçi bir [Imethodmalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirimi bellek ayırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb40a-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb40a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb40a-108">Remarks</span></span>  
 <span data-ttu-id="eb40a-109">MSIL kod yöntemi gövdesinde modülü 4 GB içinde izlediğini anlamına gelir yüklenen modülün göre göreli sanal adres (RAV) olarak yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb40a-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="eb40a-110">Bir yöntemin gövdesi değiştirilecek bir aracı kolaylaştırmak için `GetILFunctionBodyAllocator` yöntemi, belleğin sağlar bu aralıkta ayrılır.</span><span class="sxs-lookup"><span data-stu-id="eb40a-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb40a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb40a-111">Requirements</span></span>  
 <span data-ttu-id="eb40a-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb40a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb40a-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb40a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb40a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb40a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb40a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb40a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb40a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb40a-116">See Also</span></span>  
 [<span data-ttu-id="eb40a-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb40a-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
