---
title: ICorRuntimeHost::SwitchInLogicalThreadState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d12555fb53a6c1b21f161402da77860adcf0a4b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478914"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="e0350-102">ICorRuntimeHost::SwitchInLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0350-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="e0350-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="e0350-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0350-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0350-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0350-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0350-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="e0350-106">[in] Kullanılacak fiber gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="e0350-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0350-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0350-107">Requirements</span></span>  
 <span data-ttu-id="e0350-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0350-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0350-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0350-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0350-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e0350-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0350-111">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e0350-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0350-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0350-112">See also</span></span>
- [<span data-ttu-id="e0350-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0350-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
