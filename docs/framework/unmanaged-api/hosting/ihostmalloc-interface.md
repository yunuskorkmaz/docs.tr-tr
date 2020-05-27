---
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
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804612"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="972a9-102">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="972a9-102">IHostMalloc Interface</span></span>
<span data-ttu-id="972a9-103">Ortak dil çalışma zamanının (CLR) ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="972a9-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="972a9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="972a9-104">Methods</span></span>  
  
|<span data-ttu-id="972a9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="972a9-105">Method</span></span>|<span data-ttu-id="972a9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="972a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="972a9-107">Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="972a9-107">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="972a9-108">Konağın, istenen bellek miktarını yığından ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="972a9-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="972a9-109">DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="972a9-109">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="972a9-110">Konağın, istenen bellek miktarını yığından ayırmasını ister ve ayrıca belleğin nerede ayrıldığını izler.</span><span class="sxs-lookup"><span data-stu-id="972a9-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="972a9-111">Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="972a9-111">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="972a9-112">Yöntemi kullanılarak ayrılan belleği boşaltır `Alloc` .</span><span class="sxs-lookup"><span data-stu-id="972a9-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="972a9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="972a9-113">Remarks</span></span>  
 <span data-ttu-id="972a9-114">CLR, `IHostMalloc` [IHostMemoryManager:: createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="972a9-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="972a9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="972a9-115">Requirements</span></span>  
 <span data-ttu-id="972a9-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="972a9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="972a9-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="972a9-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="972a9-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="972a9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="972a9-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="972a9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972a9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="972a9-120">See also</span></span>

- [<span data-ttu-id="972a9-121">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="972a9-121">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="972a9-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="972a9-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
