---
title: "IMetaDataImport::EnumModuleRefs Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 782b363ddf518d45ac5e5fc2b2e4b1c68aff8ea3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="e1521-102">IMetaDataImport::EnumModuleRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1521-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="e1521-103">İçeri aktarılan modülleri temsil ModuleRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e1521-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1521-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1521-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1521-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1521-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e1521-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1521-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e1521-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1521-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="e1521-108">[out] ModuleRef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="e1521-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e1521-109">[in] En büyük boyutunu `rModuleRefs` dizi.</span><span class="sxs-lookup"><span data-stu-id="e1521-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="e1521-110">[out] Döndürülen ModuleRef belirteçleri sayısı `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="e1521-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1521-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1521-111">Return Value</span></span>  
  
|<span data-ttu-id="e1521-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1521-112">HRESULT</span></span>|<span data-ttu-id="e1521-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1521-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e1521-114">`EnumModuleRefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e1521-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e1521-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e1521-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e1521-116">Bu durumda, `pcModuleRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e1521-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1521-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1521-117">Requirements</span></span>  
 <span data-ttu-id="e1521-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1521-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1521-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1521-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1521-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e1521-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1521-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1521-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1521-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1521-122">See Also</span></span>  
 [<span data-ttu-id="e1521-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1521-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e1521-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1521-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
