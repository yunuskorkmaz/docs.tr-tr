---
title: ICorConfiguration::SetGCHostControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a64922e1fe069d682f7ebc51040d06231a8b49c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484361"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="9efb0-102">ICorConfiguration::SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9efb0-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="9efb0-103">Sanal bellek sınırlarını değiştirmek için ana istemek için atık toplayıcı tarafından kullanılmak üzere geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9efb0-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9efb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9efb0-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9efb0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9efb0-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="9efb0-106">[in] Bir işaretçi bir [Igchostcontrol](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) sanal bellek sınırlarını değiştirmek için ana istemek çöp toplayıcı sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="9efb0-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9efb0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9efb0-107">Requirements</span></span>  
 <span data-ttu-id="9efb0-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9efb0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9efb0-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9efb0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9efb0-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9efb0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9efb0-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9efb0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9efb0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9efb0-112">See also</span></span>
- [<span data-ttu-id="9efb0-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9efb0-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
