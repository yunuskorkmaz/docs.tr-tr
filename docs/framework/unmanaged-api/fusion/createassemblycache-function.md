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
ms.openlocfilehash: bf78ded62f11b336d9f5fe0f3a205275ae37189b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157410"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="3f3b7-102">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f3b7-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="3f3b7-103">Yeni bir işaretçi alır [Iassemblycache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) genel derleme önbelleğini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="3f3b7-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f3b7-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f3b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f3b7-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="3f3b7-106">[out] Döndürülen `IAssemblyCache` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f3b7-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="3f3b7-107">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="3f3b7-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="3f3b7-108">`dwReserved` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f3b7-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3b7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f3b7-109">Requirements</span></span>  
 <span data-ttu-id="3f3b7-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3b7-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3f3b7-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3f3b7-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3f3b7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f3b7-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3b7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f3b7-114">See also</span></span>

- [<span data-ttu-id="3f3b7-115">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f3b7-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="3f3b7-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3f3b7-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="3f3b7-117">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="3f3b7-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
