---
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
ms.openlocfilehash: 64751032c017473ffd82248b310b14c087f74129
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727841"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="0ff5b-102">ITypeName::GetModifiers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ff5b-102">ITypeName::GetModifiers Method</span></span>

<span data-ttu-id="0ff5b-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="0ff5b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ff5b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ff5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0ff5b-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ff5b-105">Requirements</span></span>  

 <span data-ttu-id="0ff5b-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ff5b-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ff5b-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ff5b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ff5b-108">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0ff5b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ff5b-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ff5b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff5b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ff5b-110">See also</span></span>

- [<span data-ttu-id="0ff5b-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0ff5b-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
