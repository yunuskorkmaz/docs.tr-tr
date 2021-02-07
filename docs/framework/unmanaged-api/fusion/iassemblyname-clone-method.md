---
description: 'Şu konuda daha fazla bilgi edinin: IAssemblyName:: Clone yöntemi'
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
ms.openlocfilehash: b1d8ba2aec73565e9f6acaa44a5ef3731baa3af9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760790"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="f1aab-103">IAssemblyName::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1aab-103">IAssemblyName::Clone Method</span></span>

<span data-ttu-id="f1aab-104">Bu [IAssemblyName](iassemblyname-interface.md) nesnesinin basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1aab-104">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1aab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1aab-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1aab-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1aab-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="f1aab-107">dışı Bu nesnenin döndürülen kopyası `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="f1aab-107">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1aab-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1aab-108">Requirements</span></span>  

 <span data-ttu-id="f1aab-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1aab-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1aab-110">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f1aab-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f1aab-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1aab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1aab-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1aab-112">See also</span></span>

- [<span data-ttu-id="f1aab-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1aab-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
