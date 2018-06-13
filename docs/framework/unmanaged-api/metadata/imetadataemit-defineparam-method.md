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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d49ac70aceb76f69711ea4bf514f69697ac156c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447378"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="f94e7-102">IMetaDataEmit::DefineParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f94e7-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="f94e7-103">Belirtilen belirteç tarafından başvurulan yöntemi için belirtilen imzalı bir parametrenin tanımını oluşturur ve bu parametre tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="f94e7-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f94e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f94e7-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="f94e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f94e7-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f94e7-106">[in] Parametresi tanımlı yöntemi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="f94e7-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="f94e7-107">[in] Parametre sıra numarası.</span><span class="sxs-lookup"><span data-stu-id="f94e7-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="f94e7-108">[in] Unicode parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="f94e7-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="f94e7-109">[in] Parametresi için işaretler.</span><span class="sxs-lookup"><span data-stu-id="f94e7-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="f94e7-110">Bu, bir bit maskesi olan `CorParamAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="f94e7-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="f94e7-111">[in] `ELEMENT_TYPE_` *\** sabit değer.</span><span class="sxs-lookup"><span data-stu-id="f94e7-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f94e7-112">[in] Parametresi için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="f94e7-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="f94e7-113">[in] Unicode karakterler, boyutunu, `pValue`.</span><span class="sxs-lookup"><span data-stu-id="f94e7-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="f94e7-114">[out] `mdParamDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="f94e7-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f94e7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f94e7-115">Remarks</span></span>  
 <span data-ttu-id="f94e7-116">Sıralı değerler `ulParamSeq` parametreleri için 1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="f94e7-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="f94e7-117">Dönüş değeri bir sıra numarası 0 sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f94e7-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f94e7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f94e7-118">Requirements</span></span>  
 <span data-ttu-id="f94e7-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f94e7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f94e7-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f94e7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f94e7-121">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f94e7-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f94e7-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f94e7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94e7-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f94e7-123">See Also</span></span>  
 [<span data-ttu-id="f94e7-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f94e7-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f94e7-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f94e7-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
