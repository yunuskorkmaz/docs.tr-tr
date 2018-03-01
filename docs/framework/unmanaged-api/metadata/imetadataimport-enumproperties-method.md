---
title: "IMetaDataImport::EnumProperties Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63ff10904440f55ec3fe6fb6aa581fbf560763e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="e6e9f-102">IMetaDataImport::EnumProperties Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6e9f-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="e6e9f-103">Belirtilen TypeDef belirteç tarafından başvurulan türünün özelliklerini temsil eden PropertyDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e9f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6e9f-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6e9f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6e9f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e6e9f-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e6e9f-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="e6e9f-108">[in] Numaralandırılacak özellikleri ile türünü temsil eden bir TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="e6e9f-109">[out] PropertyDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e6e9f-110">[in] En büyük boyutunu `rProperties` dizi.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="e6e9f-111">[out] Döndürülen PropertyDef belirteçleri sayısı `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6e9f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e6e9f-112">Return Value</span></span>  
  
|<span data-ttu-id="e6e9f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6e9f-113">HRESULT</span></span>|<span data-ttu-id="e6e9f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6e9f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e6e9f-115">`EnumProperties`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e6e9f-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="e6e9f-117">Bu durumda, `pcProperties` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6e9f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6e9f-118">Requirements</span></span>  
 <span data-ttu-id="e6e9f-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6e9f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6e9f-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6e9f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6e9f-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e6e9f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6e9f-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6e9f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e9f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6e9f-123">See Also</span></span>  
 [<span data-ttu-id="e6e9f-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6e9f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e6e9f-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6e9f-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
