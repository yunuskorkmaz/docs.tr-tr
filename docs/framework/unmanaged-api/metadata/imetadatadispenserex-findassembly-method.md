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
ms.openlocfilehash: 2d974b7368dd01062d2d310d076dce05e102eb81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442281"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="224f2-102">IMetaDataDispenserEx::FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="224f2-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="224f2-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="224f2-103">This method is not implemented.</span></span> <span data-ttu-id="224f2-104">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="224f2-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="224f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="224f2-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="224f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="224f2-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="224f2-107">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="224f2-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="224f2-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="224f2-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="224f2-109">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="224f2-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="224f2-110">'ndaki Bulunan bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="224f2-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="224f2-111">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="224f2-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="224f2-112">'ndaki `szName`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="224f2-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="224f2-113">dışı `szName`' de aslında döndürülen karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="224f2-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="224f2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="224f2-114">Requirements</span></span>  
 <span data-ttu-id="224f2-115">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="224f2-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="224f2-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="224f2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="224f2-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="224f2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="224f2-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="224f2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="224f2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="224f2-119">See also</span></span>

- [<span data-ttu-id="224f2-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="224f2-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="224f2-121">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="224f2-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
