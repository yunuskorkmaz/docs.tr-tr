---
title: IMetaDataImport::EnumEvents Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 608b4a7d147124ede60e9d81f91600dfdaad0a65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446502"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="8a829-102">IMetaDataImport::EnumEvents Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a829-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="8a829-103">Belirtilen TypeDef belirteci için olay tanımı belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8a829-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a829-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a829-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a829-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a829-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8a829-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8a829-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="8a829-107">[in] Numaralandırılacak, olay tanımları olan TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="8a829-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="8a829-108">[out] Döndürülen olaylar dizisi.</span><span class="sxs-lookup"><span data-stu-id="8a829-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8a829-109">[in] En büyük boyutunu `rEvents` dizi.</span><span class="sxs-lookup"><span data-stu-id="8a829-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="8a829-110">[out] Döndürülen olayları gerçek sayısını `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="8a829-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a829-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8a829-111">Return Value</span></span>  
  
|<span data-ttu-id="8a829-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a829-112">HRESULT</span></span>|<span data-ttu-id="8a829-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a829-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8a829-114">`EnumEvents` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8a829-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8a829-115">Numaralandırılacak olay yok.</span><span class="sxs-lookup"><span data-stu-id="8a829-115">There are no events to enumerate.</span></span> <span data-ttu-id="8a829-116">Bu durumda, `pcEvents` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="8a829-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a829-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a829-117">Requirements</span></span>  
 <span data-ttu-id="8a829-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a829-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a829-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a829-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a829-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8a829-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a829-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a829-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a829-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a829-122">See Also</span></span>  
 [<span data-ttu-id="8a829-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a829-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8a829-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a829-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
