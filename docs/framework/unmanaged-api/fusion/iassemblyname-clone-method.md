---
title: IAssemblyName::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a6d0036a1f4c499505743fd15a115f870e9cb50
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492406"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="af247-102">IAssemblyName::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af247-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="af247-103">Bu basit bir kopyasını oluşturur [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="af247-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af247-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af247-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af247-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af247-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="af247-106">[out] Döndürülen bu kopyasını `IAssemblyName` nesne.</span><span class="sxs-lookup"><span data-stu-id="af247-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af247-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af247-107">Requirements</span></span>  
 <span data-ttu-id="af247-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af247-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af247-109">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="af247-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="af247-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af247-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af247-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af247-111">See also</span></span>
- [<span data-ttu-id="af247-112">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af247-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
