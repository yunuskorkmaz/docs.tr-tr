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
ms.openlocfilehash: e41ead54b50b8b28ebd9ee9c97d15ca6c71e7313
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690128"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="b2949-102">ICorRuntimeHost::SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2949-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>

<span data-ttu-id="b2949-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="b2949-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2949-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2949-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2949-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2949-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="b2949-106">dışı Dışarı aktarılmakta olan fiber öğesini gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="b2949-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2949-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2949-107">Requirements</span></span>  

 <span data-ttu-id="b2949-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2949-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2949-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b2949-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2949-110">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b2949-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2949-111">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="b2949-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2949-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2949-112">See also</span></span>

- [<span data-ttu-id="b2949-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2949-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
