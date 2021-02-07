---
description: 'Daha fazla bilgi edinin: IHostMAlloc arabirimi'
title: IHostMalloc Arabirimi
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: cd04a0f71fd429ea10b9edcce02806f4afa57148
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708183"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="810ed-103">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="810ed-103">IHostMalloc Interface</span></span>

<span data-ttu-id="810ed-104">Ortak dil çalışma zamanının (CLR) ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="810ed-104">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="810ed-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="810ed-105">Methods</span></span>  
  
|<span data-ttu-id="810ed-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="810ed-106">Method</span></span>|<span data-ttu-id="810ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="810ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="810ed-108">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="810ed-108">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="810ed-109">Konağın, istenen bellek miktarını yığından ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="810ed-109">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="810ed-110">DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="810ed-110">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="810ed-111">Konağın, istenen bellek miktarını yığından ayırmasını ister ve ayrıca belleğin nerede ayrıldığını izler.</span><span class="sxs-lookup"><span data-stu-id="810ed-111">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="810ed-112">Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="810ed-112">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="810ed-113">Yöntemi kullanılarak ayrılan belleği boşaltır `Alloc` .</span><span class="sxs-lookup"><span data-stu-id="810ed-113">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="810ed-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="810ed-114">Remarks</span></span>  

 <span data-ttu-id="810ed-115">CLR, `IHostMalloc` [IHostMemoryManager:: createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="810ed-115">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="810ed-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="810ed-116">Requirements</span></span>  

 <span data-ttu-id="810ed-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="810ed-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="810ed-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="810ed-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="810ed-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="810ed-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="810ed-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="810ed-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810ed-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="810ed-121">See also</span></span>

- [<span data-ttu-id="810ed-122">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="810ed-122">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="810ed-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="810ed-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
