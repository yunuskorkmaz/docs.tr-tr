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
ms.openlocfilehash: ec08c786992996ec6f44038ff3c1596cada88484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127077"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="b46f1-102">IAssemblyCache::InstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b46f1-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="b46f1-103">Belirtilen derlemeyi genel derleme önbelleğine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b46f1-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b46f1-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b46f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b46f1-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b46f1-106">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="b46f1-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="b46f1-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="b46f1-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="b46f1-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="b46f1-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="b46f1-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="b46f1-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="b46f1-110">'ndaki Yüklenecek derleme için bildirimin yolu.</span><span class="sxs-lookup"><span data-stu-id="b46f1-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="b46f1-111">'ndaki Yükleme için veri içeren bir [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="b46f1-111">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b46f1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b46f1-112">Requirements</span></span>  
 <span data-ttu-id="b46f1-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b46f1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b46f1-114">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b46f1-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b46f1-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b46f1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46f1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b46f1-116">See also</span></span>

- [<span data-ttu-id="b46f1-117">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b46f1-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
