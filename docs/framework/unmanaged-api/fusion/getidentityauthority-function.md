---
description: GetIdentityAuthority Işlevi hakkında daha fazla bilgi edinin
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
ms.openlocfilehash: 5126aa9b319af41f7ecd30845a9f74ba69016588
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761004"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="e2462-103">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2462-103">GetIdentityAuthority Function</span></span>

<span data-ttu-id="e2462-104">Kod nesneleri için anahtarları yöneten bir [IIdentityAuthority](iidentityauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e2462-104">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2462-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2462-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2462-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2462-106">Parameters</span></span>  

 `ppIIdentityAuthority`  
 <span data-ttu-id="e2462-107">dışı Döndürülen `IIdentityAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2462-107">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2462-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2462-108">Requirements</span></span>  

 <span data-ttu-id="e2462-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2462-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2462-110">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="e2462-110">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e2462-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2462-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2462-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2462-112">See also</span></span>

- [<span data-ttu-id="e2462-113">IIdentityAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2462-113">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="e2462-114">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e2462-114">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
