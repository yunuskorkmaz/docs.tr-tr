---
title: ITypeName::GetTypeArguments Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetTypeArguments
api_location: mscoree.dll
api_type: COM
f1_keywords: GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b0110d67b5f72a060fae3800ca6292465896e3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="48216-102">ITypeName::GetTypeArguments Metodu</span><span class="sxs-lookup"><span data-stu-id="48216-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="48216-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="48216-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48216-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48216-104">Syntax</span></span>  
  
```  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="48216-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48216-105">Requirements</span></span>  
 <span data-ttu-id="48216-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48216-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48216-107">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48216-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48216-108">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="48216-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48216-109">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48216-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48216-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48216-110">See Also</span></span>  
 [<span data-ttu-id="48216-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="48216-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
