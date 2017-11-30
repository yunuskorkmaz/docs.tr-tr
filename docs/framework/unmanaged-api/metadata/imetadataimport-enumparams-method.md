---
title: "IMetaDataImport::EnumParams Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42555e1300016222e9ea8064e90fa3062d79db6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="61ad2-102">IMetaDataImport::EnumParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61ad2-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="61ad2-103">Belirtilen MethodDef belirteç tarafından başvurulan yönteminin parametreleri temsil eden ParamDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="61ad2-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ad2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61ad2-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61ad2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61ad2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="61ad2-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61ad2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="61ad2-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="61ad2-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="61ad2-108">[in] Numaralandırma parametrelerle yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="61ad2-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="61ad2-109">[out] ParamDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="61ad2-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="61ad2-110">[in] En büyük boyutunu `rParams` dizi.</span><span class="sxs-lookup"><span data-stu-id="61ad2-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="61ad2-111">[out] Döndürülen ParamDef belirteçleri sayısı `rParams`.</span><span class="sxs-lookup"><span data-stu-id="61ad2-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61ad2-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61ad2-112">Return Value</span></span>  
  
|<span data-ttu-id="61ad2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61ad2-113">HRESULT</span></span>|<span data-ttu-id="61ad2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61ad2-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="61ad2-115">`EnumParams`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="61ad2-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="61ad2-116">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="61ad2-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="61ad2-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="61ad2-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61ad2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61ad2-118">Requirements</span></span>  
 <span data-ttu-id="61ad2-119">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ad2-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ad2-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61ad2-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61ad2-121">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="61ad2-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61ad2-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ad2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ad2-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61ad2-123">See Also</span></span>  
 [<span data-ttu-id="61ad2-124">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="61ad2-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="61ad2-125">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="61ad2-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
