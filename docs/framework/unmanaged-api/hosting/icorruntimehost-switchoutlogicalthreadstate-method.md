---
description: ': ICorRuntimeHost:: SwitchOutLogicalThreadState Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b4190ebe6b2c260f85afd8dd17127d0c63dca6c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799453"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="6adda-103">ICorRuntimeHost::SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6adda-103">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>

<span data-ttu-id="6adda-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="6adda-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6adda-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6adda-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6adda-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6adda-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="6adda-107">dışı Dışarı aktarılmakta olan fiber öğesini gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="6adda-107">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6adda-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6adda-108">Requirements</span></span>  

 <span data-ttu-id="6adda-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6adda-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6adda-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6adda-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6adda-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6adda-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6adda-112">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="6adda-112">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6adda-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6adda-113">See also</span></span>

- [<span data-ttu-id="6adda-114">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6adda-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
