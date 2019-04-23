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
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077790"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="1caa7-102">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1caa7-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="1caa7-103">Yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için bellek ayırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="1caa7-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1caa7-104">`IMethodMalloc` Basit bellek ayırıcı arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="1caa7-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="1caa7-105">Bellek ayıramadı, ancak boş değil sağlar.</span><span class="sxs-lookup"><span data-stu-id="1caa7-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1caa7-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1caa7-106">Methods</span></span>  
  
|<span data-ttu-id="1caa7-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1caa7-107">Method</span></span>|<span data-ttu-id="1caa7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1caa7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1caa7-109">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1caa7-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="1caa7-110">Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="1caa7-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1caa7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1caa7-111">Remarks</span></span>  
 <span data-ttu-id="1caa7-112">Her ayırıcı modülü özgü olan ve işlev gövdesi modülünün temel pozitif bir sapma olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1caa7-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="1caa7-113">Yalnızca bir işlev gövdesi için bellek ayırmak için ayırıcı kullanılması gereken şekilde bellek temel bir modülün yukarıda değerli, olabilir.</span><span class="sxs-lookup"><span data-stu-id="1caa7-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1caa7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1caa7-114">Requirements</span></span>  
 <span data-ttu-id="1caa7-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1caa7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1caa7-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1caa7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1caa7-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1caa7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1caa7-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1caa7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caa7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1caa7-119">See also</span></span>

- [<span data-ttu-id="1caa7-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1caa7-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
