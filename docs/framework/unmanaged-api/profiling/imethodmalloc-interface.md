---
title: IMethodMalloc Arabirimi
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 12b97b28383eb7c39f20ee0e88f55d48e60ad956
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494117"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="c2610-102">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2610-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="c2610-103">Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2610-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2610-104">`IMethodMalloc`Arabirim basit bir bellek ayırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c2610-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="c2610-105">Bellek ayırmayı, ancak serbest bırakmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c2610-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2610-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c2610-106">Methods</span></span>  
  
|<span data-ttu-id="c2610-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c2610-107">Method</span></span>|<span data-ttu-id="c2610-108">Description</span><span class="sxs-lookup"><span data-stu-id="c2610-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2610-109">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2610-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="c2610-110">Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="c2610-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2610-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2610-111">Remarks</span></span>  
 <span data-ttu-id="c2610-112">Her ayırıcı modüle özeldir ve işlev gövdesinin, modülün temelini pozitif bir uzaklığa göre olacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2610-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="c2610-113">Modülün temel aldığı bellek çok değerli olabilir, bu nedenle ayırıcı yalnızca bir işlev gövdesi için bellek ayırmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2610-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2610-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2610-114">Requirements</span></span>  
 <span data-ttu-id="c2610-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2610-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2610-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2610-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2610-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c2610-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2610-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2610-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2610-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2610-119">See also</span></span>

- [<span data-ttu-id="c2610-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2610-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
