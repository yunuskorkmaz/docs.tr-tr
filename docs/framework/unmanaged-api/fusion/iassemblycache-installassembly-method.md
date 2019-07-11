---
title: IAssemblyCache::InstallAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd420f0f166b0b17e5fbaf08d6bedd6651188b1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778747"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="34711-102">IAssemblyCache::InstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34711-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="34711-103">Belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="34711-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34711-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34711-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34711-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34711-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="34711-106">[in] Fusion.idl içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="34711-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="34711-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="34711-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="34711-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="34711-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="34711-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="34711-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="34711-110">[in] Yüklenecek derlemenin bildirimi yolu.</span><span class="sxs-lookup"><span data-stu-id="34711-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="34711-111">[in] A [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) içeren yüklemesi için veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="34711-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34711-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34711-112">Requirements</span></span>  
 <span data-ttu-id="34711-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34711-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34711-114">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="34711-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="34711-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34711-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34711-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34711-116">See also</span></span>

- [<span data-ttu-id="34711-117">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34711-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
