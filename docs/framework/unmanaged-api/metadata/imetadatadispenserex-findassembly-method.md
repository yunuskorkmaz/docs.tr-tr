---
title: IMetaDataDispenserEx::FindAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b35abe6a11b96a88bdd610a4018469bf747fe90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550714"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="79f97-102">IMetaDataDispenserEx::FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79f97-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="79f97-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="79f97-103">This method is not implemented.</span></span> <span data-ttu-id="79f97-104">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="79f97-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f97-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79f97-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="79f97-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79f97-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="79f97-107">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="79f97-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="79f97-108">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="79f97-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="79f97-109">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="79f97-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="79f97-110">[in] Bulunacak derleme.</span><span class="sxs-lookup"><span data-stu-id="79f97-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="79f97-111">[out] Derlemenin basit adını.</span><span class="sxs-lookup"><span data-stu-id="79f97-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="79f97-112">[in] Bayt cinsinden boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="79f97-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="79f97-113">[out] Gerçekte döndürülen karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="79f97-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79f97-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79f97-114">Requirements</span></span>  
 <span data-ttu-id="79f97-115">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79f97-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79f97-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="79f97-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79f97-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="79f97-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79f97-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79f97-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f97-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79f97-119">See also</span></span>
- [<span data-ttu-id="79f97-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79f97-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="79f97-121">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79f97-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
