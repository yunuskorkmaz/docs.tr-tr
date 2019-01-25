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
ms.openlocfilehash: 1194ae12710ce9ef6d5f53e584493eec0541f3fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569722"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="0fb05-102">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="0fb05-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="0fb05-103">Bir işaretçi alır bir [Iıdentityauthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) kod nesneleri tuşları yöneten bir örneği.</span><span class="sxs-lookup"><span data-stu-id="0fb05-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0fb05-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fb05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0fb05-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="0fb05-106">[out] Döndürülen `IIdentityAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0fb05-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fb05-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0fb05-107">Requirements</span></span>  
 <span data-ttu-id="0fb05-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fb05-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fb05-109">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="0fb05-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0fb05-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fb05-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb05-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fb05-111">See also</span></span>
- [<span data-ttu-id="0fb05-112">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0fb05-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [<span data-ttu-id="0fb05-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0fb05-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
