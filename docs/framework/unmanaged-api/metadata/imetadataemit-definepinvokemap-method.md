---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D Efinepınvokemap yöntemi'
title: IMetaDataEmit::DefinePinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: 7b0477ca603241e773a67f335da579daa2ed3d30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784073"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="a1a76-103">IMetaDataEmit::DefinePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1a76-103">IMetaDataEmit::DefinePinvokeMap Method</span></span>

<span data-ttu-id="a1a76-104">Belirtilen belirteç tarafından başvurulan metodun PInvoke imzasının özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1a76-104">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a76-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1a76-105">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1a76-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1a76-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="a1a76-107">'ndaki Hedef yöntemi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="a1a76-107">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="a1a76-108">'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="a1a76-108">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="a1a76-109">'ndaki Yönetilmeyen DLL içindeki hedef dışarı aktarma yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="a1a76-109">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="a1a76-110">'ndaki Hedef yerel DLL için belirteç.</span><span class="sxs-lookup"><span data-stu-id="a1a76-110">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1a76-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1a76-111">Requirements</span></span>  

 <span data-ttu-id="a1a76-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1a76-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1a76-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a1a76-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1a76-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a1a76-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1a76-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1a76-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a76-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1a76-116">See also</span></span>

- [<span data-ttu-id="a1a76-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1a76-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a1a76-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1a76-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
