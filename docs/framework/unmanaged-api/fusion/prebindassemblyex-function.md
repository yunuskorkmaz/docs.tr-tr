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
ms.openlocfilehash: ea34c4087014091b92d6227177a2f08209cc2e10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570885"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="ebc03-102">PreBindAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="ebc03-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="ebc03-103">Derleme sonrası ilke görünen adını alır.</span><span class="sxs-lookup"><span data-stu-id="ebc03-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="ebc03-104">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="ebc03-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc03-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebc03-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ebc03-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebc03-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="ebc03-107">[in] Uygulama bağlamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ebc03-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="ebc03-108">[in] Derleme adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ebc03-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="ebc03-109">[in] Üst derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ebc03-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="ebc03-110">Bu parametre yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="ebc03-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="ebc03-111">[in] Çalışma zamanı sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ebc03-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="ebc03-112">[out] İlke sonrası görünen adını içerir.</span><span class="sxs-lookup"><span data-stu-id="ebc03-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ebc03-113">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="ebc03-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ebc03-114">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ebc03-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebc03-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebc03-115">Remarks</span></span>  
 <span data-ttu-id="ebc03-116">`ppNamePostPolicy` Çıkış parametresi yalnızca işlev HRESULT FUSION_E_REF_DEF_MISMATCH döndürürse ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ebc03-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="ebc03-117">Aksi takdirde null olur.</span><span class="sxs-lookup"><span data-stu-id="ebc03-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebc03-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebc03-118">Requirements</span></span>  
 <span data-ttu-id="ebc03-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebc03-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebc03-120">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ebc03-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ebc03-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ebc03-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebc03-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebc03-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc03-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebc03-123">See also</span></span>
- [<span data-ttu-id="ebc03-124">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ebc03-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
