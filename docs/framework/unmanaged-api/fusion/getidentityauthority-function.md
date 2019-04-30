---
title: GetIdentityAuthority İşlevi
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3090887d3c670b2784b7b40c7d63832715596c3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697608"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="c8507-102">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="c8507-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="c8507-103">Bir işaretçi alır bir [Iıdentityauthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) kod nesneleri tuşları yöneten bir örneği.</span><span class="sxs-lookup"><span data-stu-id="c8507-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8507-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8507-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8507-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8507-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="c8507-106">[out] Döndürülen `IIdentityAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8507-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8507-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8507-107">Requirements</span></span>  
 <span data-ttu-id="c8507-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8507-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8507-109">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="c8507-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c8507-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8507-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8507-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8507-111">See also</span></span>

- [<span data-ttu-id="c8507-112">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8507-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [<span data-ttu-id="c8507-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c8507-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
