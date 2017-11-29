---
title: "IMetaDataEmit::DefineProperty Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineProperty
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc0403fd51f028510eb60d93ff96fc7d05606366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="80d5f-102">IMetaDataEmit::DefineProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80d5f-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="80d5f-103">Belirtilen türde bir özellik tanımı belirtilen oluşturur `get` ve `set` yöntemi erişimciler ve bu özellik tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="80d5f-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d5f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80d5f-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="80d5f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80d5f-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="80d5f-106">[in] Sınıf veya özellik tanımlanıyorsa arabirim için belirteci.</span><span class="sxs-lookup"><span data-stu-id="80d5f-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="80d5f-107">[in] Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="80d5f-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="80d5f-108">[in] Özellik bayraklar.</span><span class="sxs-lookup"><span data-stu-id="80d5f-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="80d5f-109">[in] Özellik imzası.</span><span class="sxs-lookup"><span data-stu-id="80d5f-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="80d5f-110">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="80d5f-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="80d5f-111">[in] Özelliğin varsayılan değeri türü.</span><span class="sxs-lookup"><span data-stu-id="80d5f-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="80d5f-112">[in] Özelliğin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="80d5f-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="80d5f-113">[in] (Unicode) sayısını karakterleri `pValue`.</span><span class="sxs-lookup"><span data-stu-id="80d5f-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="80d5f-114">[in] Özellik değeri ayarlar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80d5f-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="80d5f-115">[in] Özellik değeri alır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80d5f-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="80d5f-116">[in] Özellik ile ilişkilendirilmiş diğer yöntemleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="80d5f-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="80d5f-117">Dizi ile sonlandırmak bir `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="80d5f-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="80d5f-118">[out] `mdProperty` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="80d5f-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d5f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80d5f-119">Requirements</span></span>  
 <span data-ttu-id="80d5f-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d5f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d5f-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80d5f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80d5f-122">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="80d5f-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80d5f-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d5f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d5f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80d5f-124">See Also</span></span>  
 [<span data-ttu-id="80d5f-125">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="80d5f-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="80d5f-126">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="80d5f-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
