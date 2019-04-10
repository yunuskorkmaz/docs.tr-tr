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
ms.openlocfilehash: a8ba8a762c56a666c67b25b9ce0420099fce419a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223530"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="03a25-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03a25-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="03a25-103">Belirtilen meta verileri imza ile bir alan için bir tanım oluşturur ve bu alan tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="03a25-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03a25-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="03a25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03a25-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="03a25-106">[in] `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="03a25-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="03a25-107">[in] Unicode alan adı.</span><span class="sxs-lookup"><span data-stu-id="03a25-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="03a25-108">[in] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="03a25-108">[in] The field attributes.</span></span> <span data-ttu-id="03a25-109">Bu, bir bit maskesi, `CorFieldAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="03a25-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="03a25-110">[in] Bir BLOB olarak alan imzası.</span><span class="sxs-lookup"><span data-stu-id="03a25-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="03a25-111">[in] Bayt sayısı `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="03a25-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="03a25-112">[in] `ELEMENT_TYPE_` *\** Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="03a25-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="03a25-113">Bu bir `CorElementType` değeri.</span><span class="sxs-lookup"><span data-stu-id="03a25-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="03a25-114">Alan için sabit bir değer tanımlamayarak kullanırsanız `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="03a25-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="03a25-115">[in] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="03a25-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="03a25-116">[in] \(Unicode) karakter cinsinden boyutu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="03a25-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="03a25-117">[out] `mdFieldDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="03a25-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a25-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03a25-118">Requirements</span></span>  
 <span data-ttu-id="03a25-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03a25-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a25-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="03a25-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03a25-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="03a25-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="03a25-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="03a25-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03a25-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03a25-123">See also</span></span>

- [<span data-ttu-id="03a25-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03a25-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="03a25-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03a25-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
