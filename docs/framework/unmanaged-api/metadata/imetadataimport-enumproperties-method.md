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
ms.openlocfilehash: ad29204e445bc61b6dc9753d594f0e4bf62930fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448579"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="4deec-102">IMetaDataImport::EnumProperties Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4deec-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="4deec-103">Belirtilen TypeDef belirteç tarafından başvurulan türünün özelliklerini temsil eden PropertyDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="4deec-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4deec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4deec-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4deec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4deec-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4deec-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4deec-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4deec-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4deec-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="4deec-108">[in] Numaralandırılacak özellikleri ile türünü temsil eden bir TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="4deec-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="4deec-109">[out] PropertyDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="4deec-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4deec-110">[in] En büyük boyutunu `rProperties` dizi.</span><span class="sxs-lookup"><span data-stu-id="4deec-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="4deec-111">[out] Döndürülen PropertyDef belirteçleri sayısı `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="4deec-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4deec-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4deec-112">Return Value</span></span>  
  
|<span data-ttu-id="4deec-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4deec-113">HRESULT</span></span>|<span data-ttu-id="4deec-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4deec-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4deec-115">`EnumProperties` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4deec-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4deec-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="4deec-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="4deec-117">Bu durumda, `pcProperties` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="4deec-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4deec-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4deec-118">Requirements</span></span>  
 <span data-ttu-id="4deec-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4deec-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4deec-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4deec-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4deec-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4deec-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4deec-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4deec-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4deec-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4deec-123">See Also</span></span>  
 [<span data-ttu-id="4deec-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4deec-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4deec-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4deec-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
