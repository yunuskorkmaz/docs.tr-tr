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
ms.openlocfilehash: 86711d107636505ab7aa23f0f72f70bd3e27635d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167778"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="cf14f-102">IMetaDataEmit::DefineParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf14f-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="cf14f-103">Belirtilen belirteç tarafından başvurulan yöntemi için belirtilen imzaya sahip bir parametre tanımında oluşturur ve bu parametre tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="cf14f-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf14f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf14f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cf14f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf14f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="cf14f-106">[in] Parametresi tanımlı yöntem için belirteç.</span><span class="sxs-lookup"><span data-stu-id="cf14f-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="cf14f-107">[in] Parametre dizisi numarası.</span><span class="sxs-lookup"><span data-stu-id="cf14f-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="cf14f-108">[in] Unicode parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="cf14f-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="cf14f-109">[in] Parametresi için bayrakları.</span><span class="sxs-lookup"><span data-stu-id="cf14f-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="cf14f-110">Bu, bir bit maskesi, `CorParamAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="cf14f-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="cf14f-111">[in] `ELEMENT_TYPE_` *\** sabit değer.</span><span class="sxs-lookup"><span data-stu-id="cf14f-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="cf14f-112">[in] Parametresi için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="cf14f-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="cf14f-113">[in] Unicode karakter cinsinden boyutu, `pValue`.</span><span class="sxs-lookup"><span data-stu-id="cf14f-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="cf14f-114">[out] `mdParamDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="cf14f-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf14f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf14f-115">Remarks</span></span>  
 <span data-ttu-id="cf14f-116">Sıralı değerleri `ulParamSeq` parametreleri için 1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="cf14f-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="cf14f-117">Dönüş değeri bir sıra numarası 0 sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cf14f-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf14f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf14f-118">Requirements</span></span>  
 <span data-ttu-id="cf14f-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf14f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf14f-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="cf14f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf14f-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="cf14f-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf14f-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf14f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf14f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf14f-123">See also</span></span>

- [<span data-ttu-id="cf14f-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf14f-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cf14f-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf14f-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
