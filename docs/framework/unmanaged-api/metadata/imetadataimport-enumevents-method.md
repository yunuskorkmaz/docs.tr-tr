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
ms.openlocfilehash: 2f3d74830de0541ec789081c47352beca8d81d74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780705"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="70f5b-102">IMetaDataImport::EnumEvents Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70f5b-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="70f5b-103">Olay tanımı belirteçleri TypeDef belirteç numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="70f5b-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70f5b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70f5b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70f5b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="70f5b-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="70f5b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="70f5b-107">[in] Numaralandırılacak olan olay tanımlarına olan TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="70f5b-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="70f5b-108">[out] Döndürülen olaylar dizisi.</span><span class="sxs-lookup"><span data-stu-id="70f5b-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="70f5b-109">[in] En büyük boyutunu `rEvents` dizisi.</span><span class="sxs-lookup"><span data-stu-id="70f5b-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="70f5b-110">[out] Döndürülen olaylar gerçek sayısını `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="70f5b-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70f5b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="70f5b-111">Return Value</span></span>  
  
|<span data-ttu-id="70f5b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70f5b-112">HRESULT</span></span>|<span data-ttu-id="70f5b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70f5b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="70f5b-114">`EnumEvents` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="70f5b-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="70f5b-115">Numaralandırılacak olay yok.</span><span class="sxs-lookup"><span data-stu-id="70f5b-115">There are no events to enumerate.</span></span> <span data-ttu-id="70f5b-116">Bu durumda, `pcEvents` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="70f5b-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70f5b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70f5b-117">Requirements</span></span>  
 <span data-ttu-id="70f5b-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70f5b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70f5b-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="70f5b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70f5b-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="70f5b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70f5b-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70f5b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f5b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70f5b-122">See also</span></span>

- [<span data-ttu-id="70f5b-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70f5b-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="70f5b-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70f5b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
