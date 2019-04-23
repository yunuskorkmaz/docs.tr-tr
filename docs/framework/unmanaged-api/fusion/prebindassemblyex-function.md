---
title: PreBindAssemblyEx İşlevi
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8251d21fe535f85cc6abd0a7bc6c96ab320007f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090244"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="298d9-102">PreBindAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="298d9-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="298d9-103">Derleme sonrası ilke görünen adını alır.</span><span class="sxs-lookup"><span data-stu-id="298d9-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="298d9-104">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="298d9-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298d9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="298d9-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="298d9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="298d9-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="298d9-107">[in] Uygulama bağlamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="298d9-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="298d9-108">[in] Derleme adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="298d9-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="298d9-109">[in] Üst derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="298d9-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="298d9-110">Bu parametre yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="298d9-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="298d9-111">[in] Çalışma zamanı sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="298d9-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="298d9-112">[out] İlke sonrası görünen adını içerir.</span><span class="sxs-lookup"><span data-stu-id="298d9-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="298d9-113">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="298d9-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="298d9-114">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="298d9-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="298d9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="298d9-115">Remarks</span></span>  
 <span data-ttu-id="298d9-116">`ppNamePostPolicy` Çıkış parametresi yalnızca işlev HRESULT FUSION_E_REF_DEF_MISMATCH döndürürse ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="298d9-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="298d9-117">Aksi takdirde null olur.</span><span class="sxs-lookup"><span data-stu-id="298d9-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="298d9-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="298d9-118">Requirements</span></span>  
 <span data-ttu-id="298d9-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="298d9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="298d9-120">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="298d9-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="298d9-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="298d9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="298d9-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="298d9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298d9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="298d9-123">See also</span></span>

- [<span data-ttu-id="298d9-124">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="298d9-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
