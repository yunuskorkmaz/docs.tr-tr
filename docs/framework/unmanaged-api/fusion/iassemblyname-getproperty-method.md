---
title: IAssemblyName::GetProperty Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5ddc2646b560814adef01f2508f3792abe13c1d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744531"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="b2bfa-102">IAssemblyName::GetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2bfa-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="b2bfa-103">Belirtilen özellik tanımlayıcısı tarafından başvurulduğundan özelliği için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b2bfa-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2bfa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2bfa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2bfa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2bfa-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="b2bfa-106">[in] İstenen özellik için benzersiz tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b2bfa-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="b2bfa-107">[out] Özelliği döndürülen veriler.</span><span class="sxs-lookup"><span data-stu-id="b2bfa-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="b2bfa-108">[out içinde] Bayt cinsinden boyutu, `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="b2bfa-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2bfa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2bfa-109">Requirements</span></span>  
 <span data-ttu-id="b2bfa-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2bfa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2bfa-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b2bfa-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b2bfa-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2bfa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bfa-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2bfa-113">See also</span></span>

- [<span data-ttu-id="b2bfa-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2bfa-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
