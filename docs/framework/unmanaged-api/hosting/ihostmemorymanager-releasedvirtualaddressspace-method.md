---
title: IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f6a3d425d4c2ae2146723a6acfc5ab9893f0fe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438447"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="a770e-102">IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a770e-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="a770e-103">Ana makine ortak dil çalışma zamanı (CLR) belirtilen bellek kullanarak tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="a770e-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a770e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a770e-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a770e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a770e-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="a770e-106">[in] Başlangıç adresi serbest bırakılacak bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a770e-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a770e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a770e-107">Remarks</span></span>  
 <span data-ttu-id="a770e-108">`ReleasedVirtualAddressSpace` Yöntemi bir geri çağırma yöntemini ve barındırma uygulama yazıcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a770e-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="a770e-109">CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a770e-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a770e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a770e-110">Requirements</span></span>  
 <span data-ttu-id="a770e-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a770e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a770e-112">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a770e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a770e-113">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a770e-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a770e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a770e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a770e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a770e-115">See Also</span></span>  
 [<span data-ttu-id="a770e-116">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a770e-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
