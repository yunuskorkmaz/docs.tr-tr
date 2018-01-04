---
title: "IMetaDataDispenserEx::FindAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f125008e4ae5b7f2abbe6d467b486b962700d42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="ebf47-102">IMetaDataDispenserEx::FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebf47-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="ebf47-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ebf47-103">This method is not implemented.</span></span> <span data-ttu-id="ebf47-104">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="ebf47-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf47-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebf47-105">Syntax</span></span>  
  
```  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebf47-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebf47-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="ebf47-107">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ebf47-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="ebf47-108">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ebf47-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="ebf47-109">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ebf47-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="ebf47-110">[in] Bulunacak derleme.</span><span class="sxs-lookup"><span data-stu-id="ebf47-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="ebf47-111">[out] Derleme basit adı.</span><span class="sxs-lookup"><span data-stu-id="ebf47-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ebf47-112">[in] Bayt olarak boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="ebf47-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="ebf47-113">[out] Gerçekte döndürülen karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="ebf47-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf47-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebf47-114">Requirements</span></span>  
 <span data-ttu-id="ebf47-115">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf47-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf47-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ebf47-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebf47-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ebf47-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebf47-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf47-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf47-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebf47-119">See Also</span></span>  
 [<span data-ttu-id="ebf47-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebf47-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="ebf47-121">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebf47-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
