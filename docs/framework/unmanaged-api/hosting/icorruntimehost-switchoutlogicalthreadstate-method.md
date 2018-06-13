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
ms.openlocfilehash: ff3bd9345825b5e7a4ccb41cd260b447b74cede3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437956"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="4dcd0-102">ICorRuntimeHost::SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4dcd0-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="4dcd0-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcd0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4dcd0-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4dcd0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4dcd0-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="4dcd0-106">[out] Giden geçiş fiber gösterir tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dcd0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4dcd0-107">Requirements</span></span>  
 <span data-ttu-id="4dcd0-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dcd0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dcd0-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4dcd0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4dcd0-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4dcd0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dcd0-111">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="4dcd0-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcd0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-112">See Also</span></span>  
 [<span data-ttu-id="4dcd0-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4dcd0-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
