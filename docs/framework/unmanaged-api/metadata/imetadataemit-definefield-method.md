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
ms.openlocfilehash: ccc4843864f375c167acdb12575c282dbe3a49e1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004822"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="131fe-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="131fe-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="131fe-103">Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="131fe-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="131fe-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="131fe-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="131fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="131fe-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="131fe-106">'ndaki `mdTypeDef`Kapsayan sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="131fe-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="131fe-107">'ndaki Unicode 'daki alan adı.</span><span class="sxs-lookup"><span data-stu-id="131fe-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="131fe-108">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="131fe-108">[in] The field attributes.</span></span> <span data-ttu-id="131fe-109">Bu bir değer bit değeridir `CorFieldAttr` .</span><span class="sxs-lookup"><span data-stu-id="131fe-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="131fe-110">'ndaki BLOB olarak alan imzası.</span><span class="sxs-lookup"><span data-stu-id="131fe-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="131fe-111">'ndaki İçindeki bayt sayısı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="131fe-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="131fe-112">'ndaki `ELEMENT_TYPE_` *\** Sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="131fe-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="131fe-113">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="131fe-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="131fe-114">Alan için sabit bir değer tanımlamadıysanız kullanın `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="131fe-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="131fe-115">'ndaki Alanın sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="131fe-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="131fe-116">'ndaki (Unicode) karakter boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="131fe-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="131fe-117">dışı `mdFieldDef`Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="131fe-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="131fe-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="131fe-118">Requirements</span></span>  
 <span data-ttu-id="131fe-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="131fe-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="131fe-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="131fe-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="131fe-121">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="131fe-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="131fe-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="131fe-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131fe-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="131fe-123">See also</span></span>

- [<span data-ttu-id="131fe-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="131fe-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="131fe-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="131fe-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
