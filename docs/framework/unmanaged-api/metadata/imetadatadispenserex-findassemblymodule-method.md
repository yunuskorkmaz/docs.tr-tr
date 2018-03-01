---
title: "IMetaDataDispenserEx::FindAssemblyModule Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 482bc9b9a89d876e7ac09fcb4edcd190adc168f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="fa77f-102">IMetaDataDispenserEx::FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa77f-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="fa77f-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="fa77f-103">This method is not implemented.</span></span> <span data-ttu-id="fa77f-104">Adlı E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa77f-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa77f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa77f-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fa77f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa77f-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="fa77f-107">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="fa77f-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="fa77f-108">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="fa77f-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="fa77f-109">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="fa77f-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="fa77f-110">[in] Modül adı.</span><span class="sxs-lookup"><span data-stu-id="fa77f-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="fa77f-111">[in] Bulunacak derleme.</span><span class="sxs-lookup"><span data-stu-id="fa77f-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="fa77f-112">[out] Derleme basit adı.</span><span class="sxs-lookup"><span data-stu-id="fa77f-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fa77f-113">[in] Bayt olarak boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="fa77f-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="fa77f-114">[out] Gerçekte döndürülen karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="fa77f-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa77f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa77f-115">Requirements</span></span>  
 <span data-ttu-id="fa77f-116">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa77f-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa77f-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa77f-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa77f-118">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fa77f-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa77f-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa77f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa77f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa77f-120">See Also</span></span>  
 [<span data-ttu-id="fa77f-121">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa77f-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="fa77f-122">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa77f-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
