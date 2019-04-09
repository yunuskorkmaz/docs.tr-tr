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
ms.openlocfilehash: 1291d4e69843db7bd90af07291da415220d98807
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131364"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="79e58-102">ICorRuntimeHost::SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79e58-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="79e58-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="79e58-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79e58-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79e58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79e58-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="79e58-106">[out] Dışarı geçiş fiber gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="79e58-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e58-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79e58-107">Requirements</span></span>  
 <span data-ttu-id="79e58-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79e58-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79e58-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79e58-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79e58-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="79e58-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79e58-111">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="79e58-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e58-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79e58-112">See also</span></span>

- [<span data-ttu-id="79e58-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79e58-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
