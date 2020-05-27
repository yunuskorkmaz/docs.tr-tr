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
ms.openlocfilehash: 0d34c7a2992a2779b96ec87f1a0175d8fcbce34a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007799"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="e017e-102">IMetaDataEmit::SetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e017e-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="e017e-103">Bir yöntemin PInvoke imzasının, [ımetadatayay::D Efinepınvokemap](imetadataemit-definepinvokemap-method.md)'e yönelik önceki bir çağrı tarafından tanımlanan özellikleri ayarlar veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e017e-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e017e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e017e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e017e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e017e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e017e-106">'ndaki `mdToken`Eşleme bilgileri geçerli.</span><span class="sxs-lookup"><span data-stu-id="e017e-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="e017e-107">'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e017e-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="e017e-108">Bu bir değer bit değeridir `CorPinvokeMap` .</span><span class="sxs-lookup"><span data-stu-id="e017e-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="e017e-109">'ndaki Yerel DLL 'de hedef dışarı aktarmanın adı.</span><span class="sxs-lookup"><span data-stu-id="e017e-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="e017e-110">'ndaki `mdModuleRef`Hedef YÖNETILMEYEN dll için belirteç.</span><span class="sxs-lookup"><span data-stu-id="e017e-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e017e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e017e-111">Requirements</span></span>  
 <span data-ttu-id="e017e-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e017e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e017e-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e017e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e017e-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e017e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e017e-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e017e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e017e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e017e-116">See also</span></span>

- [<span data-ttu-id="e017e-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e017e-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e017e-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e017e-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
