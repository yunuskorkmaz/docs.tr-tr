---
title: IMethodMalloc::Alloc Yöntemi
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54c38f9a9abc9a02ba4d84c9a41b2ef6b1f7cb69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528569"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="907da-102">IMethodMalloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="907da-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="907da-103">Yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="907da-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="907da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="907da-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="907da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="907da-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="907da-106">[in] Yöntem gövdesi için ayrılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="907da-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="907da-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="907da-107">Remarks</span></span>  
 <span data-ttu-id="907da-108">Ayrılan bellek bu ayırıcı ile ilişkili olan modülün taban adresi daha büyük bir adresten başlar.</span><span class="sxs-lookup"><span data-stu-id="907da-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="907da-109">Diğer bir deyişle, her ayırıcı için belirli bir modülün oluşturulur ve kendi temel adres bir pozitif uzaklığında bellek dener.</span><span class="sxs-lookup"><span data-stu-id="907da-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="907da-110">Varsa `Alloc` modülü temel adresini büyük bir adresteki bayt istenen sayıda başarısız E_OUTOFMEMORY, gerçek kullanılabilir bellek alanı miktarından bağımsız olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="907da-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="907da-111">`Alloc` Yöntemi ile birlikte kullanılması gerekir [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="907da-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="907da-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="907da-112">Requirements</span></span>  
 <span data-ttu-id="907da-113">**Platformlar:** WindSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="907da-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="907da-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="907da-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="907da-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="907da-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="907da-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="907da-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907da-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="907da-117">See also</span></span>
- [<span data-ttu-id="907da-118">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="907da-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
