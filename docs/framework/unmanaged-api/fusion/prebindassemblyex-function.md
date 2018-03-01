---
title: "PreBindAssemblyEx İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 05977db8e01d00af6e160cb2993867cf83eb24c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="077b4-102">PreBindAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="077b4-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="077b4-103">Derleme sonrası İlkesi görünen adını alır.</span><span class="sxs-lookup"><span data-stu-id="077b4-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="077b4-104">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="077b4-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="077b4-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="077b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="077b4-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="077b4-107">[in] Uygulama bağlamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="077b4-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="077b4-108">[in] Derleme adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="077b4-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="077b4-109">[in] Ana derleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="077b4-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="077b4-110">Bu parametre yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="077b4-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="077b4-111">[in] Çalışma zamanı sürümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="077b4-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="077b4-112">[out] İlke sonrası görünen adı içerir.</span><span class="sxs-lookup"><span data-stu-id="077b4-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="077b4-113">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="077b4-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="077b4-114">`pvReserved`bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="077b4-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="077b4-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="077b4-115">Remarks</span></span>  
 <span data-ttu-id="077b4-116">`ppNamePostPolicy` Çıktı parametresi yalnızca işlevi HRESULT FUSION_E_REF_DEF_MISMATCH döndürürse ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="077b4-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="077b4-117">Aksi takdirde null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="077b4-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="077b4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="077b4-118">Requirements</span></span>  
 <span data-ttu-id="077b4-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="077b4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="077b4-120">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="077b4-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="077b4-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="077b4-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="077b4-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="077b4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077b4-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="077b4-123">See Also</span></span>  
 [<span data-ttu-id="077b4-124">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="077b4-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
