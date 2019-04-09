---
title: IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4675c34bfe8d1d79c184c43e5f7f5dd3a03be6a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201006"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="573f6-102">IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="573f6-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="573f6-103">Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek işletim sisteminden almışsa bildirir.</span><span class="sxs-lookup"><span data-stu-id="573f6-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="573f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="573f6-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="573f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="573f6-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="573f6-106">[in] Bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="573f6-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="573f6-107">[in] Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="573f6-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="573f6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="573f6-108">Remarks</span></span>  
 <span data-ttu-id="573f6-109">`AcquiredVirtualAddressSpace` Yöntemi geri çağırma yöntemi olan ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="573f6-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="573f6-110">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="573f6-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="573f6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="573f6-111">Requirements</span></span>  
 <span data-ttu-id="573f6-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="573f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="573f6-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="573f6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="573f6-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="573f6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="573f6-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="573f6-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="573f6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="573f6-116">See also</span></span>

- [<span data-ttu-id="573f6-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="573f6-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
