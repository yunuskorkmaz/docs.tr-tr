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
ms.openlocfilehash: d830635b911fa5d80382e432f283c455c41af7a8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762688"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="723f2-102">ICorRuntimeHost::SwitchInLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="723f2-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="723f2-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="723f2-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723f2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="723f2-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="723f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="723f2-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="723f2-106">'ndaki Kullanılacak fiber öğesini gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="723f2-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="723f2-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="723f2-107">Requirements</span></span>  
 <span data-ttu-id="723f2-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="723f2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="723f2-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="723f2-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="723f2-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="723f2-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="723f2-111">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="723f2-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723f2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="723f2-112">See also</span></span>

- [<span data-ttu-id="723f2-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="723f2-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
