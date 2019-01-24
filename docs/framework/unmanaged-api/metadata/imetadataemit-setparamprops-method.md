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
ms.openlocfilehash: b2885d89883ab6312c2ad9d3feac405eef2fbede
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693697"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="6a1d0-102">IMetaDataEmit::SetParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a1d0-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="6a1d0-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir yöntem parametresi özelliklerini değiştirir [Imetadataemit::defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a1d0-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a1d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a1d0-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="6a1d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a1d0-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="6a1d0-106">[in] Hedef parametresi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="6a1d0-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="6a1d0-107">[in] Unicode parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="6a1d0-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="6a1d0-108">[in] Parametresi için bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6a1d0-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="6a1d0-109">[in] ELEMENT_TYPE_ \* sabit değer.</span><span class="sxs-lookup"><span data-stu-id="6a1d0-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="6a1d0-110">[in] Parametresi için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="6a1d0-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="6a1d0-111">[in] \(Unicode) karakter cinsinden boyutu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="6a1d0-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a1d0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a1d0-112">Requirements</span></span>  
 <span data-ttu-id="6a1d0-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a1d0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a1d0-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6a1d0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a1d0-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6a1d0-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a1d0-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a1d0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1d0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a1d0-117">See also</span></span>
- [<span data-ttu-id="6a1d0-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a1d0-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6a1d0-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a1d0-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
