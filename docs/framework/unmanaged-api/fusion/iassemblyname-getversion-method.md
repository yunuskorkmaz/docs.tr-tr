---
title: IAssemblyName::GetVersion Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a28cb9f1fd2e12cd750d4eeb8db6c2d7a181b414
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197431"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="d65e4-102">IAssemblyName::GetVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="d65e4-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="d65e4-103">Bu tarafından başvurulan derlemenin sürüm bilgilerini alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="d65e4-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d65e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d65e4-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d65e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d65e4-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="d65e4-106">[out] Yüksek 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="d65e4-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="d65e4-107">[out] Düşük 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="d65e4-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d65e4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d65e4-108">Requirements</span></span>  
 <span data-ttu-id="d65e4-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d65e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d65e4-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d65e4-110">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="d65e4-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d65e4-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d65e4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d65e4-112">See also</span></span>

- [<span data-ttu-id="d65e4-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d65e4-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
