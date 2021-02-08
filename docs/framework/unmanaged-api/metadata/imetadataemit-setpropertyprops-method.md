---
description: ': Imetadatayayma:: SetPropertyProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ad5efa86b4f774bcaa2251cb992c2dd52ac28bdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771840"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="d06c6-103">IMetaDataEmit::SetPropertyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d06c6-103">IMetaDataEmit::SetPropertyProps Method</span></span>

<span data-ttu-id="d06c6-104">[DefineProperty metoduna](imetadataemit-defineproperty-method.md)önceki bir çağrı tarafından tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d06c6-104">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d06c6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d06c6-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d06c6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d06c6-106">Parameters</span></span>  

 `pr`  
 <span data-ttu-id="d06c6-107">'ndaki Değiştirilecek özelliğin belirteci</span><span class="sxs-lookup"><span data-stu-id="d06c6-107">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="d06c6-108">'ndaki Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="d06c6-108">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d06c6-109">'ndaki Özelliğin varsayılan değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="d06c6-109">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d06c6-110">'ndaki Özelliğin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="d06c6-110">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d06c6-111">'ndaki İçindeki (Unicode) karakterlerin sayısı `pValue` .</span><span class="sxs-lookup"><span data-stu-id="d06c6-111">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="d06c6-112">'ndaki Özellik değerini ayarlayan yöntem.</span><span class="sxs-lookup"><span data-stu-id="d06c6-112">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="d06c6-113">'ndaki Özellik değerini alan yöntem.</span><span class="sxs-lookup"><span data-stu-id="d06c6-113">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d06c6-114">'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="d06c6-114">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="d06c6-115">Bu diziyi bir belirteçle sonlandırın `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="d06c6-115">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d06c6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d06c6-116">Requirements</span></span>  

 <span data-ttu-id="d06c6-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d06c6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d06c6-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d06c6-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d06c6-119">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d06c6-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d06c6-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d06c6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06c6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d06c6-121">See also</span></span>

- [<span data-ttu-id="d06c6-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d06c6-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d06c6-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d06c6-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
