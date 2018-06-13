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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61688ed5201a1bb6721c4db70b380c7b8373c2e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446447"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="716cd-102">IMetaDataEmit::SetParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="716cd-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="716cd-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir yöntem parametresi özelliklerini değiştirir [Imetadataemit::defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="716cd-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="716cd-104">Syntax</span></span>  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="716cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="716cd-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="716cd-106">[in] Hedef parametresi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="716cd-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="716cd-107">[in] Unicode parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="716cd-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="716cd-108">[in] Parametresi için bayrak.</span><span class="sxs-lookup"><span data-stu-id="716cd-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="716cd-109">[in] ELEMENT_TYPE_ \* sabit değer.</span><span class="sxs-lookup"><span data-stu-id="716cd-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="716cd-110">[in] Parametresi için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="716cd-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="716cd-111">[in] \(Unicode) karakter cinsinden boyutu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="716cd-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="716cd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="716cd-112">Requirements</span></span>  
 <span data-ttu-id="716cd-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="716cd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="716cd-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="716cd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="716cd-115">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="716cd-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="716cd-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="716cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716cd-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="716cd-117">See Also</span></span>  
 [<span data-ttu-id="716cd-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="716cd-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="716cd-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="716cd-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
