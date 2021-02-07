---
description: 'Daha fazla bilgi edinin: IGCHost:: SetVirtualMemLimit Yöntemi'
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
ms.openlocfilehash: 62cd9e2d84e51f0544e464bdbf49c50af8086546
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709444"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="97774-103">IGCHost::SetVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97774-103">IGCHost::SetVirtualMemLimit Method</span></span>

<span data-ttu-id="97774-104">Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="97774-104">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97774-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97774-105">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97774-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97774-106">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="97774-107">'ndaki Çalışma zamanının sanal belleğinin megabayt cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="97774-107">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97774-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97774-108">Remarks</span></span>  

 <span data-ttu-id="97774-109">Çalışma zamanının sanal belleğinin en büyük boyutu dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="97774-109">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97774-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97774-110">Requirements</span></span>  

 <span data-ttu-id="97774-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97774-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97774-112">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="97774-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="97774-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="97774-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97774-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97774-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97774-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97774-115">See also</span></span>

- [<span data-ttu-id="97774-116">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97774-116">IGCHost Interface</span></span>](igchost-interface.md)
