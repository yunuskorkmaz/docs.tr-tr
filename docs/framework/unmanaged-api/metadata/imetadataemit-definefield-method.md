---
title: IMetaDataEmit::DefineField Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0ddda898911da2c96a53d941c4290af9028154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446580"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="ff55d-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff55d-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="ff55d-103">Belirtilen meta veri imzayla bir alan için bir tanım oluşturur ve bu alan tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="ff55d-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff55d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff55d-104">Syntax</span></span>  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff55d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff55d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ff55d-106">[in] `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="ff55d-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="ff55d-107">[in] Unicode alanın adı.</span><span class="sxs-lookup"><span data-stu-id="ff55d-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="ff55d-108">[in] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="ff55d-108">[in] The field attributes.</span></span> <span data-ttu-id="ff55d-109">Bu, bir bit maskesi olan `CorFieldAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="ff55d-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ff55d-110">[in] Bir BLOB alan imzası.</span><span class="sxs-lookup"><span data-stu-id="ff55d-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ff55d-111">[in] Bayt sayısı `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ff55d-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="ff55d-112">[in] `ELEMENT_TYPE_` *\** Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="ff55d-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="ff55d-113">Bu bir `CorElementType` değeri.</span><span class="sxs-lookup"><span data-stu-id="ff55d-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="ff55d-114">Alan için sabit bir değer tanımlama değil kullanırsanız `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="ff55d-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ff55d-115">[in] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff55d-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ff55d-116">[in] \(Unicode) karakter cinsinden boyutu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="ff55d-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="ff55d-117">[out] `mdFieldDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="ff55d-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff55d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff55d-118">Requirements</span></span>  
 <span data-ttu-id="ff55d-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff55d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff55d-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff55d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff55d-121">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ff55d-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff55d-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff55d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff55d-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff55d-123">See Also</span></span>  
 [<span data-ttu-id="ff55d-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff55d-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ff55d-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff55d-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
