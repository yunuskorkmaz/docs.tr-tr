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
ms.openlocfilehash: 37c02b878cd52034603ab6cafe4d8aaca594cbe9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126882"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="a898b-102">IAppDomainBinding::OnAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a898b-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="a898b-103">Bir uygulama etki alanının oluşturulduğunu konağa bildirmek için ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a898b-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a898b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a898b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a898b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a898b-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="a898b-106">'ndaki Yeni uygulama etki alanını temsil eden bir [IUnknown](/cpp/atl/iunknown) arabirimi nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a898b-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a898b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a898b-107">Requirements</span></span>  
 <span data-ttu-id="a898b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a898b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a898b-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a898b-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a898b-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a898b-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a898b-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a898b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a898b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a898b-112">See also</span></span>

- [<span data-ttu-id="a898b-113">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a898b-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
