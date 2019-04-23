---
title: IMetaDataImport::EnumMethods Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bab625b8415183b9cf90c35cba140c4d28095805
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076880"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="220c1-102">IMetaDataImport::EnumMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="220c1-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="220c1-103">Belirtilen türün yöntemlerini temsil eden MethodDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="220c1-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="220c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="220c1-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="220c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="220c1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="220c1-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="220c1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="220c1-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="220c1-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="220c1-108">[in] Numaralandırma için yöntemlerle türünü temsil eden bir tür tanımı belirteci.</span><span class="sxs-lookup"><span data-stu-id="220c1-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="220c1-109">[out] MethodDef simgeleri depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="220c1-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="220c1-110">[in] En büyük boyutunu MethodDef `rMethods` dizisi.</span><span class="sxs-lookup"><span data-stu-id="220c1-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="220c1-111">[out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="220c1-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="220c1-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="220c1-112">Return Value</span></span>  
  
|<span data-ttu-id="220c1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="220c1-113">HRESULT</span></span>|<span data-ttu-id="220c1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="220c1-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="220c1-115">`EnumMethods` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="220c1-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="220c1-116">Numaralandırılacak hiçbir MethodDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="220c1-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="220c1-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="220c1-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="220c1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="220c1-118">Requirements</span></span>  
 <span data-ttu-id="220c1-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="220c1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="220c1-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="220c1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="220c1-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="220c1-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="220c1-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="220c1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220c1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="220c1-123">See also</span></span>

- [<span data-ttu-id="220c1-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="220c1-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="220c1-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="220c1-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
