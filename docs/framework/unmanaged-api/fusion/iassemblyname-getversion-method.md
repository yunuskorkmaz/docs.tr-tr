---
title: IAssemblyName::GetVersion Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetVersion
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a843ca1ebc12b0ae9aaf1d9dbb4e5d845fb61fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="b9712-102">IAssemblyName::GetVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="b9712-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="b9712-103">Bu tarafından başvurulan derlemenin sürüm bilgisi alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b9712-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9712-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9712-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9712-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9712-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="b9712-106">[out] Yüksek 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="b9712-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="b9712-107">[out] Düşük 32 bit sürümü.</span><span class="sxs-lookup"><span data-stu-id="b9712-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9712-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9712-108">Requirements</span></span>  
 <span data-ttu-id="b9712-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9712-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9712-110">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b9712-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b9712-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9712-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9712-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9712-112">See Also</span></span>  
 [<span data-ttu-id="b9712-113">Iassemblyname arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9712-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
