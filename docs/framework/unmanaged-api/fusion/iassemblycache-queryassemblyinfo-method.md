---
description: 'Şu konuda daha fazla bilgi edinin: IAssemblyCache:: QueryAssemblyInfo yöntemi'
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
ms.openlocfilehash: b3aa0064e24b22cf0af8b4e8d23a8b92d2f1ac34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760920"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="01422-103">IAssemblyCache::QueryAssemblyInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01422-103">IAssemblyCache::QueryAssemblyInfo Method</span></span>

<span data-ttu-id="01422-104">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="01422-104">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01422-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01422-105">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01422-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01422-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="01422-107">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="01422-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="01422-108">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="01422-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="01422-109">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="01422-109">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="01422-110">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="01422-110">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="01422-111">'ndaki Verilerin alınacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="01422-111">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="01422-112">[in, out] Derlemeyle ilgili verileri içeren [ASSEMBLY_INFO](assembly-info-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="01422-112">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01422-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01422-113">Requirements</span></span>  

 <span data-ttu-id="01422-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01422-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01422-115">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="01422-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="01422-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01422-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01422-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01422-117">See also</span></span>

- [<span data-ttu-id="01422-118">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01422-118">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
