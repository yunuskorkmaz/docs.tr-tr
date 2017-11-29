---
title: IMethodMalloc Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="8b7c4-102">IMethodMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b7c4-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="8b7c4-103">Bellek için yeni bir Microsoft Ara dili (MSIL) işlev gövdesi ayırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b7c4-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b7c4-104">`IMethodMalloc` Basit bellek ayırıcısı bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="8b7c4-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="8b7c4-105">Bellek ayıramadı, ancak boş olmayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b7c4-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b7c4-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8b7c4-106">Methods</span></span>  
  
|<span data-ttu-id="8b7c4-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8b7c4-107">Method</span></span>|<span data-ttu-id="8b7c4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b7c4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b7c4-109">Alloc yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b7c4-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="8b7c4-110">Yeni bir MSIL işlev gövdesi için belirtilen bir bellek miktarı ayırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="8b7c4-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b7c4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b7c4-111">Remarks</span></span>  
 <span data-ttu-id="8b7c4-112">Her ayırıcısı modülü özeldir ve işlev gövdesi modülü tabanı pozitif uzaklığı en olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b7c4-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="8b7c4-113">Ayırıcı yalnızca bir işlev gövdesi için bellek tahsis için kullanılması gereken şekilde bir modül tabanı yukarıda bellek değerli, olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b7c4-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b7c4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b7c4-114">Requirements</span></span>  
 <span data-ttu-id="8b7c4-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b7c4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b7c4-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b7c4-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b7c4-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b7c4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b7c4-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b7c4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7c4-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b7c4-119">See Also</span></span>  
 [<span data-ttu-id="8b7c4-120">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b7c4-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
