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
ms.openlocfilehash: e059cdddef7926c1359a83bc562146203724aa60
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842128"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="623c2-102">ITypeName::GetTypeArguments Metodu</span><span class="sxs-lookup"><span data-stu-id="623c2-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="623c2-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="623c2-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="623c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="623c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="623c2-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="623c2-105">Requirements</span></span>  
 <span data-ttu-id="623c2-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="623c2-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="623c2-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="623c2-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="623c2-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="623c2-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="623c2-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="623c2-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="623c2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="623c2-110">See also</span></span>

- [<span data-ttu-id="623c2-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="623c2-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
