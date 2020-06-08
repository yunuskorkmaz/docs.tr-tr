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
ms.openlocfilehash: a82a2150f32b1b335da083ca235ed9d2966a0b6e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494208"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="d59aa-102">IMethodMalloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d59aa-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="d59aa-103">Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="d59aa-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="d59aa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d59aa-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="d59aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d59aa-105">Parameters</span></span>

`cb`\
<span data-ttu-id="d59aa-106">'ndaki Yöntem gövdesi için ayrılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d59aa-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="d59aa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d59aa-107">Remarks</span></span>

 <span data-ttu-id="d59aa-108">Ayrılan bellek, bu ayırıcıyla ilişkili modülün temel adresinden büyük bir adreste başlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d59aa-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="d59aa-109">Diğer bir deyişle, her ayırıcı belirli bir modül için oluşturulur ve temel adresinden pozitif bir uzaklığa bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="d59aa-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="d59aa-110">`Alloc`Modülün temel adresinden daha büyük bir adreste istenen bayt sayısını ayıramazsa, kullanılabilir bellek alanının gerçek miktarından bağımsız olarak e_outofmemory döndürür.</span><span class="sxs-lookup"><span data-stu-id="d59aa-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="d59aa-111">`Alloc`Yöntemi [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yöntemiyle birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d59aa-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d59aa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d59aa-112">Requirements</span></span>
 <span data-ttu-id="d59aa-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59aa-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="d59aa-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d59aa-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="d59aa-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d59aa-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="d59aa-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59aa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d59aa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d59aa-117">See also</span></span>

- [<span data-ttu-id="d59aa-118">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d59aa-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
