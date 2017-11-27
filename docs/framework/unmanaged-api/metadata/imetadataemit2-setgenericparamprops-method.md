---
title: "IMetaDataEmit2::SetGenericParamProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SetGenericParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5de54b3d113c8d43bd004b18e0a6cb22b1051dc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="e7803-102">IMetaDataEmit2::SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7803-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="e7803-103">Belirtilen belirteç tarafından başvurulan genel parametresini tanımı için özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e7803-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7803-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7803-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7803-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7803-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="e7803-106">[in] Hangi değerlerini ayarlamak genel parametresini tanımı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="e7803-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e7803-107">[in] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) türünü genel parametresi için açıklayan numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="e7803-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="e7803-108">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e7803-108">[in] Optional.</span></span> <span data-ttu-id="e7803-109">Değerleri ayarlanacak parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="e7803-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="e7803-110">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e7803-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="e7803-111">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e7803-111">[in] Optional.</span></span> <span data-ttu-id="e7803-112">Tür kısıtlamaları sıfır sonlandırılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="e7803-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="e7803-113">Dizi üyeleri olmalıdır bir `mdTypeDef`, `mdTypeRef`, veya `mdTypeSpec` meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="e7803-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7803-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7803-114">Requirements</span></span>  
 <span data-ttu-id="e7803-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7803-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7803-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e7803-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7803-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e7803-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7803-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7803-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7803-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7803-119">See Also</span></span>  
 [<span data-ttu-id="e7803-120">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7803-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="e7803-121">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7803-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
