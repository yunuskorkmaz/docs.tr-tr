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
ms.openlocfilehash: 8af2b6834ac8655c64a7738c65550b515a4b6675
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439051"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="03bc1-102">ICorProfilerInfo::GetILFunctionBodyAllocator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03bc1-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="03bc1-103">Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesini değiştirmek için kullanılacak belleği ayırmak üzere bir yöntemi sağlayan bir arabirim alır.</span><span class="sxs-lookup"><span data-stu-id="03bc1-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03bc1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03bc1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03bc1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03bc1-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="03bc1-106">'ndaki Yöntemin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="03bc1-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="03bc1-107">dışı Belleği ayırmak için bir yöntem sağlayan bir [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03bc1-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03bc1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03bc1-108">Remarks</span></span>  
 <span data-ttu-id="03bc1-109">MSIL kodundaki bir yöntem gövdesi, yüklenen modüle göre, bir göreli sanal adres (RVA) olarak yerleştirilmelidir, bu da modülün 4 GB dahilinde izlediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="03bc1-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="03bc1-110">Bir aracın bir yöntemin gövdesini takas edilmesini kolaylaştırmak için `GetILFunctionBodyAllocator` yöntemi belleğin bu Aralık içinde ayrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="03bc1-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03bc1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03bc1-111">Requirements</span></span>  
 <span data-ttu-id="03bc1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03bc1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03bc1-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="03bc1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03bc1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="03bc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03bc1-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03bc1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03bc1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03bc1-116">See also</span></span>

- [<span data-ttu-id="03bc1-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03bc1-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
