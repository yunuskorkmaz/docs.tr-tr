---
title: "IMetaDataImport::EnumEvents Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumEvents
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba893d59f9f119ce2f7eaf1af4ce268b6534acd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="3f6c9-102">IMetaDataImport::EnumEvents Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f6c9-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="3f6c9-103">Belirtilen TypeDef belirteci için olay tanımı belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f6c9-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f6c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f6c9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3f6c9-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="3f6c9-107">[in] Numaralandırılacak, olay tanımları olan TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="3f6c9-108">[out] Döndürülen olaylar dizisi.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3f6c9-109">[in] En büyük boyutunu `rEvents` dizi.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="3f6c9-110">[out] Döndürülen olayları gerçek sayısını `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f6c9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f6c9-111">Return Value</span></span>  
  
|<span data-ttu-id="3f6c9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f6c9-112">HRESULT</span></span>|<span data-ttu-id="3f6c9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f6c9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3f6c9-114">`EnumEvents`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3f6c9-115">Numaralandırılacak olay yok.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-115">There are no events to enumerate.</span></span> <span data-ttu-id="3f6c9-116">Bu durumda, `pcEvents` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f6c9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f6c9-117">Requirements</span></span>  
 <span data-ttu-id="3f6c9-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f6c9-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f6c9-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f6c9-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3f6c9-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f6c9-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f6c9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6c9-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f6c9-122">See Also</span></span>  
 [<span data-ttu-id="3f6c9-123">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f6c9-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3f6c9-124">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f6c9-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
