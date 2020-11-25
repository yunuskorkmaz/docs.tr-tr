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
ms.openlocfilehash: c11a4498610c3e82590a0ff9be1247173e70be76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713398"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="53658-102">IMetaDataDispenserEx::FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53658-102">IMetaDataDispenserEx::FindAssembly Method</span></span>

<span data-ttu-id="53658-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="53658-103">This method is not implemented.</span></span> <span data-ttu-id="53658-104">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="53658-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53658-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="53658-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="53658-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53658-106">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="53658-107">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="53658-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="53658-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="53658-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="53658-109">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="53658-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="53658-110">'ndaki Bulunan bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="53658-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="53658-111">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="53658-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="53658-112">'ndaki Bayt cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="53658-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="53658-113">dışı Aslında ' de döndürülen karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="53658-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53658-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53658-114">Requirements</span></span>  

 <span data-ttu-id="53658-115">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53658-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53658-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="53658-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53658-117">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="53658-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53658-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53658-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53658-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53658-119">See also</span></span>

- [<span data-ttu-id="53658-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53658-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="53658-121">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53658-121">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
