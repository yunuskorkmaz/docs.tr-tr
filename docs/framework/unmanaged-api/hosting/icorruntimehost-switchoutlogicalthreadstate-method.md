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
ms.openlocfilehash: f32381dc40a744157e46780e59b83efd63e58dcb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762649"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="ed489-102">ICorRuntimeHost::SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed489-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="ed489-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="ed489-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed489-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ed489-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed489-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed489-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="ed489-106">dışı Dışarı aktarılmakta olan fiber öğesini gösteren tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="ed489-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed489-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed489-107">Requirements</span></span>  
 <span data-ttu-id="ed489-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed489-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed489-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ed489-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed489-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ed489-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed489-111">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="ed489-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed489-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed489-112">See also</span></span>

- [<span data-ttu-id="ed489-113">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed489-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
