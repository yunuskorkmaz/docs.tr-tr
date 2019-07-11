---
title: IGCHostControl::RequestVirtualMemLimit Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb0b6191c74c2b7ebdc8267701f246c17b016f9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779519"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="0a6e4-102">IGCHostControl::RequestVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a6e4-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="0a6e4-103">Sanal bellek sınırlarını değiştirmek için ana ister.</span><span class="sxs-lookup"><span data-stu-id="0a6e4-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a6e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a6e4-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a6e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a6e4-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="0a6e4-106">[in] Ayrılacak bellek istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="0a6e4-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="0a6e4-107">[out içinde] Gerçek Boyut ayrılan bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0a6e4-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a6e4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a6e4-108">Requirements</span></span>  
 <span data-ttu-id="0a6e4-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a6e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a6e4-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a6e4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a6e4-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0a6e4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a6e4-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a6e4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a6e4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a6e4-113">See also</span></span>

- [<span data-ttu-id="0a6e4-114">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a6e4-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
