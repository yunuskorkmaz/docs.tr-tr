---
description: ': IAssemblyCache:: InstallAssembly yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0bb9fe31467506a03f5e81e5a29a6b1fb65f5804
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760952"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="e9450-103">IAssemblyCache::InstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9450-103">IAssemblyCache::InstallAssembly Method</span></span>

<span data-ttu-id="e9450-104">Belirtilen derlemeyi genel derleme önbelleğine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e9450-104">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9450-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9450-105">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9450-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9450-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="e9450-107">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e9450-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="e9450-108">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e9450-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="e9450-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="e9450-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="e9450-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="e9450-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="e9450-111">'ndaki Yüklenecek derleme için bildirimin yolu.</span><span class="sxs-lookup"><span data-stu-id="e9450-111">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="e9450-112">'ndaki Yükleme için veri içeren bir [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="e9450-112">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9450-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9450-113">Requirements</span></span>  

 <span data-ttu-id="e9450-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9450-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9450-115">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e9450-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e9450-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9450-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9450-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9450-117">See also</span></span>

- [<span data-ttu-id="e9450-118">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9450-118">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
