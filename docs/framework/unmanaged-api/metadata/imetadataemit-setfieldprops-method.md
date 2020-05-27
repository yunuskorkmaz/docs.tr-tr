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
ms.openlocfilehash: 220556ec130c7bff7c413405820c4fee0582b051
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008020"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="9e732-102">IMetaDataEmit::SetFieldProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e732-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="9e732-103">Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değeri ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e732-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e732-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9e732-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e732-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e732-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="9e732-106">'ndaki Hedef alan için belirteç.</span><span class="sxs-lookup"><span data-stu-id="9e732-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="9e732-107">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="9e732-107">[in] Field attributes.</span></span> <span data-ttu-id="9e732-108">Bu bir değer bit değeridir `CorFieldAttr` .</span><span class="sxs-lookup"><span data-stu-id="9e732-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="9e732-109">'ndaki `ELEMENT_TYPE_` *\** Sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="9e732-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="9e732-110">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e732-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="9e732-111">Bir sabit tanımlanmamışsa, bu değeri olarak ayarlayın `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="9e732-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9e732-112">'ndaki Alanın sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="9e732-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="9e732-113">'ndaki ' Nin Unicode karakterdeki boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="9e732-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e732-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e732-114">Requirements</span></span>  
 <span data-ttu-id="9e732-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e732-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e732-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9e732-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e732-117">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9e732-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e732-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e732-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e732-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e732-119">See also</span></span>

- [<span data-ttu-id="9e732-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e732-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9e732-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e732-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
