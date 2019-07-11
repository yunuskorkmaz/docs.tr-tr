---
title: CreateAssemblyCache İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffeb04ddcec290f899556bf0d8078acfb06707ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778598"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="e7d00-102">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="e7d00-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="e7d00-103">Yeni bir işaretçi alır [Iassemblycache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) genel derleme önbelleğini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="e7d00-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d00-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7d00-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7d00-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7d00-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="e7d00-106">[out] Döndürülen `IAssemblyCache` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e7d00-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="e7d00-107">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e7d00-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e7d00-108">`dwReserved` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7d00-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d00-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7d00-109">Requirements</span></span>  
 <span data-ttu-id="e7d00-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d00-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d00-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e7d00-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e7d00-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e7d00-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7d00-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d00-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d00-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7d00-114">See also</span></span>

- [<span data-ttu-id="e7d00-115">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7d00-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="e7d00-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e7d00-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="e7d00-117">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="e7d00-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
