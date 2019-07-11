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
ms.openlocfilehash: 057bae1d702fa091ebc3d3178c9fba35d5dd3d90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777647"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="93560-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93560-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="93560-103">Belirtilen meta verileri imza ile bir alan için bir tanım oluşturur ve bu alan tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="93560-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93560-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93560-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="93560-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93560-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="93560-106">[in] `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="93560-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="93560-107">[in] Unicode alan adı.</span><span class="sxs-lookup"><span data-stu-id="93560-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="93560-108">[in] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="93560-108">[in] The field attributes.</span></span> <span data-ttu-id="93560-109">Bu, bir bit maskesi, `CorFieldAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="93560-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="93560-110">[in] Bir BLOB olarak alan imzası.</span><span class="sxs-lookup"><span data-stu-id="93560-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="93560-111">[in] Bayt sayısı `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="93560-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="93560-112">[in] `ELEMENT_TYPE_` *\** Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="93560-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="93560-113">Bu bir `CorElementType` değeri.</span><span class="sxs-lookup"><span data-stu-id="93560-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="93560-114">Alan için sabit bir değer tanımlamayarak kullanırsanız `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="93560-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="93560-115">[in] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="93560-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="93560-116">[in] \(Unicode) karakter cinsinden boyutu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="93560-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="93560-117">[out] `mdFieldDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="93560-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93560-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93560-118">Requirements</span></span>  
 <span data-ttu-id="93560-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93560-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93560-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="93560-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93560-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="93560-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93560-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93560-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93560-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93560-123">See also</span></span>

- [<span data-ttu-id="93560-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93560-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="93560-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93560-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
