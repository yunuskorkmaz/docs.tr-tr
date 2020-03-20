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
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177471"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="1782c-102">IMetaDataEmit::SetPropertyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1782c-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="1782c-103">[DefineProperty Yöntemi'ne](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)önceki bir çağrıyla tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1782c-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1782c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1782c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1782c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1782c-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="1782c-106">[içinde] Özelliğin değiştirilecek belirteci</span><span class="sxs-lookup"><span data-stu-id="1782c-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="1782c-107">[içinde] Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="1782c-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="1782c-108">[içinde] Özelliğin varsayılan değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="1782c-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="1782c-109">[içinde] Özellik için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="1782c-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="1782c-110">[içinde] (Unicode) karakter `pValue`sayısı.</span><span class="sxs-lookup"><span data-stu-id="1782c-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="1782c-111">[içinde] Özellik değerini ayarlayan yöntem.</span><span class="sxs-lookup"><span data-stu-id="1782c-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="1782c-112">[içinde] Özellik değerini alan yöntem.</span><span class="sxs-lookup"><span data-stu-id="1782c-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="1782c-113">[içinde] Özellik ile ilişkili diğer yöntemler dizisi.</span><span class="sxs-lookup"><span data-stu-id="1782c-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="1782c-114">Bu diziyi `mdTokenNil` bir belirteçle sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="1782c-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1782c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1782c-115">Requirements</span></span>  
 <span data-ttu-id="1782c-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1782c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1782c-117">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1782c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1782c-118">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1782c-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1782c-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1782c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1782c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1782c-120">See also</span></span>

- [<span data-ttu-id="1782c-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1782c-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1782c-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1782c-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
