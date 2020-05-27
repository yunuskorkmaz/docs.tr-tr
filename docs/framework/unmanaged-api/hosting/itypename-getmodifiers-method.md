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
ms.openlocfilehash: 8544b8d7b1f23853465bbb2aea697dfe021d77f2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842185"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="30d87-102">ITypeName::GetModifiers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30d87-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="30d87-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="30d87-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30d87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="30d87-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30d87-105">Requirements</span></span>  
 <span data-ttu-id="30d87-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30d87-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30d87-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30d87-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30d87-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="30d87-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30d87-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30d87-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d87-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30d87-110">See also</span></span>

- [<span data-ttu-id="30d87-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="30d87-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
