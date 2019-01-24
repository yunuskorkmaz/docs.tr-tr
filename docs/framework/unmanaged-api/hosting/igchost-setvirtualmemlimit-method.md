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
ms.openlocfilehash: d38b174a7e959647a9c1f5287b8acbbcdaf5ca7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564285"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="73bf2-102">IGCHost::SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73bf2-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="73bf2-103">Çalışma zamanının sanal bellek en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="73bf2-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73bf2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73bf2-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73bf2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73bf2-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="73bf2-106">[in] Çalışma zamanının sanal bellek megabayt cinsinden maksimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="73bf2-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73bf2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73bf2-107">Remarks</span></span>  
 <span data-ttu-id="73bf2-108">Çalışma zamanının sanal bellek en büyük boyutunu dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="73bf2-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73bf2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73bf2-109">Requirements</span></span>  
 <span data-ttu-id="73bf2-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73bf2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73bf2-111">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="73bf2-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="73bf2-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="73bf2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73bf2-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73bf2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bf2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73bf2-114">See also</span></span>
- [<span data-ttu-id="73bf2-115">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73bf2-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
