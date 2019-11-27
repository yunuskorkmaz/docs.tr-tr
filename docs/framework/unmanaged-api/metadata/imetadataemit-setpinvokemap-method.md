---
title: IMetaDataEmit::SetPinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 4e2a78e2d049e952aa1be0b3a8fd640eb18d0320
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440573"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="5c9cc-102">IMetaDataEmit::SetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c9cc-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="5c9cc-103">Bir yöntemin PInvoke imzasının, [ımetadatayay::D Efinepınvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)'e yönelik önceki bir çağrı tarafından tanımlanan özellikleri ayarlar veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5c9cc-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c9cc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c9cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c9cc-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5c9cc-106">'ndaki Eşleme bilgilerinin geçerli olduğu `mdToken`.</span><span class="sxs-lookup"><span data-stu-id="5c9cc-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="5c9cc-107">'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5c9cc-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="5c9cc-108">Bu, `CorPinvokeMap` değerlerinin bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="5c9cc-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="5c9cc-109">'ndaki Yerel DLL 'de hedef dışarı aktarmanın adı.</span><span class="sxs-lookup"><span data-stu-id="5c9cc-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="5c9cc-110">'ndaki Hedef yönetilmeyen DLL için `mdModuleRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="5c9cc-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9cc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c9cc-111">Requirements</span></span>  
 <span data-ttu-id="5c9cc-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c9cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9cc-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5c9cc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c9cc-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5c9cc-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c9cc-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9cc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c9cc-116">See also</span></span>

- [<span data-ttu-id="5c9cc-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c9cc-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5c9cc-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c9cc-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
