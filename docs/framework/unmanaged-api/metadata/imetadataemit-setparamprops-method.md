---
title: IMetaDataEmit::SetParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: b0cc28807938bcfb9b2465093ff4cfb94066ee98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675067"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="e07a2-102">IMetaDataEmit::SetParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e07a2-102">IMetaDataEmit::SetParamProps Method</span></span>

<span data-ttu-id="e07a2-103">Imetadatayayma için önceki bir çağrı tarafından tanımlanan bir yöntem parametresinin özelliklerini ayarlar veya değiştirir [::D efineParam](imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="e07a2-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07a2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e07a2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e07a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e07a2-105">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="e07a2-106">'ndaki Hedef parametrenin belirteci.</span><span class="sxs-lookup"><span data-stu-id="e07a2-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="e07a2-107">'ndaki Parametrenin Unicode olarak adı.</span><span class="sxs-lookup"><span data-stu-id="e07a2-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e07a2-108">'ndaki Parametresinin bayrakları.</span><span class="sxs-lookup"><span data-stu-id="e07a2-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e07a2-109">'ndaki Sabit değer için ELEMENT_TYPE_ \*.</span><span class="sxs-lookup"><span data-stu-id="e07a2-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e07a2-110">'ndaki Parametrenin sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="e07a2-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e07a2-111">'ndaki (Unicode) karakter boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="e07a2-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07a2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e07a2-112">Requirements</span></span>  

 <span data-ttu-id="e07a2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e07a2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e07a2-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e07a2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e07a2-115">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e07a2-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e07a2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e07a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e07a2-117">See also</span></span>

- [<span data-ttu-id="e07a2-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e07a2-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e07a2-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e07a2-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
