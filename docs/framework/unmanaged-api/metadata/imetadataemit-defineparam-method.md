---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineParam yöntemi'
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
ms.openlocfilehash: 300de3183b329773a8e6813d6b92c6d049d63195
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784099"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="27994-103">IMetaDataEmit::DefineParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27994-103">IMetaDataEmit::DefineParam Method</span></span>

<span data-ttu-id="27994-104">Belirtilen belirteç tarafından başvurulan yöntem için belirtilen imzaya sahip bir parametre tanımı oluşturur ve bu parametre tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="27994-104">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27994-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27994-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="27994-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27994-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="27994-107">'ndaki Parametresi tanımlanmakta olan metodun belirteci.</span><span class="sxs-lookup"><span data-stu-id="27994-107">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="27994-108">'ndaki Parametre sıra numarası.</span><span class="sxs-lookup"><span data-stu-id="27994-108">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="27994-109">'ndaki Parametrenin Unicode olarak adı.</span><span class="sxs-lookup"><span data-stu-id="27994-109">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="27994-110">'ndaki Parametre bayrakları.</span><span class="sxs-lookup"><span data-stu-id="27994-110">[in] Flags for the parameter.</span></span> <span data-ttu-id="27994-111">Bu bir değer bit değeridir `CorParamAttr` .</span><span class="sxs-lookup"><span data-stu-id="27994-111">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="27994-112">[in] `ELEMENT_TYPE_` *\** sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="27994-112">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="27994-113">'ndaki Parametrenin sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="27994-113">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="27994-114">'ndaki ' Nin Unicode karakterdeki boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="27994-114">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="27994-115">dışı `mdParamDef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="27994-115">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27994-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27994-116">Remarks</span></span>  

 <span data-ttu-id="27994-117">İçindeki sıra değerleri, `ulParamSeq` Parametreler için 1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="27994-117">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="27994-118">Dönüş değerinin sıra numarası 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="27994-118">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27994-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27994-119">Requirements</span></span>  

 <span data-ttu-id="27994-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27994-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27994-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="27994-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27994-122">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="27994-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27994-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27994-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27994-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27994-124">See also</span></span>

- [<span data-ttu-id="27994-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27994-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="27994-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27994-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
