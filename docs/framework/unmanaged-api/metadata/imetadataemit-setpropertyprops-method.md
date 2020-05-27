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
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007786"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="5047a-102">IMetaDataEmit::SetPropertyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5047a-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="5047a-103">[DefineProperty metoduna](imetadataemit-defineproperty-method.md)önceki bir çağrı tarafından tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5047a-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5047a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5047a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5047a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5047a-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="5047a-106">'ndaki Değiştirilecek özelliğin belirteci</span><span class="sxs-lookup"><span data-stu-id="5047a-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="5047a-107">'ndaki Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="5047a-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="5047a-108">'ndaki Özelliğin varsayılan değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="5047a-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="5047a-109">'ndaki Özelliğin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="5047a-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="5047a-110">'ndaki İçindeki (Unicode) karakterlerin sayısı `pValue` .</span><span class="sxs-lookup"><span data-stu-id="5047a-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="5047a-111">'ndaki Özellik değerini ayarlayan yöntem.</span><span class="sxs-lookup"><span data-stu-id="5047a-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="5047a-112">'ndaki Özellik değerini alan yöntem.</span><span class="sxs-lookup"><span data-stu-id="5047a-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="5047a-113">'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="5047a-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="5047a-114">Bu diziyi bir belirteçle sonlandırın `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="5047a-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5047a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5047a-115">Requirements</span></span>  
 <span data-ttu-id="5047a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5047a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5047a-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5047a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5047a-118">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5047a-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5047a-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5047a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5047a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5047a-120">See also</span></span>

- [<span data-ttu-id="5047a-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5047a-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5047a-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5047a-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
