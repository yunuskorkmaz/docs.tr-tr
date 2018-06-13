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
ms.openlocfilehash: 5db040f6db078b211043c547eed823c9b495ac97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431328"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="6e32f-102">IAppDomainBinding::OnAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e32f-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="6e32f-103">Ortak dil çalışma zamanı tarafından ana uygulama etki alanı oluşturulduğunu bildirmek için (CLR) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6e32f-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e32f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e32f-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e32f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e32f-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="6e32f-106">[in] Bir işaretçi bir [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) yeni uygulama etki alanı temsil eden arabirim nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6e32f-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e32f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e32f-107">Requirements</span></span>  
 <span data-ttu-id="6e32f-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e32f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e32f-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e32f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e32f-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6e32f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e32f-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e32f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e32f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e32f-112">See Also</span></span>  
 [<span data-ttu-id="6e32f-113">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e32f-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
