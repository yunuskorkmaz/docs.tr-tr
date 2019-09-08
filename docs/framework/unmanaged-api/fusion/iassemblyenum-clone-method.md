---
title: IAssemblyEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::Clone
helpviewer_keywords:
- Clone method, IAssemblyEnum interface [.NET Framework fusion]
- IAssemblyEnum::Clone method [.NET Framework fusion]
ms.assetid: 0014bb66-590c-486c-9ade-f2133905cd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 141e6e303933c46a85adf08339856f8964b21f4e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796700"
---
# <a name="iassemblyenumclone-method"></a><span data-ttu-id="441f4-102">IAssemblyEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="441f4-102">IAssemblyEnum::Clone Method</span></span>
<span data-ttu-id="441f4-103">Bu [IAssemblyEnum](iassemblyenum-interface.md) nesnesinin basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="441f4-103">Creates a shallow copy of this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="441f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="441f4-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="441f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="441f4-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="441f4-106">dışı Kopyaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="441f4-106">[out] A pointer to the copy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="441f4-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="441f4-107">Requirements</span></span>  
 <span data-ttu-id="441f4-108">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="441f4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="441f4-109">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="441f4-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="441f4-110">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="441f4-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441f4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="441f4-111">See also</span></span>

- [<span data-ttu-id="441f4-112">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="441f4-112">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
