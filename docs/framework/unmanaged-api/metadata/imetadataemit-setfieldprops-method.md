---
description: ': Imetadatayayma:: SetFieldProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ee9964077e556a1d0666a836ca0c3bab92540252
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658015"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="acc76-103">IMetaDataEmit::SetFieldProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acc76-103">IMetaDataEmit::SetFieldProps Method</span></span>

<span data-ttu-id="acc76-104">Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değeri ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="acc76-104">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acc76-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acc76-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acc76-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acc76-106">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="acc76-107">'ndaki Hedef alan için belirteç.</span><span class="sxs-lookup"><span data-stu-id="acc76-107">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="acc76-108">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="acc76-108">[in] Field attributes.</span></span> <span data-ttu-id="acc76-109">Bu bir değer bit değeridir `CorFieldAttr` .</span><span class="sxs-lookup"><span data-stu-id="acc76-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="acc76-110">'ndaki `ELEMENT_TYPE_` *\** Sabit değer için.</span><span class="sxs-lookup"><span data-stu-id="acc76-110">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="acc76-111">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="acc76-111">This is a `CorElementType` value.</span></span> <span data-ttu-id="acc76-112">Bir sabit tanımlanmamışsa, bu değeri olarak ayarlayın `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="acc76-112">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="acc76-113">'ndaki Alanın sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="acc76-113">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="acc76-114">'ndaki ' Nin Unicode karakterdeki boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="acc76-114">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acc76-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acc76-115">Requirements</span></span>  

 <span data-ttu-id="acc76-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acc76-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acc76-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="acc76-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="acc76-118">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="acc76-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acc76-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acc76-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc76-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acc76-120">See also</span></span>

- [<span data-ttu-id="acc76-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acc76-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="acc76-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acc76-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
