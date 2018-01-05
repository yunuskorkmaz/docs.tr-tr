---
title: "IMetaDataEmit::DefineField Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2c4b5604c3daec78744eb8902a30750571b9f82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="a80a4-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a80a4-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="a80a4-103">Belirtilen meta veri imzayla bir alan için bir tanım oluşturur ve bu alan tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="a80a4-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a80a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a80a4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a80a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a80a4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a80a4-106">[in] `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="a80a4-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="a80a4-107">[in] Unicode alanın adı.</span><span class="sxs-lookup"><span data-stu-id="a80a4-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="a80a4-108">[in] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a80a4-108">[in] The field attributes.</span></span> <span data-ttu-id="a80a4-109">Bu, bir bit maskesi olan `CorFieldAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="a80a4-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a80a4-110">[in] Bir BLOB alan imzası.</span><span class="sxs-lookup"><span data-stu-id="a80a4-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a80a4-111">[in] Bayt sayısı `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a80a4-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="a80a4-112">[in] `ELEMENT_TYPE_`  *\**  Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="a80a4-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="a80a4-113">Bu bir `CorElementType` değeri.</span><span class="sxs-lookup"><span data-stu-id="a80a4-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="a80a4-114">Alan için sabit bir değer tanımlama değil kullanırsanız `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="a80a4-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="a80a4-115">[in] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="a80a4-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="a80a4-116">[in] (Unicode) karakter cinsinden boyutu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="a80a4-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="a80a4-117">[out] `mdFieldDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="a80a4-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a80a4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a80a4-118">Requirements</span></span>  
 <span data-ttu-id="a80a4-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a80a4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a80a4-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a80a4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a80a4-121">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a80a4-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a80a4-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a80a4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80a4-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a80a4-123">See Also</span></span>  
 [<span data-ttu-id="a80a4-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a80a4-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a80a4-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a80a4-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
