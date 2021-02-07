---
description: 'Daha fazla bilgi edinin: IMethodMalloc arabirimi'
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
ms.openlocfilehash: 6b84ac0ddb49718d24b2cad174613bc311dc509b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736966"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="208ef-103">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="208ef-103">IMethodMalloc Interface</span></span>

<span data-ttu-id="208ef-104">Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="208ef-104">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="208ef-105">`IMethodMalloc`Arabirim basit bir bellek ayırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="208ef-105">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="208ef-106">Bellek ayırmayı, ancak serbest bırakmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="208ef-106">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="208ef-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="208ef-107">Methods</span></span>  
  
|<span data-ttu-id="208ef-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="208ef-108">Method</span></span>|<span data-ttu-id="208ef-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="208ef-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="208ef-110">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="208ef-110">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="208ef-111">Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="208ef-111">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="208ef-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="208ef-112">Remarks</span></span>  

 <span data-ttu-id="208ef-113">Her ayırıcı modüle özeldir ve işlev gövdesinin, modülün temelini pozitif bir uzaklığa göre olacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="208ef-113">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="208ef-114">Modülün temel aldığı bellek çok değerli olabilir, bu nedenle ayırıcı yalnızca bir işlev gövdesi için bellek ayırmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="208ef-114">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="208ef-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="208ef-115">Requirements</span></span>  

 <span data-ttu-id="208ef-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="208ef-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="208ef-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="208ef-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="208ef-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="208ef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="208ef-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="208ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208ef-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="208ef-120">See also</span></span>

- [<span data-ttu-id="208ef-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="208ef-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
