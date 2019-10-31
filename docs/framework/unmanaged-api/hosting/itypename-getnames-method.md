---
title: ITypeName::GetNames Metodu
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
ms.openlocfilehash: 66934db3f1507262ffb2e9eec232f21574c29348
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095752"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="e264e-102">ITypeName::GetNames Metodu</span><span class="sxs-lookup"><span data-stu-id="e264e-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="e264e-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="e264e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e264e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e264e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e264e-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e264e-105">Requirements</span></span>  
 <span data-ttu-id="e264e-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e264e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e264e-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e264e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e264e-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e264e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e264e-109">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e264e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e264e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e264e-110">See also</span></span>

- [<span data-ttu-id="e264e-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e264e-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
