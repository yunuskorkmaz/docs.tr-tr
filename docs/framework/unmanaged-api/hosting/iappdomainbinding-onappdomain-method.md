---
title: IAppDomainBinding::OnAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2903395f5f834f2435b14d0b3f3e8bfe24af2867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183059"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="ae79e-102">IAppDomainBinding::OnAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae79e-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="ae79e-103">Ortak dil çalışma zamanı tarafından ana bilgisayara bir uygulama etki alanı oluşturulduğunu bildirmek için (CLR) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ae79e-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae79e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae79e-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae79e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae79e-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="ae79e-106">[in] Bir işaretçi bir [IUnknown](/cpp/atl/iunknown) yeni uygulama etki alanını temsil eden arabirim nesne.</span><span class="sxs-lookup"><span data-stu-id="ae79e-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae79e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae79e-107">Requirements</span></span>  
 <span data-ttu-id="ae79e-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae79e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae79e-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae79e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae79e-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ae79e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ae79e-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ae79e-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae79e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae79e-112">See also</span></span>

- [<span data-ttu-id="ae79e-113">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae79e-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
