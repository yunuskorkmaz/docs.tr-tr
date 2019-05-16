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
ms.openlocfilehash: 66bd56a332dc34fd35f3129256cc0e3d6c5d4508
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636695"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="b79d5-102">IMethodMalloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b79d5-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="b79d5-103">Yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="b79d5-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="b79d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b79d5-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="b79d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b79d5-105">Parameters</span></span>

`cb`\
<span data-ttu-id="b79d5-106">[in] Yöntem gövdesi için ayrılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b79d5-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="b79d5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b79d5-107">Remarks</span></span>

 <span data-ttu-id="b79d5-108">Ayrılan bellek bu ayırıcı ile ilişkili olan modülün taban adresi daha büyük bir adresten başlar.</span><span class="sxs-lookup"><span data-stu-id="b79d5-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="b79d5-109">Diğer bir deyişle, her ayırıcı için belirli bir modülün oluşturulur ve kendi temel adres bir pozitif uzaklığında bellek dener.</span><span class="sxs-lookup"><span data-stu-id="b79d5-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="b79d5-110">Varsa `Alloc` modülü temel adresini büyük bir adresteki bayt istenen sayıda başarısız E_OUTOFMEMORY, gerçek kullanılabilir bellek alanı miktarından bağımsız olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="b79d5-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="b79d5-111">`Alloc` Yöntemi ile birlikte kullanılması gerekir [Icorprofilerınfo::setılfunctionbody](icorprofilerinfo-setilfunctionbody-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b79d5-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b79d5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b79d5-112">Requirements</span></span>
 <span data-ttu-id="b79d5-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b79d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="b79d5-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b79d5-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="b79d5-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b79d5-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="b79d5-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b79d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b79d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b79d5-117">See also</span></span>

- [<span data-ttu-id="b79d5-118">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b79d5-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
