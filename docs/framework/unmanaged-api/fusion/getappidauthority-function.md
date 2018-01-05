---
title: "GetAppIdAuthority İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: GetAppIdAuthority
helpviewer_keywords: GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e89624feb04050534b917b865d5cb53b8c4cf58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getappidauthority-function"></a><span data-ttu-id="db0a6-102">GetAppIdAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="db0a6-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="db0a6-103">Bir işaretçi alır bir [Iappıdauthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) uygulama kimlikleri ve başvurular tuşları yönetir örneği.</span><span class="sxs-lookup"><span data-stu-id="db0a6-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db0a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db0a6-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db0a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db0a6-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="db0a6-106">[out] Döndürülen `IAppIdAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db0a6-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db0a6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db0a6-107">Requirements</span></span>  
 <span data-ttu-id="db0a6-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db0a6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db0a6-109">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="db0a6-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="db0a6-110">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db0a6-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0a6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db0a6-111">See Also</span></span>  
 [<span data-ttu-id="db0a6-112">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db0a6-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 [<span data-ttu-id="db0a6-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="db0a6-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
