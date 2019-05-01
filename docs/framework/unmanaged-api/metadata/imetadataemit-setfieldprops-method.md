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
ms.openlocfilehash: 94ba607669b4b1ca68294470cf1cc4fb27464d28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992491"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="73e20-102">IMetaDataEmit::SetFieldProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73e20-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="73e20-103">Belirtilen alan belirteci tarafından başvurulan alan için varsayılan değer güncelleştirir veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="73e20-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73e20-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73e20-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73e20-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="73e20-106">[in] Hedef alan belirteci.</span><span class="sxs-lookup"><span data-stu-id="73e20-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="73e20-107">[in] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="73e20-107">[in] Field attributes.</span></span> <span data-ttu-id="73e20-108">Bu, bir bit maskesi, `CorFieldAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="73e20-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="73e20-109">[in] `ELEMENT_TYPE_` *\** Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="73e20-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="73e20-110">Bu bir `CorElementType` değeri.</span><span class="sxs-lookup"><span data-stu-id="73e20-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="73e20-111">Bir sabit tanımlı değilse, bu değeri ayarlamak `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="73e20-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="73e20-112">[in] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="73e20-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="73e20-113">[in] Unicode karakter cinsinden boyutu, `pValue`.</span><span class="sxs-lookup"><span data-stu-id="73e20-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73e20-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73e20-114">Requirements</span></span>  
 <span data-ttu-id="73e20-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e20-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e20-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="73e20-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73e20-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="73e20-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73e20-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e20-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e20-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73e20-119">See also</span></span>

- [<span data-ttu-id="73e20-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73e20-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="73e20-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73e20-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
