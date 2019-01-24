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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71cdfc6b05288fef020e1aed1870a9a155588d47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543087"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="1f3bc-102">IMetaDataEmit::DefineProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f3bc-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="1f3bc-103">Belirtilen tür için bir özellik tanımı belirtilen oluşturur `get` ve `set` yöntemi erişimcileri ve bu özellik tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f3bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f3bc-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1f3bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f3bc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="1f3bc-106">[in] Sınıf veya arabirim özelliği tanımlanmakta olan belirteci.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="1f3bc-107">[in] Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="1f3bc-108">[in] Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="1f3bc-109">[in] Özellik imzası.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="1f3bc-110">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="1f3bc-111">[in] Özelliğin varsayılan değeri türü.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="1f3bc-112">[in] Bir özellik için varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="1f3bc-113">[in] \(Unicode) sayısını karakterleri `pValue`.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="1f3bc-114">[in] Özellik değeri ayarlar yönteminin.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="1f3bc-115">[in] Yöntem özellik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="1f3bc-116">[in] Özellikle ilişkili diğer yöntemleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="1f3bc-117">Dizi sonlandırmak bir `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="1f3bc-118">[out] `mdProperty` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f3bc-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f3bc-119">Requirements</span></span>  
 <span data-ttu-id="1f3bc-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f3bc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f3bc-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1f3bc-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f3bc-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1f3bc-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f3bc-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f3bc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f3bc-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f3bc-124">See also</span></span>
- [<span data-ttu-id="1f3bc-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f3bc-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1f3bc-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f3bc-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
