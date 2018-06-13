---
title: IGCHost::SetVirtualMemLimit Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1d61c8aeaf458d8cbbd2976fa83aaa0eeb0f834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437745"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="d488c-102">IGCHost::SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d488c-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="d488c-103">En büyük çalışma zamanı'nın sanal bellek boyutunu belirler.</span><span class="sxs-lookup"><span data-stu-id="d488c-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d488c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d488c-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d488c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d488c-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="d488c-106">[in] Çalışma zamanı'nın sanal bellek megabayt cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="d488c-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d488c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d488c-107">Remarks</span></span>  
 <span data-ttu-id="d488c-108">En büyük çalışma zamanı'nın sanal bellek boyutunu dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d488c-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d488c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d488c-109">Requirements</span></span>  
 <span data-ttu-id="d488c-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d488c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d488c-111">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="d488c-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d488c-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d488c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d488c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d488c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d488c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d488c-114">See Also</span></span>  
 [<span data-ttu-id="d488c-115">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d488c-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
