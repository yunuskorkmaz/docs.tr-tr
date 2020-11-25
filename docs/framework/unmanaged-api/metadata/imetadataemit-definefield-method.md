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
ms.openlocfilehash: 2bc2b983171dc41d5ac37eda0359f1aaee4ebd6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725761"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="997ab-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="997ab-102">IMetaDataEmit::DefineField Method</span></span>

<span data-ttu-id="997ab-103">Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="997ab-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="997ab-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="997ab-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="997ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="997ab-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="997ab-106">'ndaki `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="997ab-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="997ab-107">'ndaki Unicode 'daki alan adı.</span><span class="sxs-lookup"><span data-stu-id="997ab-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="997ab-108">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="997ab-108">[in] The field attributes.</span></span> <span data-ttu-id="997ab-109">Bu bir değer bit değeridir `CorFieldAttr` .</span><span class="sxs-lookup"><span data-stu-id="997ab-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="997ab-110">'ndaki BLOB olarak alan imzası.</span><span class="sxs-lookup"><span data-stu-id="997ab-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="997ab-111">'ndaki İçindeki bayt sayısı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="997ab-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="997ab-112">'ndaki `ELEMENT_TYPE_` *\** Sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="997ab-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="997ab-113">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="997ab-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="997ab-114">Alan için sabit bir değer tanımlamadıysanız kullanın `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="997ab-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="997ab-115">'ndaki Alanın sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="997ab-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="997ab-116">'ndaki (Unicode) karakter boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="997ab-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="997ab-117">dışı `mdFieldDef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="997ab-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="997ab-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="997ab-118">Requirements</span></span>  

 <span data-ttu-id="997ab-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="997ab-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="997ab-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="997ab-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="997ab-121">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="997ab-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="997ab-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="997ab-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997ab-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="997ab-123">See also</span></span>

- [<span data-ttu-id="997ab-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="997ab-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="997ab-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="997ab-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
