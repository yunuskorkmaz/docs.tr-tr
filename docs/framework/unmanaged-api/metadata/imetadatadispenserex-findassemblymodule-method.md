---
title: IMetaDataDispenserEx::FindAssemblyModule Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ae455aeba353cfa66a1253b580e15b280caec8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584106"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="a26ef-102">IMetaDataDispenserEx::FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a26ef-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="a26ef-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a26ef-103">This method is not implemented.</span></span> <span data-ttu-id="a26ef-104">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="a26ef-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26ef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a26ef-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a26ef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a26ef-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="a26ef-107">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a26ef-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="a26ef-108">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a26ef-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="a26ef-109">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a26ef-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="a26ef-110">[in] Modülün adı.</span><span class="sxs-lookup"><span data-stu-id="a26ef-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="a26ef-111">[in] Bulunacak derleme.</span><span class="sxs-lookup"><span data-stu-id="a26ef-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="a26ef-112">[out] Derlemenin basit adını.</span><span class="sxs-lookup"><span data-stu-id="a26ef-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a26ef-113">[in] Bayt cinsinden boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="a26ef-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="a26ef-114">[out] Gerçekte döndürülen karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="a26ef-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a26ef-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a26ef-115">Requirements</span></span>  
 <span data-ttu-id="a26ef-116">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a26ef-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26ef-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a26ef-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a26ef-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="a26ef-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a26ef-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a26ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26ef-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a26ef-120">See also</span></span>
- [<span data-ttu-id="a26ef-121">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a26ef-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="a26ef-122">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a26ef-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
