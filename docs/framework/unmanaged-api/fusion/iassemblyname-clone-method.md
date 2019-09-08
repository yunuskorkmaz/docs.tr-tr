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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c71616d261f145574d580b68793ec91bb4ea3f42
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796646"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="94f0a-102">IAssemblyName::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94f0a-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="94f0a-103">Bu [IAssemblyName](iassemblyname-interface.md) nesnesinin basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94f0a-103">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94f0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94f0a-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94f0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94f0a-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="94f0a-106">dışı Bu `IAssemblyName` nesnenin döndürülen kopyası.</span><span class="sxs-lookup"><span data-stu-id="94f0a-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94f0a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94f0a-107">Requirements</span></span>  
 <span data-ttu-id="94f0a-108">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94f0a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94f0a-109">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="94f0a-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="94f0a-110">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94f0a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f0a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94f0a-111">See also</span></span>

- [<span data-ttu-id="94f0a-112">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94f0a-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
