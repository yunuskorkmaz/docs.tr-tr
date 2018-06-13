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
ms.openlocfilehash: 71b9eb6cc5640913c5723f088034d9bcd86c4a43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428879"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="bffec-102">IAssemblyName::GetVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="bffec-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="bffec-103">Bu tarafından başvurulan derlemenin sürüm bilgisi alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bffec-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bffec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bffec-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bffec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bffec-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="bffec-106">[out] Yüksek 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="bffec-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="bffec-107">[out] Düşük 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="bffec-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bffec-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bffec-108">Requirements</span></span>  
 <span data-ttu-id="bffec-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bffec-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bffec-110">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bffec-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bffec-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bffec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffec-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bffec-112">See Also</span></span>  
 [<span data-ttu-id="bffec-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bffec-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
