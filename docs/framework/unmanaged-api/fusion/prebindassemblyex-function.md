---
description: 'Daha fazla bilgi edinin: PreBindAssemblyEx Işlevi'
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
ms.openlocfilehash: e94bd7c335555e8109df60a00cadc76f7e13434b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800012"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="c5d18-103">PreBindAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="c5d18-103">PreBindAssemblyEx Function</span></span>

<span data-ttu-id="c5d18-104">Bir derlemenin ilke sonrası görünen adını alır.</span><span class="sxs-lookup"><span data-stu-id="c5d18-104">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="c5d18-105">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="c5d18-105">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d18-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5d18-106">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5d18-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5d18-107">Parameters</span></span>  

 `pAppCtx`  
 <span data-ttu-id="c5d18-108">'ndaki Uygulama bağlamını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5d18-108">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="c5d18-109">'ndaki Derleme adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5d18-109">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="c5d18-110">'ndaki Üst derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5d18-110">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="c5d18-111">Bu parametre yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="c5d18-111">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="c5d18-112">'ndaki Çalışma zamanı sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5d18-112">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="c5d18-113">dışı İlke sonrası görünen adını içerir.</span><span class="sxs-lookup"><span data-stu-id="c5d18-113">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c5d18-114">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5d18-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="c5d18-115">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5d18-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5d18-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5d18-116">Remarks</span></span>  

 <span data-ttu-id="c5d18-117">`ppNamePostPolicy`Output parametresi yalnızca Işlev HRESULT FUSION_E_REF_DEF_MISMATCH döndürürse ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5d18-117">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="c5d18-118">Aksi halde, null olur.</span><span class="sxs-lookup"><span data-stu-id="c5d18-118">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d18-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5d18-119">Requirements</span></span>  

 <span data-ttu-id="c5d18-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d18-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d18-121">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c5d18-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c5d18-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c5d18-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5d18-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d18-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d18-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5d18-124">See also</span></span>

- [<span data-ttu-id="c5d18-125">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c5d18-125">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
