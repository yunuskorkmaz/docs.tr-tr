---
title: "IMethodMalloc::Alloc Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae0fa84c08cb8e366db36b6727a3058f24789801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="4f818-102">IMethodMalloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f818-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="4f818-103">Belirtilen bir bellek miktarı için yeni bir Microsoft Ara dili (MSIL) işlev gövdesi ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="4f818-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f818-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f818-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f818-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f818-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="4f818-106">[in] Yöntem gövdesi için ayrılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4f818-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f818-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f818-107">Remarks</span></span>  
 <span data-ttu-id="4f818-108">Ayrılmış bellek taban adresi bu ayırıcısı ile ilişkili modülünün daha büyük bir adresindeki başlar.</span><span class="sxs-lookup"><span data-stu-id="4f818-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="4f818-109">Diğer bir deyişle, her ayırıcısı için belirli bir modülü oluşturulur ve temel adresinden bellek pozitif uzaklığındaki dener.</span><span class="sxs-lookup"><span data-stu-id="4f818-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="4f818-110">Varsa `Alloc` istenen modülü temel adresinden daha büyük bir adresindeki bayt sayısı ayrılamıyor başarısız kullanılabilir bellek alanı gerçek bakılmaksızın E_OUTOFMEMORY döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f818-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="4f818-111">`Alloc` Yöntemi ile birlikte kullanılmalıdır [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4f818-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f818-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f818-112">Requirements</span></span>  
 <span data-ttu-id="4f818-113">**Platformlar:** WindSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f818-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f818-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f818-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f818-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f818-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f818-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f818-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f818-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f818-117">See Also</span></span>  
 [<span data-ttu-id="4f818-118">Imethodmalloc arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f818-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
