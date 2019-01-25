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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f5c21d329ed35f82e36c2d88ac911401799e820
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596026"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="8e624-102">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e624-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="8e624-103">Yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için bellek ayırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e624-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e624-104">`IMethodMalloc` Basit bellek ayırıcı arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="8e624-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="8e624-105">Bellek ayıramadı, ancak boş değil sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e624-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e624-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8e624-106">Methods</span></span>  
  
|<span data-ttu-id="8e624-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8e624-107">Method</span></span>|<span data-ttu-id="8e624-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e624-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e624-109">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e624-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="8e624-110">Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="8e624-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e624-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e624-111">Remarks</span></span>  
 <span data-ttu-id="8e624-112">Her ayırıcı modülü özgü olan ve işlev gövdesi modülünün temel pozitif bir sapma olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e624-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="8e624-113">Yalnızca bir işlev gövdesi için bellek ayırmak için ayırıcı kullanılması gereken şekilde bellek temel bir modülün yukarıda değerli, olabilir.</span><span class="sxs-lookup"><span data-stu-id="8e624-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e624-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e624-114">Requirements</span></span>  
 <span data-ttu-id="8e624-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e624-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e624-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e624-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e624-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e624-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e624-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e624-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e624-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e624-119">See also</span></span>
- [<span data-ttu-id="8e624-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8e624-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
