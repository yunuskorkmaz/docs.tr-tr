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
ms.openlocfilehash: 20ea800b86a169eff984b6068db3e9887235a034
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496982"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="1c572-102">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="1c572-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="1c572-103">Bir işaretçi alır bir `IUnknown` belirtilen nesnesiyle `IID` belirtilen dosya yolunda derlemedeki.</span><span class="sxs-lookup"><span data-stu-id="1c572-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c572-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c572-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c572-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c572-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="1c572-106">[in] İstenen derleme için geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="1c572-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="1c572-107">[in] `IID` Döndürülecek arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1c572-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="1c572-108">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1c572-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c572-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c572-109">Requirements</span></span>  
 <span data-ttu-id="1c572-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c572-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c572-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1c572-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1c572-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c572-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c572-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c572-113">See also</span></span>
- [<span data-ttu-id="1c572-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="1c572-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="1c572-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1c572-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
