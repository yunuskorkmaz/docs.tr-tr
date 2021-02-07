---
description: ': IAppDomainBinding:: OnAppDomain Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: de7f37152261a6fe829026607cf135f3ea0b4a84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760608"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="7914e-103">IAppDomainBinding::OnAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7914e-103">IAppDomainBinding::OnAppDomain Method</span></span>

<span data-ttu-id="7914e-104">Bir uygulama etki alanının oluşturulduğunu konağa bildirmek için ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="7914e-104">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7914e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7914e-105">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7914e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7914e-106">Parameters</span></span>  

 `pAppdomain`  
 <span data-ttu-id="7914e-107">'ndaki Yeni uygulama etki alanını temsil eden bir [IUnknown](/cpp/atl/iunknown) arabirimi nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7914e-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7914e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7914e-108">Requirements</span></span>  

 <span data-ttu-id="7914e-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7914e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7914e-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7914e-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7914e-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7914e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7914e-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7914e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7914e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7914e-113">See also</span></span>

- [<span data-ttu-id="7914e-114">IAppDomainBinding Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7914e-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
