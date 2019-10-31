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
ms.openlocfilehash: b86828e01fb00b12feff2ed451793c240e16e240
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134388"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="e165a-102">IAssemblyName::GetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e165a-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="e165a-103">Belirtilen özellik tanımlayıcısının başvurduğu özelliğe bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e165a-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e165a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e165a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e165a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e165a-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="e165a-106">'ndaki İstenen özellik için benzersiz tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="e165a-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="e165a-107">dışı Döndürülen özellik verileri.</span><span class="sxs-lookup"><span data-stu-id="e165a-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="e165a-108">[in, out] `pvProperty`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e165a-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e165a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e165a-109">Requirements</span></span>  
 <span data-ttu-id="e165a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e165a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e165a-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e165a-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e165a-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e165a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e165a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e165a-113">See also</span></span>

- [<span data-ttu-id="e165a-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e165a-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
