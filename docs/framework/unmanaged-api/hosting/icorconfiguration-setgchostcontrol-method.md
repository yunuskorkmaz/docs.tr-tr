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
ms.openlocfilehash: 50a92058e8a394b95c690d19f1bafdddbed8246a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135999"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="0a470-102">ICorConfiguration::SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a470-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="0a470-103">Sanal bellek sınırlarını değiştirmek için ana istemek için atık toplayıcı tarafından kullanılmak üzere geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0a470-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a470-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a470-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a470-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a470-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="0a470-106">[in] Bir işaretçi bir [Igchostcontrol](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) sanal bellek sınırlarını değiştirmek için ana istemek çöp toplayıcı sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="0a470-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a470-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a470-107">Requirements</span></span>  
 <span data-ttu-id="0a470-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a470-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a470-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a470-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a470-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0a470-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a470-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a470-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a470-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a470-112">See also</span></span>

- [<span data-ttu-id="0a470-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a470-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
