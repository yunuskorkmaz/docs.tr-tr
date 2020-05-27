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
ms.openlocfilehash: 1d00d150f98e44fb5c6484378266b7d9b238f4a9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008592"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="02459-102">ITypeNameFactory::ParseTypeName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02459-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="02459-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="02459-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02459-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02459-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="02459-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02459-105">Requirements</span></span>  
 <span data-ttu-id="02459-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02459-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02459-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="02459-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02459-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="02459-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02459-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02459-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02459-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02459-110">See also</span></span>

- [<span data-ttu-id="02459-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="02459-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
