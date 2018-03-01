---
title: IMethodMalloc Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1941a46a60219d9dd56d162f89baf268f220c102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="ecb95-102">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecb95-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="ecb95-103">Bellek için yeni bir Microsoft Ara dili (MSIL) işlev gövdesi ayırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecb95-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecb95-104">`IMethodMalloc` Basit bellek ayırıcısı bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="ecb95-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="ecb95-105">Bellek ayıramadı, ancak boş olmayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecb95-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecb95-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ecb95-106">Methods</span></span>  
  
|<span data-ttu-id="ecb95-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ecb95-107">Method</span></span>|<span data-ttu-id="ecb95-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecb95-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecb95-109">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecb95-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="ecb95-110">Yeni bir MSIL işlev gövdesi için belirtilen bir bellek miktarı ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="ecb95-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecb95-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecb95-111">Remarks</span></span>  
 <span data-ttu-id="ecb95-112">Her ayırıcısı modülü özeldir ve işlev gövdesi modülü tabanı pozitif uzaklığı en olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecb95-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="ecb95-113">Ayırıcı yalnızca bir işlev gövdesi için bellek tahsis için kullanılması gereken şekilde bir modül tabanı yukarıda bellek değerli, olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecb95-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecb95-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecb95-114">Requirements</span></span>  
 <span data-ttu-id="ecb95-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecb95-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecb95-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ecb95-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ecb95-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecb95-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecb95-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecb95-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb95-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecb95-119">See Also</span></span>  
 [<span data-ttu-id="ecb95-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ecb95-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
