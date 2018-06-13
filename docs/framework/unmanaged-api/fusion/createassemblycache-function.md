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
ms.openlocfilehash: ba4259ad9cdf4f56fd4c00b5c7e9ebfa8b7fe1ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429585"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="696e0-102">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="696e0-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="696e0-103">Bir işaretçi yeni bir alır [Iassemblycache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) Genel Derleme Önbelleği temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="696e0-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="696e0-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="696e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="696e0-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="696e0-106">[out] Döndürülen `IAssemblyCache` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="696e0-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="696e0-107">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="696e0-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="696e0-108">`dwReserved` 0 (sıfır) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="696e0-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696e0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="696e0-109">Requirements</span></span>  
 <span data-ttu-id="696e0-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="696e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696e0-111">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="696e0-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="696e0-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="696e0-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="696e0-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="696e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696e0-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="696e0-114">See Also</span></span>  
 [<span data-ttu-id="696e0-115">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="696e0-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="696e0-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="696e0-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="696e0-117">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="696e0-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
