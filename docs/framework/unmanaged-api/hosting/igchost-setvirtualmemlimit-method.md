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
ms.openlocfilehash: c060e4883335a8318970b5fbd74bf72c9e13f5bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134868"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="e2561-102">IGCHost::SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2561-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="e2561-103">Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e2561-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2561-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2561-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2561-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2561-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="e2561-106">'ndaki Çalışma zamanının sanal belleğinin megabayt cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="e2561-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2561-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2561-107">Remarks</span></span>  
 <span data-ttu-id="e2561-108">Çalışma zamanının sanal belleğinin en büyük boyutu dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e2561-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2561-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2561-109">Requirements</span></span>  
 <span data-ttu-id="e2561-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2561-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2561-111">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="e2561-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e2561-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e2561-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2561-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2561-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2561-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2561-114">See also</span></span>

- [<span data-ttu-id="e2561-115">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2561-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
