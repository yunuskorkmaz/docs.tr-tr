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
ms.openlocfilehash: e5b5f7ce6a4ce8f542b3c49fe4749bfde23ecf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744493"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="828ad-102">IAssemblyName::GetVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="828ad-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="828ad-103">Bu tarafından başvurulan derlemenin sürüm bilgilerini alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="828ad-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828ad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="828ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="828ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="828ad-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="828ad-106">[out] Yüksek 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="828ad-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="828ad-107">[out] Düşük 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="828ad-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="828ad-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="828ad-108">Requirements</span></span>  
 <span data-ttu-id="828ad-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="828ad-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="828ad-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="828ad-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="828ad-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="828ad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828ad-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="828ad-112">See also</span></span>

- [<span data-ttu-id="828ad-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="828ad-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
