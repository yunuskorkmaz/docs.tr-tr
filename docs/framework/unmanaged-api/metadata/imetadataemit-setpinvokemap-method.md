---
description: ': Imetadatayayma:: Setpınvokemap yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e50f06385b599a99454da0a9b971b00806d3140a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771853"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="22bb3-103">IMetaDataEmit::SetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22bb3-103">IMetaDataEmit::SetPinvokeMap Method</span></span>

<span data-ttu-id="22bb3-104">Bir yöntemin PInvoke imzasının, [ımetadatayay::D Efinepınvokemap](imetadataemit-definepinvokemap-method.md)'e yönelik önceki bir çağrı tarafından tanımlanan özellikleri ayarlar veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="22bb3-104">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bb3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22bb3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22bb3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22bb3-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="22bb3-107">'ndaki `mdToken` Eşleme bilgileri geçerli.</span><span class="sxs-lookup"><span data-stu-id="22bb3-107">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="22bb3-108">'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="22bb3-108">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="22bb3-109">Bu bir değer bit değeridir `CorPinvokeMap` .</span><span class="sxs-lookup"><span data-stu-id="22bb3-109">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="22bb3-110">'ndaki Yerel DLL 'de hedef dışarı aktarmanın adı.</span><span class="sxs-lookup"><span data-stu-id="22bb3-110">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="22bb3-111">'ndaki `mdModuleRef` Hedef YÖNETILMEYEN dll için belirteç.</span><span class="sxs-lookup"><span data-stu-id="22bb3-111">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22bb3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22bb3-112">Requirements</span></span>  

 <span data-ttu-id="22bb3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22bb3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22bb3-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="22bb3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22bb3-115">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="22bb3-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22bb3-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22bb3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22bb3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22bb3-117">See also</span></span>

- [<span data-ttu-id="22bb3-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22bb3-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="22bb3-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22bb3-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
