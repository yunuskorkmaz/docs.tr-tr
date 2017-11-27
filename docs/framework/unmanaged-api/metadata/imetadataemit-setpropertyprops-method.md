---
title: "IMetaDataEmit::SetPropertyProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe79846b9fd576941c706b48a7aed0667c264a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="a7b29-102">IMetaDataEmit::SetPropertyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7b29-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="a7b29-103">Önceki bir çağrı tarafından tanımlanmış bir özellik için meta verilerde depolanan özellikleri ayarlar [DefineProperty yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="a7b29-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7b29-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a7b29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7b29-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="a7b29-106">[in] Değiştirilecek bir özellik için belirteci</span><span class="sxs-lookup"><span data-stu-id="a7b29-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="a7b29-107">[in] Özellik bayraklar.</span><span class="sxs-lookup"><span data-stu-id="a7b29-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="a7b29-108">[in] Özelliğin varsayılan değeri türü.</span><span class="sxs-lookup"><span data-stu-id="a7b29-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="a7b29-109">[in] Özelliğin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="a7b29-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="a7b29-110">[in] (Unicode) sayısını karakterleri `pValue`.</span><span class="sxs-lookup"><span data-stu-id="a7b29-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="a7b29-111">[in] Özellik değeri ayarlar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7b29-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="a7b29-112">[in] Özellik değeri alır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7b29-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="a7b29-113">[in] Özellik ile ilişkilendirilmiş diğer yöntemleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="a7b29-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="a7b29-114">Bu diziyle sonlandırmak bir `mdTokenNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="a7b29-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b29-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7b29-115">Requirements</span></span>  
 <span data-ttu-id="a7b29-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7b29-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b29-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7b29-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7b29-118">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a7b29-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7b29-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b29-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b29-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7b29-120">See Also</span></span>  
 [<span data-ttu-id="a7b29-121">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7b29-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a7b29-122">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7b29-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
