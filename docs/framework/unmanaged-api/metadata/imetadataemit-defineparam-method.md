---
title: IMetaDataEmit::DefineParam Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 5b3f89bb14be0d7128682f8702548545b1e50928
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719534"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="9a1ba-102">IMetaDataEmit::DefineParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a1ba-102">IMetaDataEmit::DefineParam Method</span></span>

<span data-ttu-id="9a1ba-103">Belirtilen belirteç tarafından başvurulan yöntem için belirtilen imzaya sahip bir parametre tanımı oluşturur ve bu parametre tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a1ba-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9a1ba-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a1ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a1ba-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="9a1ba-106">'ndaki Parametresi tanımlanmakta olan metodun belirteci.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="9a1ba-107">'ndaki Parametre sıra numarası.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a1ba-108">'ndaki Parametrenin Unicode olarak adı.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="9a1ba-109">'ndaki Parametre bayrakları.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="9a1ba-110">Bu bir değer bit değeridir `CorParamAttr` .</span><span class="sxs-lookup"><span data-stu-id="9a1ba-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="9a1ba-111">[in] `ELEMENT_TYPE_` *\** sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9a1ba-112">'ndaki Parametrenin sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="9a1ba-113">'ndaki ' Nin Unicode karakterdeki boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="9a1ba-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="9a1ba-114">dışı `mdParamDef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a1ba-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a1ba-115">Remarks</span></span>  

 <span data-ttu-id="9a1ba-116">İçindeki sıra değerleri, `ulParamSeq` Parametreler için 1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="9a1ba-117">Dönüş değerinin sıra numarası 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a1ba-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a1ba-118">Requirements</span></span>  

 <span data-ttu-id="9a1ba-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a1ba-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a1ba-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9a1ba-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a1ba-121">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9a1ba-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a1ba-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a1ba-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1ba-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a1ba-123">See also</span></span>

- [<span data-ttu-id="9a1ba-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1ba-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9a1ba-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1ba-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
