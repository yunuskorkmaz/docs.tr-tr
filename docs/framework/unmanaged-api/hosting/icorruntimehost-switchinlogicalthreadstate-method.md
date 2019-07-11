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
ms.openlocfilehash: 44973bcf98eb776735e0144ff1c2747b1445c5d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770887"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="a29bb-102">ICorRuntimeHost::SwitchInLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a29bb-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="a29bb-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="a29bb-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a29bb-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a29bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a29bb-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="a29bb-106">[in] Kullanılacak fiber gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="a29bb-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a29bb-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a29bb-107">Requirements</span></span>  
 <span data-ttu-id="a29bb-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a29bb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a29bb-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a29bb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a29bb-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a29bb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a29bb-111">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a29bb-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29bb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a29bb-112">See also</span></span>

- [<span data-ttu-id="a29bb-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a29bb-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
