---
title: "IAssemblyName::SetProperty Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.SetProperty
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60ef27021ec3431c90086e0dfbae56bb6e6ccc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="5f8d2-102">IAssemblyName::SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f8d2-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="5f8d2-103">Belirtilen özellik tanımlayıcısı tarafından başvurulan özelliğinin değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f8d2-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f8d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f8d2-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f8d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f8d2-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="5f8d2-106">[in] Değeri ayarlanacak özellik benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5f8d2-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="5f8d2-107">[in] Tarafından başvurulan özelliğini ayarlamak olan değer `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="5f8d2-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="5f8d2-108">[in] Bayt olarak boyutu, `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="5f8d2-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f8d2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f8d2-109">Requirements</span></span>  
 <span data-ttu-id="5f8d2-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f8d2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f8d2-111">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5f8d2-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5f8d2-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f8d2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f8d2-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f8d2-113">See Also</span></span>  
 [<span data-ttu-id="5f8d2-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f8d2-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
