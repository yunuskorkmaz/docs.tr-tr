---
title: "IMetaDataImport::EnumEvents Yöntemi"
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
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ed783cf80fb068656855c2c06ab814f665f1cede
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="16652-102">IMetaDataImport::EnumEvents Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16652-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="16652-103">Belirtilen TypeDef belirteci için olay tanımı belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="16652-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16652-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16652-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16652-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16652-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="16652-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16652-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="16652-107">[in] Numaralandırılacak, olay tanımları olan TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="16652-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="16652-108">[out] Döndürülen olaylar dizisi.</span><span class="sxs-lookup"><span data-stu-id="16652-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="16652-109">[in] En büyük boyutunu `rEvents` dizi.</span><span class="sxs-lookup"><span data-stu-id="16652-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="16652-110">[out] Döndürülen olayları gerçek sayısını `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="16652-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16652-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="16652-111">Return Value</span></span>  
  
|<span data-ttu-id="16652-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16652-112">HRESULT</span></span>|<span data-ttu-id="16652-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16652-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="16652-114">`EnumEvents`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="16652-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="16652-115">Numaralandırılacak olay yok.</span><span class="sxs-lookup"><span data-stu-id="16652-115">There are no events to enumerate.</span></span> <span data-ttu-id="16652-116">Bu durumda, `pcEvents` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="16652-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16652-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16652-117">Requirements</span></span>  
 <span data-ttu-id="16652-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16652-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16652-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16652-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16652-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="16652-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16652-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16652-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16652-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16652-122">See Also</span></span>  
 [<span data-ttu-id="16652-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16652-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="16652-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16652-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
