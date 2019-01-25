---
title: ITypeName::GetTypeArguments Metodu
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c6d89372bd9c1e10412832e91dc7660dfe6bbfd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732459"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="d5e53-102">ITypeName::GetTypeArguments Metodu</span><span class="sxs-lookup"><span data-stu-id="d5e53-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="d5e53-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="d5e53-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5e53-104">Syntax</span></span>  
  
```  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d5e53-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5e53-105">Requirements</span></span>  
 <span data-ttu-id="d5e53-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e53-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e53-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5e53-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5e53-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d5e53-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5e53-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e53-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e53-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5e53-110">See also</span></span>
- [<span data-ttu-id="d5e53-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5e53-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
