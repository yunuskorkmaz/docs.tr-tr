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
ms.openlocfilehash: 9898b760edbb149afcd6bf957a30d0a47287485b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687827"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="6bf62-102">IGCHost::SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bf62-102">IGCHost::SetVirtualMemLimit Method</span></span>

<span data-ttu-id="6bf62-103">Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6bf62-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bf62-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6bf62-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bf62-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bf62-105">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="6bf62-106">'ndaki Çalışma zamanının sanal belleğinin megabayt cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="6bf62-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bf62-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bf62-107">Remarks</span></span>  

 <span data-ttu-id="6bf62-108">Çalışma zamanının sanal belleğinin en büyük boyutu dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6bf62-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bf62-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bf62-109">Requirements</span></span>  

 <span data-ttu-id="6bf62-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bf62-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bf62-111">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="6bf62-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6bf62-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6bf62-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bf62-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bf62-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf62-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bf62-114">See also</span></span>

- [<span data-ttu-id="6bf62-115">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bf62-115">IGCHost Interface</span></span>](igchost-interface.md)
