---
title: "IAssemblyName::Clone Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 306263bcb27141eadc0943c0045a5f71285436e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="b5495-102">IAssemblyName::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5495-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="b5495-103">Bu basit bir kopyasını oluşturur [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b5495-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5495-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5495-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5495-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5495-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b5495-106">[out] Bu döndürülen kopyasını `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b5495-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5495-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5495-107">Requirements</span></span>  
 <span data-ttu-id="b5495-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5495-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5495-109">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b5495-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b5495-110">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5495-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5495-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5495-111">See Also</span></span>  
 [<span data-ttu-id="b5495-112">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5495-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
