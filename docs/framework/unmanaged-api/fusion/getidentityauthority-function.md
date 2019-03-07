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
ms.openlocfilehash: 09d6284d7042dfebee004c4cb18d8ef3752c325c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496995"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="31513-102">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="31513-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="31513-103">Bir işaretçi alır bir [Iıdentityauthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) kod nesneleri tuşları yöneten bir örneği.</span><span class="sxs-lookup"><span data-stu-id="31513-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31513-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31513-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="31513-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31513-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="31513-106">[out] Döndürülen `IIdentityAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31513-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31513-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31513-107">Requirements</span></span>  
 <span data-ttu-id="31513-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31513-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31513-109">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="31513-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="31513-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31513-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31513-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31513-111">See also</span></span>
- [<span data-ttu-id="31513-112">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31513-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [<span data-ttu-id="31513-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="31513-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
