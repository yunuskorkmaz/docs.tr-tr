---
title: "GetAssemblyIdentityFromFile İşlevi"
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
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56d7fb4ee74e40ecd29ee276665ff43ab9fd56be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="e501e-102">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="e501e-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="e501e-103">Bir işaretçi alır bir `IUnknown` belirtilen nesnesiyle `IID` belirtilen dosya yolunda derlemesindeki.</span><span class="sxs-lookup"><span data-stu-id="e501e-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e501e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e501e-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e501e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e501e-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="e501e-106">[in] İstenen derleme için geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="e501e-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="e501e-107">[in] `IID` Döndürmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="e501e-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="e501e-108">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e501e-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e501e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e501e-109">Requirements</span></span>  
 <span data-ttu-id="e501e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e501e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e501e-111">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e501e-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e501e-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e501e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e501e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e501e-113">See Also</span></span>  
 <span data-ttu-id="e501e-114"><<!--zzxref:IUnknown --> `IUnknown`></span><span class="sxs-lookup"><span data-stu-id="e501e-114"><<!--zzxref:IUnknown --> `IUnknown`></span></span>  
 [<span data-ttu-id="e501e-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e501e-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
