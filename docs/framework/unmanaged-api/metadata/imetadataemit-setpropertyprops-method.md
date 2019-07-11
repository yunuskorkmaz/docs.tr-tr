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
ms.openlocfilehash: 9e78c4d7319a931ca7090d6f99651bc9660e4af8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782046"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="6d5df-102">IMetaDataEmit::SetPropertyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d5df-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="6d5df-103">Önceki bir çağrı tarafından tanımlanan bir özellik için meta verileri içinde depolanan özellikleri ayarlar [DefineProperty yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="6d5df-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d5df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d5df-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="6d5df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d5df-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="6d5df-106">[in] Değiştirilecek özellik için belirteç</span><span class="sxs-lookup"><span data-stu-id="6d5df-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="6d5df-107">[in] Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6d5df-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="6d5df-108">[in] Özelliğin varsayılan değeri türü.</span><span class="sxs-lookup"><span data-stu-id="6d5df-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="6d5df-109">[in] Bir özellik için varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="6d5df-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="6d5df-110">[in] \(Unicode) sayısını karakterleri `pValue`.</span><span class="sxs-lookup"><span data-stu-id="6d5df-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="6d5df-111">[in] Özellik değeri ayarlar yönteminin.</span><span class="sxs-lookup"><span data-stu-id="6d5df-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="6d5df-112">[in] Yöntem özellik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6d5df-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="6d5df-113">[in] Özellikle ilişkili diğer yöntemleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="6d5df-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="6d5df-114">Bu dizi ile sonlandırmak bir `mdTokenNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="6d5df-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d5df-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d5df-115">Requirements</span></span>  
 <span data-ttu-id="6d5df-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d5df-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d5df-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6d5df-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d5df-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6d5df-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d5df-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d5df-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d5df-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d5df-120">See also</span></span>

- [<span data-ttu-id="6d5df-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d5df-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6d5df-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d5df-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
