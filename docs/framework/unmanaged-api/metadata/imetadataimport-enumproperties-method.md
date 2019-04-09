---
title: IMetaDataImport::EnumProperties Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 410fd7a702d3aa3812b4ea053c43fdaa507a474a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176044"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="66c5e-102">IMetaDataImport::EnumProperties Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66c5e-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="66c5e-103">Belirtilen tür tanımı belirteci tarafından başvurulan türünün özelliklerini temsil eden PropertyDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="66c5e-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c5e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66c5e-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66c5e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66c5e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="66c5e-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="66c5e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="66c5e-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66c5e-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="66c5e-108">[in] Numaralandırılacak özelliklere sahip türünü temsil eden bir tür tanımı belirteci.</span><span class="sxs-lookup"><span data-stu-id="66c5e-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="66c5e-109">[out] Dizi PropertyDef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66c5e-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="66c5e-110">[in] En büyük boyutunu `rProperties` dizisi.</span><span class="sxs-lookup"><span data-stu-id="66c5e-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="66c5e-111">[out] Döndürülen PropertyDef belirteçleri sayısı `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="66c5e-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66c5e-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66c5e-112">Return Value</span></span>  
  
|<span data-ttu-id="66c5e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66c5e-113">HRESULT</span></span>|<span data-ttu-id="66c5e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66c5e-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumProperties` <span data-ttu-id="66c5e-115">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="66c5e-115">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="66c5e-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="66c5e-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="66c5e-117">Bu durumda, `pcProperties` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="66c5e-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66c5e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66c5e-118">Requirements</span></span>  
 <span data-ttu-id="66c5e-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c5e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c5e-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="66c5e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66c5e-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="66c5e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="66c5e-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="66c5e-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="66c5e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66c5e-123">See also</span></span>

- [<span data-ttu-id="66c5e-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66c5e-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="66c5e-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66c5e-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
