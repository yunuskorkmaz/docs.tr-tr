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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a2c38340614e633de4049515b38cb387031739b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446042"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="7a877-102">IMetaDataEmit::SetFieldProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a877-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="7a877-103">Belirtilen alan belirteci tarafından başvurulan bir alan için varsayılan değer güncelleştirir veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7a877-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a877-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a877-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a877-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a877-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="7a877-106">[in] Hedef alan için belirteci.</span><span class="sxs-lookup"><span data-stu-id="7a877-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="7a877-107">[in] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="7a877-107">[in] Field attributes.</span></span> <span data-ttu-id="7a877-108">Bu, bir bit maskesi olan `CorFieldAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="7a877-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7a877-109">[in] `ELEMENT_TYPE_` *\** Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="7a877-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="7a877-110">Bu bir `CorElementType` değeri.</span><span class="sxs-lookup"><span data-stu-id="7a877-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="7a877-111">Bir sabit tanımlanmazsa, bu değer ayarlanırsa `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="7a877-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7a877-112">[in] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="7a877-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7a877-113">[in] Unicode karakterler, boyutunu, `pValue`.</span><span class="sxs-lookup"><span data-stu-id="7a877-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a877-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a877-114">Requirements</span></span>  
 <span data-ttu-id="7a877-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a877-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a877-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7a877-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a877-117">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7a877-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a877-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a877-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a877-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a877-119">See Also</span></span>  
 [<span data-ttu-id="7a877-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a877-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7a877-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a877-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
