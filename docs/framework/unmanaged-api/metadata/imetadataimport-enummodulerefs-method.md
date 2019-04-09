---
title: IMetaDataImport::EnumModuleRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d66d24da05bc3b8f0c3d0a828456d7c61613d219
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188317"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="2f843-102">IMetaDataImport::EnumModuleRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f843-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="2f843-103">İçeri aktarılan modülleri temsil eden ModuleRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2f843-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f843-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f843-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f843-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f843-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2f843-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f843-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2f843-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f843-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="2f843-108">[out] Dizi ModuleRef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f843-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2f843-109">[in] En büyük boyutunu `rModuleRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="2f843-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="2f843-110">[out] Döndürülen ModuleRef belirteçleri sayısı `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="2f843-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f843-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2f843-111">Return Value</span></span>  
  
|<span data-ttu-id="2f843-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f843-112">HRESULT</span></span>|<span data-ttu-id="2f843-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f843-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumModuleRefs` <span data-ttu-id="2f843-114">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2f843-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2f843-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2f843-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2f843-116">Bu durumda, `pcModuleRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2f843-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f843-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f843-117">Requirements</span></span>  
 <span data-ttu-id="2f843-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f843-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f843-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2f843-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f843-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2f843-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2f843-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2f843-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2f843-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f843-122">See also</span></span>

- [<span data-ttu-id="2f843-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f843-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2f843-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f843-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
