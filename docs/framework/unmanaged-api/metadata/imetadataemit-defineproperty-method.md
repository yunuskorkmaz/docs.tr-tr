---
title: IMetaDataEmit::DefineProperty Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175791"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="bca23-102">IMetaDataEmit::DefineProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bca23-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="bca23-103">Belirtilen tür için, belirtilen `get` ve `set` yöntem etekleri ile bir özellik tanımı oluşturur ve bu özellik tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="bca23-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca23-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bca23-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bca23-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bca23-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="bca23-106">[içinde] Özelliğin tanımlandığı sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="bca23-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="bca23-107">[içinde] Mülkün adı.</span><span class="sxs-lookup"><span data-stu-id="bca23-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="bca23-108">[içinde] Mülk bayrakları.</span><span class="sxs-lookup"><span data-stu-id="bca23-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="bca23-109">[içinde] Mülk imzası.</span><span class="sxs-lookup"><span data-stu-id="bca23-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="bca23-110">[içinde] Bayt `pvSig`sayısı.</span><span class="sxs-lookup"><span data-stu-id="bca23-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="bca23-111">[içinde] Özelliğin varsayılan değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="bca23-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="bca23-112">[içinde] Özellik için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="bca23-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="bca23-113">[içinde] (Unicode) karakter `pValue`sayısı.</span><span class="sxs-lookup"><span data-stu-id="bca23-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="bca23-114">[içinde] Özellik değerini ayarlayan yöntem.</span><span class="sxs-lookup"><span data-stu-id="bca23-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="bca23-115">[içinde] Özellik değerini alan yöntem.</span><span class="sxs-lookup"><span data-stu-id="bca23-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="bca23-116">[içinde] Özellik ile ilişkili diğer yöntemler dizisi.</span><span class="sxs-lookup"><span data-stu-id="bca23-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="bca23-117">Diziyi bir `mdTokenNil`ile sonlandırın</span><span class="sxs-lookup"><span data-stu-id="bca23-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="bca23-118">[çıkış] Atanan `mdProperty` belirteç.</span><span class="sxs-lookup"><span data-stu-id="bca23-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca23-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bca23-119">Requirements</span></span>  
 <span data-ttu-id="bca23-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca23-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca23-121">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bca23-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bca23-122">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bca23-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bca23-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca23-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca23-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bca23-124">See also</span></span>

- [<span data-ttu-id="bca23-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bca23-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bca23-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bca23-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
