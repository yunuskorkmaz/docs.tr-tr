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
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177549"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="b3886-102">IMetaDataEmit::SetFieldProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3886-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="b3886-103">Belirtilen alan belirteci tarafından başvurulan alanın varsayılan değerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b3886-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3886-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3886-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3886-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3886-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="b3886-106">[içinde] Hedef alanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="b3886-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="b3886-107">[içinde] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="b3886-107">[in] Field attributes.</span></span> <span data-ttu-id="b3886-108">Bu `CorFieldAttr` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="b3886-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="b3886-109">[içinde] Sabit `ELEMENT_TYPE_` *\** değer için.</span><span class="sxs-lookup"><span data-stu-id="b3886-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="b3886-110">Bu bir `CorElementType` değerdir.</span><span class="sxs-lookup"><span data-stu-id="b3886-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="b3886-111">Bir sabit tanımlanmıyorsa, bu `ELEMENT_TYPE_END`değeri .</span><span class="sxs-lookup"><span data-stu-id="b3886-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b3886-112">[içinde] Alan için sabit değer.</span><span class="sxs-lookup"><span data-stu-id="b3886-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="b3886-113">[içinde] Unicode karakterlerinin boyutu. `pValue`</span><span class="sxs-lookup"><span data-stu-id="b3886-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3886-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3886-114">Requirements</span></span>  
 <span data-ttu-id="b3886-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3886-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3886-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3886-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3886-117">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b3886-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3886-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3886-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3886-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3886-119">See also</span></span>

- [<span data-ttu-id="b3886-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3886-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b3886-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3886-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
