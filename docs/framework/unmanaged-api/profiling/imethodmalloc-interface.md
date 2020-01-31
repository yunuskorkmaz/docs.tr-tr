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
ms.openlocfilehash: e9cbf4551c2f8b183e9e6c37a74b13aff3a19ec1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860989"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="48ed4-102">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48ed4-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="48ed4-103">Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="48ed4-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48ed4-104">`IMethodMalloc` arabirimi basit bir bellek ayırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="48ed4-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="48ed4-105">Bellek ayırmayı, ancak serbest bırakmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="48ed4-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48ed4-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="48ed4-106">Methods</span></span>  
  
|<span data-ttu-id="48ed4-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="48ed4-107">Method</span></span>|<span data-ttu-id="48ed4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48ed4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48ed4-109">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48ed4-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="48ed4-110">Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="48ed4-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48ed4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48ed4-111">Remarks</span></span>  
 <span data-ttu-id="48ed4-112">Her ayırıcı modüle özeldir ve işlev gövdesinin, modülün temelini pozitif bir uzaklığa göre olacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="48ed4-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="48ed4-113">Modülün temel aldığı bellek çok değerli olabilir, bu nedenle ayırıcı yalnızca bir işlev gövdesi için bellek ayırmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48ed4-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48ed4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48ed4-114">Requirements</span></span>  
 <span data-ttu-id="48ed4-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48ed4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48ed4-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="48ed4-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48ed4-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="48ed4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48ed4-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48ed4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ed4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48ed4-119">See also</span></span>

- [<span data-ttu-id="48ed4-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="48ed4-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
