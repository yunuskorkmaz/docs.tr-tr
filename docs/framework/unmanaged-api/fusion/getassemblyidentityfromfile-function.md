---
title: GetAssemblyIdentityFromFile İşlevi
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581c675cfb69503e6366471a469ffed1a2d13b1a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745234"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="52899-102">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="52899-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="52899-103">Bir işaretçi alır bir `IUnknown` belirtilen nesnesiyle `IID` belirtilen dosya yolunda derlemedeki.</span><span class="sxs-lookup"><span data-stu-id="52899-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52899-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52899-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="52899-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52899-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="52899-106">[in] İstenen derleme için geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="52899-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="52899-107">[in] `IID` Döndürülecek arabirimi.</span><span class="sxs-lookup"><span data-stu-id="52899-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="52899-108">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52899-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52899-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52899-109">Requirements</span></span>  
 <span data-ttu-id="52899-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52899-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52899-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="52899-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="52899-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52899-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52899-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52899-113">See also</span></span>

- [<span data-ttu-id="52899-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="52899-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="52899-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="52899-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
