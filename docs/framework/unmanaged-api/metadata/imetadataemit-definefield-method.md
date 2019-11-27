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
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432550"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="80c2c-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80c2c-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="80c2c-103">Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="80c2c-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80c2c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="80c2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80c2c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="80c2c-106">'ndaki Kapsayan sınıf veya arabirim için `mdTypeDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="80c2c-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="80c2c-107">'ndaki Unicode 'daki alan adı.</span><span class="sxs-lookup"><span data-stu-id="80c2c-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="80c2c-108">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="80c2c-108">[in] The field attributes.</span></span> <span data-ttu-id="80c2c-109">Bu, `CorFieldAttr` değerlerinin bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="80c2c-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="80c2c-110">'ndaki BLOB olarak alan imzası.</span><span class="sxs-lookup"><span data-stu-id="80c2c-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="80c2c-111">'ndaki `pvSigBlob`bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="80c2c-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="80c2c-112">'ndaki Sabit değer için `ELEMENT_TYPE_` *\** .</span><span class="sxs-lookup"><span data-stu-id="80c2c-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="80c2c-113">Bu bir `CorElementType` değeridir.</span><span class="sxs-lookup"><span data-stu-id="80c2c-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="80c2c-114">Alan için sabit bir değer tanımlamadıysanız `ELEMENT_TYPE_END`kullanın.</span><span class="sxs-lookup"><span data-stu-id="80c2c-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="80c2c-115">'ndaki Alanın sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="80c2c-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="80c2c-116">'ndaki `pValue`(Unicode) karakter boyutu.</span><span class="sxs-lookup"><span data-stu-id="80c2c-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="80c2c-117">dışı `mdFieldDef` belirteci atandı.</span><span class="sxs-lookup"><span data-stu-id="80c2c-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80c2c-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80c2c-118">Requirements</span></span>  
 <span data-ttu-id="80c2c-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c2c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c2c-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="80c2c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80c2c-121">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="80c2c-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80c2c-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c2c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c2c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80c2c-123">See also</span></span>

- [<span data-ttu-id="80c2c-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c2c-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="80c2c-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c2c-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
