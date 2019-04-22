---
title: IMetaDataEmit::SetPropertyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdee8491b22675fb8dd8fa89e77ebf8541185173
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207903"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="009cb-102">IMetaDataEmit::SetPropertyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="009cb-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="009cb-103">Önceki bir çağrı tarafından tanımlanan bir özellik için meta verileri içinde depolanan özellikleri ayarlar [DefineProperty yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="009cb-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="009cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="009cb-104">Syntax</span></span>  
  
```  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="009cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="009cb-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="009cb-106">[in] Değiştirilecek özellik için belirteç</span><span class="sxs-lookup"><span data-stu-id="009cb-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="009cb-107">[in] Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="009cb-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="009cb-108">[in] Özelliğin varsayılan değeri türü.</span><span class="sxs-lookup"><span data-stu-id="009cb-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="009cb-109">[in] Bir özellik için varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="009cb-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="009cb-110">[in] \(Unicode) sayısını karakterleri `pValue`.</span><span class="sxs-lookup"><span data-stu-id="009cb-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="009cb-111">[in] Özellik değeri ayarlar yönteminin.</span><span class="sxs-lookup"><span data-stu-id="009cb-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="009cb-112">[in] Yöntem özellik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="009cb-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="009cb-113">[in] Özellikle ilişkili diğer yöntemleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="009cb-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="009cb-114">Bu dizi ile sonlandırmak bir `mdTokenNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="009cb-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="009cb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="009cb-115">Requirements</span></span>  
 <span data-ttu-id="009cb-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="009cb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="009cb-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="009cb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="009cb-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="009cb-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="009cb-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="009cb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009cb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="009cb-120">See also</span></span>

- [<span data-ttu-id="009cb-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="009cb-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="009cb-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="009cb-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
