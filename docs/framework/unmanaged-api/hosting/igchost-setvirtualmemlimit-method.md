---
title: "IGCHost::SetVirtualMemLimit Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.SetVirtualMemLimit
api_location: mscoree.dll
api_type: COM
f1_keywords: SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff3b5a8ba559530561503a3678a37ac0b9480907
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="1a860-102">IGCHost::SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a860-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="1a860-103">En büyük çalışma zamanı'nın sanal bellek boyutunu belirler.</span><span class="sxs-lookup"><span data-stu-id="1a860-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a860-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a860-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a860-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a860-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="1a860-106">[in] Çalışma zamanı'nın sanal bellek megabayt cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="1a860-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a860-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a860-107">Remarks</span></span>  
 <span data-ttu-id="1a860-108">En büyük çalışma zamanı'nın sanal bellek boyutunu dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a860-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a860-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a860-109">Requirements</span></span>  
 <span data-ttu-id="1a860-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a860-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a860-111">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="1a860-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1a860-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1a860-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a860-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a860-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a860-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a860-114">See Also</span></span>  
 [<span data-ttu-id="1a860-115">Igchost arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a860-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
