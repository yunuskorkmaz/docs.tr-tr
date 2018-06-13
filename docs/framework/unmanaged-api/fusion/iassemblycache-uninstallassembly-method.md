---
title: IAssemblyCache::UninstallAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6be40ecbb801348ad73fb929741b5a8e8407a7ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428438"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="a0b9e-102">IAssemblyCache::UninstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0b9e-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="a0b9e-103">Belirtilen derleme Genel Derleme Önbelleği'nden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a0b9e-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0b9e-104">Syntax</span></span>  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0b9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0b9e-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="a0b9e-106">[in] Fusion.idl içinde tanımlı bayrak.</span><span class="sxs-lookup"><span data-stu-id="a0b9e-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="a0b9e-107">[in] Kaldırmak için derleme adı.</span><span class="sxs-lookup"><span data-stu-id="a0b9e-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="a0b9e-108">[in] A [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) derleme için yükleme verilerini içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="a0b9e-108">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="a0b9e-109">[out, isteğe bağlı] Fusion.idl içinde tanımlanan değerlendirme değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="a0b9e-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="a0b9e-110">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a0b9e-110">Possible values include the following:</span></span>  
  
-   <span data-ttu-id="a0b9e-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="a0b9e-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
-   <span data-ttu-id="a0b9e-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="a0b9e-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
-   <span data-ttu-id="a0b9e-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="a0b9e-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
-   <span data-ttu-id="a0b9e-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="a0b9e-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
-   <span data-ttu-id="a0b9e-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="a0b9e-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
-   <span data-ttu-id="a0b9e-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="a0b9e-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0b9e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0b9e-117">Requirements</span></span>  
 <span data-ttu-id="a0b9e-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0b9e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0b9e-119">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a0b9e-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a0b9e-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0b9e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b9e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0b9e-121">See Also</span></span>  
 [<span data-ttu-id="a0b9e-122">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0b9e-122">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
