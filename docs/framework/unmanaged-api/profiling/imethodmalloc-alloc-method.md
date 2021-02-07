---
description: ': IMethodMalloc:: ayırma yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f8a41530e0e1a126fafa1816e6fed58d10df6587
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736961"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="85f68-103">IMethodMalloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85f68-103">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="85f68-104">Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="85f68-104">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="85f68-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85f68-105">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="85f68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85f68-106">Parameters</span></span>

`cb`\
<span data-ttu-id="85f68-107">'ndaki Yöntem gövdesi için ayrılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="85f68-107">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="85f68-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85f68-108">Remarks</span></span>

 <span data-ttu-id="85f68-109">Ayrılan bellek, bu ayırıcıyla ilişkili modülün temel adresinden büyük bir adreste başlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="85f68-109">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="85f68-110">Diğer bir deyişle, her ayırıcı belirli bir modül için oluşturulur ve temel adresinden pozitif bir uzaklığa bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="85f68-110">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="85f68-111">`Alloc`Modülün temel adresinden daha büyük bir adreste istenen bayt sayısını ayıramazsa, kullanılabilir bellek alanının gerçek miktarından bağımsız olarak e_outofmemory döndürür.</span><span class="sxs-lookup"><span data-stu-id="85f68-111">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="85f68-112">`Alloc`Yöntemi [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yöntemiyle birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85f68-112">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="85f68-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85f68-113">Requirements</span></span>

 <span data-ttu-id="85f68-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85f68-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="85f68-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="85f68-115">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="85f68-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="85f68-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="85f68-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f68-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="85f68-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85f68-118">See also</span></span>

- [<span data-ttu-id="85f68-119">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f68-119">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
