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
ms.openlocfilehash: a4590bcd96226a713ff5535a8bc802c2116f862a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690141"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="9e9ca-102">ICorRuntimeHost::SwitchInLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e9ca-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>

<span data-ttu-id="9e9ca-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="9e9ca-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e9ca-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9e9ca-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e9ca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e9ca-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="9e9ca-106">'ndaki Kullanılacak fiber öğesini gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="9e9ca-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e9ca-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e9ca-107">Requirements</span></span>  

 <span data-ttu-id="9e9ca-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e9ca-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e9ca-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e9ca-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e9ca-110">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9e9ca-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e9ca-111">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="9e9ca-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e9ca-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e9ca-112">See also</span></span>

- [<span data-ttu-id="9e9ca-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e9ca-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
