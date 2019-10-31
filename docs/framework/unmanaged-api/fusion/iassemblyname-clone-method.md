---
title: IAssemblyName::Clone Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 1236a574a85c01e3e1be5df9644bd04bbf0753ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134415"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="67828-102">IAssemblyName::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67828-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="67828-103">Bu [IAssemblyName](iassemblyname-interface.md) nesnesinin basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67828-103">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67828-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67828-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67828-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67828-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="67828-106">dışı Bu `IAssemblyName` nesnesinin döndürülen kopyası.</span><span class="sxs-lookup"><span data-stu-id="67828-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67828-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67828-107">Requirements</span></span>  
 <span data-ttu-id="67828-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67828-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67828-109">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="67828-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="67828-110">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67828-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67828-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67828-111">See also</span></span>

- [<span data-ttu-id="67828-112">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67828-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
