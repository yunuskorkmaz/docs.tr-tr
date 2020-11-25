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
ms.openlocfilehash: ca528bdbd9662db373d1beeece803d6c43728f2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698617"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="a9bc0-102">IAssemblyName::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9bc0-102">IAssemblyName::Clone Method</span></span>

<span data-ttu-id="a9bc0-103">Bu [IAssemblyName](iassemblyname-interface.md) nesnesinin basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9bc0-103">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bc0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a9bc0-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9bc0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9bc0-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="a9bc0-106">dışı Bu nesnenin döndürülen kopyası `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="a9bc0-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9bc0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9bc0-107">Requirements</span></span>  

 <span data-ttu-id="a9bc0-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9bc0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9bc0-109">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a9bc0-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a9bc0-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9bc0-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bc0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9bc0-111">See also</span></span>

- [<span data-ttu-id="a9bc0-112">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9bc0-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
