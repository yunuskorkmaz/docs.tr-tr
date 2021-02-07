---
description: ': Imetadatadağıtıserex:: FindAssembly Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6bed016e9235281b42f5a3231ef2aff284b6cc3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753607"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="dd54f-103">IMetaDataDispenserEx::FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd54f-103">IMetaDataDispenserEx::FindAssembly Method</span></span>

<span data-ttu-id="dd54f-104">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="dd54f-104">This method is not implemented.</span></span> <span data-ttu-id="dd54f-105">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd54f-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd54f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd54f-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dd54f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd54f-107">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="dd54f-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="dd54f-108">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="dd54f-109">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="dd54f-109">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="dd54f-110">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="dd54f-110">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="dd54f-111">'ndaki Bulunan bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="dd54f-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="dd54f-112">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="dd54f-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="dd54f-113">'ndaki Bayt cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="dd54f-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="dd54f-114">dışı Aslında ' de döndürülen karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="dd54f-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd54f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd54f-115">Requirements</span></span>  

 <span data-ttu-id="dd54f-116">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd54f-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd54f-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dd54f-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd54f-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dd54f-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd54f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd54f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd54f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd54f-120">See also</span></span>

- [<span data-ttu-id="dd54f-121">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd54f-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="dd54f-122">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd54f-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
