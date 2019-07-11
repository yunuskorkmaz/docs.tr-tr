---
title: ITypeName::GetAssemblyName Metodu
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81b93675870d73902cf986a64d34d7c270e02203
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780551"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="e16ef-102">ITypeName::GetAssemblyName Metodu</span><span class="sxs-lookup"><span data-stu-id="e16ef-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="e16ef-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="e16ef-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e16ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e16ef-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e16ef-105">Requirements</span></span>  
 <span data-ttu-id="e16ef-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e16ef-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e16ef-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e16ef-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e16ef-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e16ef-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e16ef-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e16ef-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16ef-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e16ef-110">See also</span></span>

- [<span data-ttu-id="e16ef-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e16ef-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
