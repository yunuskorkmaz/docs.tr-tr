---
description: ': Itypeename:: GetTypeArguments yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b88ffcfb856905bf891ebeafa1e6dbeda2563aaf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753671"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="95140-103">ITypeName::GetTypeArguments Metodu</span><span class="sxs-lookup"><span data-stu-id="95140-103">ITypeName::GetTypeArguments Method</span></span>

<span data-ttu-id="95140-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="95140-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95140-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="95140-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="95140-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95140-106">Requirements</span></span>  

 <span data-ttu-id="95140-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95140-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95140-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="95140-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95140-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="95140-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95140-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95140-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95140-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95140-111">See also</span></span>

- [<span data-ttu-id="95140-112">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="95140-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
