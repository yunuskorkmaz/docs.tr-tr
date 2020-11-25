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
ms.openlocfilehash: e9631211993afbfe968c7122828251746f15c3f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732138"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="3f91a-102">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f91a-102">GetIdentityAuthority Function</span></span>

<span data-ttu-id="3f91a-103">Kod nesneleri için anahtarları yöneten bir [IIdentityAuthority](iidentityauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="3f91a-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f91a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3f91a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f91a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f91a-105">Parameters</span></span>  

 `ppIIdentityAuthority`  
 <span data-ttu-id="3f91a-106">dışı Döndürülen `IIdentityAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f91a-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f91a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f91a-107">Requirements</span></span>  

 <span data-ttu-id="3f91a-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f91a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f91a-109">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="3f91a-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3f91a-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f91a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f91a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f91a-111">See also</span></span>

- [<span data-ttu-id="3f91a-112">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f91a-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="3f91a-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3f91a-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
