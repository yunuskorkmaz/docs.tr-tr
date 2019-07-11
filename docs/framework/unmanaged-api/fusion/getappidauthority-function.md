---
title: GetAppIdAuthority İşlevi
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 536f3249593333234f7f09921007b483fb80cf79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778594"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="9d6f5-102">GetAppIdAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d6f5-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="9d6f5-103">Bir işaretçi alır bir [Iappıdauthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) uygulama kimlikleri ve başvurular için anahtarları yöneten bir örneği.</span><span class="sxs-lookup"><span data-stu-id="9d6f5-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d6f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d6f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d6f5-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="9d6f5-106">[out] Döndürülen `IAppIdAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d6f5-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6f5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d6f5-107">Requirements</span></span>  
 <span data-ttu-id="9d6f5-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6f5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6f5-109">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="9d6f5-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9d6f5-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6f5-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6f5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d6f5-111">See also</span></span>

- [<span data-ttu-id="9d6f5-112">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d6f5-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [<span data-ttu-id="9d6f5-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9d6f5-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
