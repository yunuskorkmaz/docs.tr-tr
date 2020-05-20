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
ms.openlocfilehash: 2d5dbd003d0ea5decae0025d47e6bd5c1fb1ed4a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617080"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="13f6f-102">IAppDomainBinding::OnAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13f6f-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="13f6f-103">Bir uygulama etki alanının oluşturulduğunu konağa bildirmek için ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="13f6f-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f6f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13f6f-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13f6f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13f6f-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="13f6f-106">'ndaki Yeni uygulama etki alanını temsil eden bir [IUnknown](/cpp/atl/iunknown) arabirimi nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13f6f-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13f6f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13f6f-107">Requirements</span></span>  
 <span data-ttu-id="13f6f-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f6f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f6f-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13f6f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13f6f-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="13f6f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13f6f-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f6f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f6f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13f6f-112">See also</span></span>

- [<span data-ttu-id="13f6f-113">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13f6f-113">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
