---
title: ICLRGCManager2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 72ffd7b47795ee8e46f8fbff07559133843793e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141150"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="cc2f1-102">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc2f1-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="cc2f1-103">Bir konağın ortak dil çalışma zamanının çöp toplama sistemiyle etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc2f1-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc2f1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cc2f1-104">Methods</span></span>  
  
|<span data-ttu-id="cc2f1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cc2f1-105">Method</span></span>|<span data-ttu-id="cc2f1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc2f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc2f1-107">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc2f1-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="cc2f1-108">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cc2f1-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="cc2f1-109">Nesil 0 ve kesim boyutlarını `DWORD`daha büyük bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="cc2f1-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc2f1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc2f1-110">Remarks</span></span>  
 <span data-ttu-id="cc2f1-111">Bu arabirim [ICLRGCManager arabiriminden](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)devralır.</span><span class="sxs-lookup"><span data-stu-id="cc2f1-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="cc2f1-112">Ortak dil çalışma zamanı (CLR), atık toplama mekanizmasını yönetilen <xref:System.GC> türüyle uygular.</span><span class="sxs-lookup"><span data-stu-id="cc2f1-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="cc2f1-113">Çöp toplama sistemi hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc2f1-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc2f1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc2f1-114">Requirements</span></span>  
 <span data-ttu-id="cc2f1-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc2f1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc2f1-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc2f1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc2f1-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cc2f1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc2f1-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc2f1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc2f1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc2f1-119">See also</span></span>

- [<span data-ttu-id="cc2f1-120">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="cc2f1-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="cc2f1-121">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc2f1-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="cc2f1-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc2f1-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="cc2f1-123">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cc2f1-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="cc2f1-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cc2f1-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cc2f1-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="cc2f1-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
