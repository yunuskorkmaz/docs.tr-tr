---
title: "IMetaDataDispenserEx::FindAssemblyModule Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssemblyModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3911eeb5f6ff8122c71f0c1df973c4636ad8b665
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="bb9f3-102">IMetaDataDispenserEx::FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb9f3-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="bb9f3-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-103">This method is not implemented.</span></span> <span data-ttu-id="bb9f3-104">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb9f3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb9f3-105">Syntax</span></span>  
  
```  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb9f3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb9f3-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="bb9f3-107">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="bb9f3-108">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="bb9f3-109">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="bb9f3-110">[in] Modül adı.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="bb9f3-111">[in] Bulunacak derleme.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="bb9f3-112">[out] Derleme basit adı.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bb9f3-113">[in] Bayt olarak boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="bb9f3-114">[out] Gerçekte döndürülen karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb9f3-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb9f3-115">Requirements</span></span>  
 <span data-ttu-id="bb9f3-116">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb9f3-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb9f3-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb9f3-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb9f3-118">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bb9f3-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb9f3-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb9f3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9f3-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb9f3-120">See Also</span></span>  
 [<span data-ttu-id="bb9f3-121">Imetadatadispenserex arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb9f3-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="bb9f3-122">Imetadatadispenser arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb9f3-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
