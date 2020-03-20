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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177709"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="eb272-102">IMetaDataEmit::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb272-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="eb272-103">Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="eb272-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb272-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb272-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="eb272-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb272-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="eb272-106">[içinde] Çevreleyen `mdTypeDef` sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="eb272-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="eb272-107">[içinde] Unicode'daki alan adı.</span><span class="sxs-lookup"><span data-stu-id="eb272-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="eb272-108">[içinde] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="eb272-108">[in] The field attributes.</span></span> <span data-ttu-id="eb272-109">Bu `CorFieldAttr` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="eb272-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="eb272-110">[içinde] BLOB olarak alan imzası.</span><span class="sxs-lookup"><span data-stu-id="eb272-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="eb272-111">[içinde] Bayt `pvSigBlob`sayısı.</span><span class="sxs-lookup"><span data-stu-id="eb272-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="eb272-112">[içinde] Sabit `ELEMENT_TYPE_` *\** değer için.</span><span class="sxs-lookup"><span data-stu-id="eb272-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="eb272-113">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="eb272-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="eb272-114">Alan için sabit bir değer tanımlanmıyorsanız, kullanın. `ELEMENT_TYPE_END`</span><span class="sxs-lookup"><span data-stu-id="eb272-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="eb272-115">[içinde] Alan için sabit değer.</span><span class="sxs-lookup"><span data-stu-id="eb272-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="eb272-116">[içinde] (Unicode) karakterlerinin `pValue`boyutu.</span><span class="sxs-lookup"><span data-stu-id="eb272-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="eb272-117">[çıkış] Atanan `mdFieldDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="eb272-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb272-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb272-118">Requirements</span></span>  
 <span data-ttu-id="eb272-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb272-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb272-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eb272-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb272-121">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="eb272-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb272-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb272-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb272-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb272-123">See also</span></span>

- [<span data-ttu-id="eb272-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb272-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="eb272-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb272-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
