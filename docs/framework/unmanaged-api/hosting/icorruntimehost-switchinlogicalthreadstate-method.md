---
description: ': ICorRuntimeHost:: SwitchInLogicalThreadState Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3e375379cc5d6af7c3a8fb8d64a40a389e0f9dcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789573"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="1ffe1-103">ICorRuntimeHost::SwitchInLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ffe1-103">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>

<span data-ttu-id="1ffe1-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffe1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ffe1-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ffe1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ffe1-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="1ffe1-107">'ndaki Kullanılacak fiber öğesini gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-107">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ffe1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ffe1-108">Requirements</span></span>  

 <span data-ttu-id="1ffe1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ffe1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ffe1-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1ffe1-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ffe1-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1ffe1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ffe1-112">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1ffe1-112">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffe1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-113">See also</span></span>

- [<span data-ttu-id="1ffe1-114">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ffe1-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
