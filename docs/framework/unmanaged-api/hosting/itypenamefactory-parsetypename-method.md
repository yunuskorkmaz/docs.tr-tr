---
title: ITypeNameFactory::ParseTypeName Yöntemi
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: 2b4d22fac7125ad113aaef5b093396a065f682c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728725"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="af2dd-102">ITypeNameFactory::ParseTypeName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af2dd-102">ITypeNameFactory::ParseTypeName Method</span></span>

<span data-ttu-id="af2dd-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="af2dd-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2dd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="af2dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="af2dd-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af2dd-105">Requirements</span></span>  

 <span data-ttu-id="af2dd-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af2dd-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af2dd-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af2dd-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af2dd-108">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="af2dd-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af2dd-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af2dd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2dd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af2dd-110">See also</span></span>

- [<span data-ttu-id="af2dd-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="af2dd-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
