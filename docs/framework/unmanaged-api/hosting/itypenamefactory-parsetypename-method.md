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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbe5f634a5d0580c7e58b03f318da98a0112fa6b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208091"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="53485-102">ITypeNameFactory::ParseTypeName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53485-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="53485-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="53485-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53485-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53485-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="53485-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53485-105">Requirements</span></span>  
 <span data-ttu-id="53485-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53485-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53485-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53485-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53485-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="53485-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53485-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53485-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53485-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53485-110">See also</span></span>

- [<span data-ttu-id="53485-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53485-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
