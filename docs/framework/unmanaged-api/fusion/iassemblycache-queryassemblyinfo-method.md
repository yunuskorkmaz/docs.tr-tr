---
title: IAssemblyCache::QueryAssemblyInfo Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0bdd1a22a771a8d0c3cbab511e14eb3456df5032
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497788"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="d8a2d-102">IAssemblyCache::QueryAssemblyInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8a2d-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="d8a2d-103">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="d8a2d-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a2d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8a2d-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8a2d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8a2d-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d8a2d-106">[in] Fusion.idl içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d8a2d-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="d8a2d-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d8a2d-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="d8a2d-108">QUERYASMINFO_FLAG_VALIDATE (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="d8a2d-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="d8a2d-109">QUERYASMINFO_FLAG_GETSIZE (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="d8a2d-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d8a2d-110">[in] Veriler alınır derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="d8a2d-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="d8a2d-111">[out içinde] Bir [assembly_ınfo](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) içeren derleme hakkında daha fazla veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="d8a2d-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8a2d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8a2d-112">Requirements</span></span>  
 <span data-ttu-id="d8a2d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8a2d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8a2d-114">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d8a2d-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d8a2d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8a2d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a2d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a2d-116">See also</span></span>
- [<span data-ttu-id="d8a2d-117">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8a2d-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
