---
title: IAssemblyName::SetProperty Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40953d03904e3268770c8a1b6e212873ec66d2dd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761842"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="ad45d-102">IAssemblyName::SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad45d-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="ad45d-103">Belirtilen özellik tanımlayıcısı tarafından başvurulan özelliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ad45d-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad45d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad45d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad45d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad45d-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="ad45d-106">[in] Değeri ayarlanacak özelliğin benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ad45d-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="ad45d-107">[in] Tarafından başvurulan özelliğini ayarlamak olan değer `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="ad45d-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="ad45d-108">[in] Bayt cinsinden boyutu, `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="ad45d-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad45d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad45d-109">Requirements</span></span>  
 <span data-ttu-id="ad45d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad45d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad45d-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ad45d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ad45d-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad45d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad45d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad45d-113">See also</span></span>

- [<span data-ttu-id="ad45d-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad45d-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
