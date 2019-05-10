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
ms.openlocfilehash: 515af49efc20254ad6bdc5c9fa0029cfe34f2c07
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623753"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="9342a-102">IAssemblyCache::QueryAssemblyInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9342a-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="9342a-103">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="9342a-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9342a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9342a-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9342a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9342a-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="9342a-106">[in] Fusion.idl içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="9342a-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="9342a-107">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="9342a-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="9342a-108">QUERYASMINFO_FLAG_VALIDATE (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="9342a-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="9342a-109">QUERYASMINFO_FLAG_GETSIZE (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="9342a-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="9342a-110">[in] Veriler alınır derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="9342a-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="9342a-111">[out içinde] Bir [assembly_ınfo](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) içeren derleme hakkında daha fazla veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="9342a-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9342a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9342a-112">Requirements</span></span>  
 <span data-ttu-id="9342a-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9342a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9342a-114">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9342a-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9342a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9342a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9342a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9342a-116">See also</span></span>

- [<span data-ttu-id="9342a-117">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9342a-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
