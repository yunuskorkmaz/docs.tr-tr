---
title: ICorRuntimeHost::SwitchOutLogicalThreadState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 291fb64bd86c1670945136e5ec7f586496f77d49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730223"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="83d65-102">ICorRuntimeHost::SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83d65-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="83d65-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="83d65-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83d65-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83d65-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83d65-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="83d65-106">[out] Dışarı geçiş fiber gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="83d65-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83d65-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83d65-107">Requirements</span></span>  
 <span data-ttu-id="83d65-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d65-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d65-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83d65-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83d65-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="83d65-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83d65-111">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="83d65-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d65-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83d65-112">See also</span></span>
- [<span data-ttu-id="83d65-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83d65-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
