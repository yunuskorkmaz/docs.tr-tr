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
ms.openlocfilehash: f29246bdb929c8eaf1ebce726164d5cd2269b9f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796867"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="0cbed-102">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="0cbed-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="0cbed-103">Kod nesneleri için anahtarları yöneten bir [IIdentityAuthority](iidentityauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0cbed-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cbed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cbed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cbed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cbed-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="0cbed-106">dışı Döndürülen `IIdentityAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cbed-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cbed-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cbed-107">Requirements</span></span>  
 <span data-ttu-id="0cbed-108">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cbed-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cbed-109">**Üst bilgi** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="0cbed-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0cbed-110">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cbed-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cbed-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cbed-111">See also</span></span>

- [<span data-ttu-id="0cbed-112">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cbed-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="0cbed-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0cbed-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
