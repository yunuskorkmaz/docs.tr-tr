---
title: IMetaDataEmit::SetFieldProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: 0f98fb64b43822c437c39df2f3c51a222ef386b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730402"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="a4e3f-102">IMetaDataEmit::SetFieldProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4e3f-102">IMetaDataEmit::SetFieldProps Method</span></span>

<span data-ttu-id="a4e3f-103">Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değeri ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a4e3f-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e3f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a4e3f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4e3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4e3f-105">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="a4e3f-106">'ndaki Hedef alan için belirteç.</span><span class="sxs-lookup"><span data-stu-id="a4e3f-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="a4e3f-107">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a4e3f-107">[in] Field attributes.</span></span> <span data-ttu-id="a4e3f-108">Bu bir değer bit değeridir `CorFieldAttr` .</span><span class="sxs-lookup"><span data-stu-id="a4e3f-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="a4e3f-109">'ndaki `ELEMENT_TYPE_` *\** Sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="a4e3f-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="a4e3f-110">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="a4e3f-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="a4e3f-111">Bir sabit tanımlanmamışsa, bu değeri olarak ayarlayın `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="a4e3f-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="a4e3f-112">'ndaki Alanın sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="a4e3f-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="a4e3f-113">'ndaki ' Nin Unicode karakterdeki boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="a4e3f-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4e3f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4e3f-114">Requirements</span></span>  

 <span data-ttu-id="a4e3f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4e3f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4e3f-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a4e3f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4e3f-117">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a4e3f-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4e3f-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4e3f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e3f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4e3f-119">See also</span></span>

- [<span data-ttu-id="a4e3f-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4e3f-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a4e3f-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4e3f-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
