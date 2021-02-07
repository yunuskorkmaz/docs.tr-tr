---
description: ': ITypeName:: GetModifiers yöntemi hakkında daha fazla bilgi edinin'
title: ITypeName::GetModifiers Yöntemi
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: 3c44d569255656f95ccceec0462d09044b46679b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753724"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="c4dfb-103">ITypeName::GetModifiers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4dfb-103">ITypeName::GetModifiers Method</span></span>

<span data-ttu-id="c4dfb-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="c4dfb-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4dfb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4dfb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c4dfb-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4dfb-106">Requirements</span></span>  

 <span data-ttu-id="c4dfb-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4dfb-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4dfb-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4dfb-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4dfb-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c4dfb-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4dfb-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4dfb-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4dfb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4dfb-111">See also</span></span>

- [<span data-ttu-id="c4dfb-112">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c4dfb-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
