---
title: "IMetaDataImport::EnumProperties Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumProperties
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d46e18707ff6b34e32a73aed81c2b7e57f769ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="66895-102">IMetaDataImport::EnumProperties Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66895-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="66895-103">Belirtilen TypeDef belirteç tarafından başvurulan türünün özelliklerini temsil eden PropertyDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="66895-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66895-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66895-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66895-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66895-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="66895-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="66895-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="66895-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66895-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="66895-108">[in] Numaralandırılacak özellikleri ile türünü temsil eden bir TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="66895-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="66895-109">[out] PropertyDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="66895-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="66895-110">[in] En büyük boyutunu `rProperties` dizi.</span><span class="sxs-lookup"><span data-stu-id="66895-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="66895-111">[out] Döndürülen PropertyDef belirteçleri sayısı `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="66895-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66895-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66895-112">Return Value</span></span>  
  
|<span data-ttu-id="66895-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66895-113">HRESULT</span></span>|<span data-ttu-id="66895-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66895-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="66895-115">`EnumProperties`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="66895-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="66895-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="66895-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="66895-117">Bu durumda, `pcProperties` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="66895-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66895-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66895-118">Requirements</span></span>  
 <span data-ttu-id="66895-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66895-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66895-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66895-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66895-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="66895-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66895-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66895-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66895-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66895-123">See Also</span></span>  
 [<span data-ttu-id="66895-124">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="66895-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="66895-125">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="66895-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
