---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineProperty yöntemi'
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
ms.openlocfilehash: c0c0b6009f8674a5edebf1c982e277f4ca5b185b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784041"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="7b197-103">IMetaDataEmit::DefineProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b197-103">IMetaDataEmit::DefineProperty Method</span></span>

<span data-ttu-id="7b197-104">Belirtilen ve Yöntem erişimcilerine sahip olan belirtilen tür için bir özellik tanımı oluşturur `get` `set` ve bu özellik tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="7b197-104">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b197-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b197-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7b197-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b197-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="7b197-107">'ndaki Üzerinde özelliğin tanımlandığı sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="7b197-107">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="7b197-108">'ndaki Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="7b197-108">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="7b197-109">'ndaki Özellik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="7b197-109">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="7b197-110">'ndaki Özellik imzası.</span><span class="sxs-lookup"><span data-stu-id="7b197-110">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="7b197-111">'ndaki İçindeki bayt sayısı `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="7b197-111">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7b197-112">'ndaki Özelliğin varsayılan değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="7b197-112">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7b197-113">'ndaki Özelliğin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="7b197-113">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7b197-114">'ndaki İçindeki (Unicode) karakterlerin sayısı `pValue` .</span><span class="sxs-lookup"><span data-stu-id="7b197-114">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="7b197-115">'ndaki Özellik değerini ayarlayan yöntem.</span><span class="sxs-lookup"><span data-stu-id="7b197-115">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="7b197-116">'ndaki Özellik değerini alan yöntem.</span><span class="sxs-lookup"><span data-stu-id="7b197-116">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="7b197-117">'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="7b197-117">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="7b197-118">Diziyi bir ile sonlandırın `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="7b197-118">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="7b197-119">dışı `mdProperty` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="7b197-119">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b197-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b197-120">Requirements</span></span>  

 <span data-ttu-id="7b197-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b197-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b197-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7b197-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b197-123">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7b197-123">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b197-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b197-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b197-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b197-125">See also</span></span>

- [<span data-ttu-id="7b197-126">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b197-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7b197-127">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b197-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
