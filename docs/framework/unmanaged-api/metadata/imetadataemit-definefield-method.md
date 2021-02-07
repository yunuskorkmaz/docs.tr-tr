---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineField yöntemi'
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
ms.openlocfilehash: 7636b1521de721cc183305e8a0763ff0a61f331b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753452"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="d8f3d-103">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8f3d-103">IMetaDataEmit::DefineField Method</span></span>

<span data-ttu-id="d8f3d-104">Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-104">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f3d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8f3d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d8f3d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8f3d-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="d8f3d-107">'ndaki `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-107">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="d8f3d-108">'ndaki Unicode 'daki alan adı.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-108">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="d8f3d-109">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-109">[in] The field attributes.</span></span> <span data-ttu-id="d8f3d-110">Bu bir değer bit değeridir `CorFieldAttr` .</span><span class="sxs-lookup"><span data-stu-id="d8f3d-110">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d8f3d-111">'ndaki BLOB olarak alan imzası.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-111">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d8f3d-112">'ndaki İçindeki bayt sayısı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d8f3d-112">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d8f3d-113">'ndaki `ELEMENT_TYPE_` *\** Sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-113">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="d8f3d-114">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-114">This is a `CorElementType` value.</span></span> <span data-ttu-id="d8f3d-115">Alan için sabit bir değer tanımlamadıysanız kullanın `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="d8f3d-115">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d8f3d-116">'ndaki Alanın sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-116">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d8f3d-117">'ndaki (Unicode) karakter boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="d8f3d-117">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="d8f3d-118">dışı `mdFieldDef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-118">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8f3d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8f3d-119">Requirements</span></span>  

 <span data-ttu-id="d8f3d-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8f3d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8f3d-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d8f3d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8f3d-122">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d8f3d-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8f3d-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8f3d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f3d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8f3d-124">See also</span></span>

- [<span data-ttu-id="d8f3d-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8f3d-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d8f3d-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8f3d-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
