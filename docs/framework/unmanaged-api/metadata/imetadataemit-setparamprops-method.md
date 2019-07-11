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
ms.openlocfilehash: f8448de17ad974bc77021a7880b7d8576c69ae75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750919"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="b1205-102">IMetaDataEmit::SetParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1205-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="b1205-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir yöntem parametresi özelliklerini değiştirir [Imetadataemit::defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="b1205-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1205-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1205-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b1205-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1205-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="b1205-106">[in] Hedef parametresi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="b1205-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="b1205-107">[in] Unicode parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="b1205-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="b1205-108">[in] Parametresi için bayrakları.</span><span class="sxs-lookup"><span data-stu-id="b1205-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="b1205-109">[in] ELEMENT_TYPE_ \* sabit değer.</span><span class="sxs-lookup"><span data-stu-id="b1205-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b1205-110">[in] Parametresi için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="b1205-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="b1205-111">[in] \(Unicode) karakter cinsinden boyutu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="b1205-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1205-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1205-112">Requirements</span></span>  
 <span data-ttu-id="b1205-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1205-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1205-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b1205-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1205-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="b1205-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1205-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1205-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1205-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1205-117">See also</span></span>

- [<span data-ttu-id="b1205-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1205-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b1205-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1205-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
