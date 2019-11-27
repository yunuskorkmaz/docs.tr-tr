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
ms.openlocfilehash: e73c95d8c720ed3263d6a66c48bdb5b5582eb686
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442185"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="be207-102">IMetaDataDispenserEx::FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be207-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="be207-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="be207-103">This method is not implemented.</span></span> <span data-ttu-id="be207-104">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="be207-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be207-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be207-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="be207-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be207-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="be207-107">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="be207-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="be207-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="be207-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="be207-109">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="be207-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="be207-110">'ndaki Modülün adı.</span><span class="sxs-lookup"><span data-stu-id="be207-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="be207-111">'ndaki Bulunan bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="be207-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="be207-112">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="be207-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="be207-113">'ndaki `szName`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="be207-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="be207-114">dışı `szName`' de aslında döndürülen karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="be207-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be207-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be207-115">Requirements</span></span>  
 <span data-ttu-id="be207-116">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be207-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be207-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be207-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be207-118">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="be207-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be207-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be207-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be207-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be207-120">See also</span></span>

- [<span data-ttu-id="be207-121">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be207-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="be207-122">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be207-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
