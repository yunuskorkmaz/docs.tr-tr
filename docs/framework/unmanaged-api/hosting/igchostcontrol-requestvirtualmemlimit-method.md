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
ms.openlocfilehash: 2df33e3edebbf558bf78986e737c4f7bb9b2f0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437163"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="f5082-102">IGCHostControl::RequestVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5082-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="f5082-103">Sanal bellek sınırları değiştirmek için ana ister.</span><span class="sxs-lookup"><span data-stu-id="f5082-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5082-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5082-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5082-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5082-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="f5082-106">[in] Ayrılacak bellek istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="f5082-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="f5082-107">[içinde out] Ayrılmış bellek gerçek boyutuna yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f5082-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5082-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5082-108">Requirements</span></span>  
 <span data-ttu-id="f5082-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5082-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5082-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5082-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5082-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f5082-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5082-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5082-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5082-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5082-113">See Also</span></span>  
 [<span data-ttu-id="f5082-114">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5082-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
