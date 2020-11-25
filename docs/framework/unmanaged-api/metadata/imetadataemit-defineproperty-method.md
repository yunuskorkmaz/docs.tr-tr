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
ms.openlocfilehash: d2a4a15126f34666a58021a59e9e193685b15a49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719495"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="94d0e-102">IMetaDataEmit::DefineProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94d0e-102">IMetaDataEmit::DefineProperty Method</span></span>

<span data-ttu-id="94d0e-103">Belirtilen ve Yöntem erişimcilerine sahip olan belirtilen tür için bir özellik tanımı oluşturur `get` `set` ve bu özellik tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="94d0e-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d0e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="94d0e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="94d0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94d0e-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="94d0e-106">'ndaki Üzerinde özelliğin tanımlandığı sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="94d0e-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="94d0e-107">'ndaki Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="94d0e-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="94d0e-108">'ndaki Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="94d0e-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="94d0e-109">'ndaki Özellik imzası.</span><span class="sxs-lookup"><span data-stu-id="94d0e-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="94d0e-110">'ndaki İçindeki bayt sayısı `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="94d0e-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="94d0e-111">'ndaki Özelliğin varsayılan değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="94d0e-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="94d0e-112">'ndaki Özelliğin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="94d0e-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="94d0e-113">'ndaki İçindeki (Unicode) karakterlerin sayısı `pValue` .</span><span class="sxs-lookup"><span data-stu-id="94d0e-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="94d0e-114">'ndaki Özellik değerini ayarlayan yöntem.</span><span class="sxs-lookup"><span data-stu-id="94d0e-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="94d0e-115">'ndaki Özellik değerini alan yöntem.</span><span class="sxs-lookup"><span data-stu-id="94d0e-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="94d0e-116">'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="94d0e-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="94d0e-117">Diziyi bir ile sonlandırın `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="94d0e-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="94d0e-118">dışı `mdProperty` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="94d0e-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94d0e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94d0e-119">Requirements</span></span>  

 <span data-ttu-id="94d0e-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94d0e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94d0e-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="94d0e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94d0e-122">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="94d0e-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94d0e-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94d0e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d0e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94d0e-124">See also</span></span>

- [<span data-ttu-id="94d0e-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94d0e-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="94d0e-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94d0e-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
