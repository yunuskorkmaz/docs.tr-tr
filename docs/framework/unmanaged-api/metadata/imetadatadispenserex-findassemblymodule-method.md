---
description: ': Imetadatadağıtıserex:: FindAssemblyModule Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 39ea13a2d8f2436e86db513aaa33f990f43d8132
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753581"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="b17bd-103">IMetaDataDispenserEx::FindAssemblyModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b17bd-103">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>

<span data-ttu-id="b17bd-104">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="b17bd-104">This method is not implemented.</span></span> <span data-ttu-id="b17bd-105">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="b17bd-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b17bd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b17bd-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b17bd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b17bd-107">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="b17bd-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b17bd-108">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="b17bd-109">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b17bd-109">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="b17bd-110">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b17bd-110">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="b17bd-111">'ndaki Modülün adı.</span><span class="sxs-lookup"><span data-stu-id="b17bd-111">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="b17bd-112">'ndaki Bulunan bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="b17bd-112">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="b17bd-113">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="b17bd-113">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b17bd-114">'ndaki Bayt cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="b17bd-114">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="b17bd-115">dışı Aslında ' de döndürülen karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="b17bd-115">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b17bd-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b17bd-116">Requirements</span></span>  

 <span data-ttu-id="b17bd-117">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b17bd-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b17bd-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b17bd-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b17bd-119">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b17bd-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b17bd-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b17bd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17bd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b17bd-121">See also</span></span>

- [<span data-ttu-id="b17bd-122">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b17bd-122">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="b17bd-123">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b17bd-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
