---
title: "IMetaDataImport::EnumMethodsWithName Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dadff8be283160ddc6049d0d2f8b78052e5c8ec5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="3f1fb-102">IMetaDataImport::EnumMethodsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f1fb-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="3f1fb-103">Belirtilen ada sahip ve belirtilen TypeDef belirteç tarafından başvurulan türü tarafından tanımlanan yöntemlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f1fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f1fb-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f1fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f1fb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3f1fb-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3f1fb-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="3f1fb-108">[in] Numaralandırılacak olan yöntemleri türünü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="3f1fb-109">[in] Numaralandırma kapsamını sınırlar adı.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="3f1fb-110">[out] MethodDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3f1fb-111">[in] En büyük boyutunu `rMethods` dizi.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3f1fb-112">[out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f1fb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f1fb-113">Remarks</span></span>  
 <span data-ttu-id="3f1fb-114">Bu yöntem, alanları ve yöntemleri, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="3f1fb-115">Farklı [Imetadataımport::enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` belirtilen ada sahip olmayan tüm yöntemi belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f1fb-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f1fb-116">Return Value</span></span>  
  
|<span data-ttu-id="3f1fb-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f1fb-117">HRESULT</span></span>|<span data-ttu-id="3f1fb-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f1fb-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3f1fb-119">`EnumMethodsWithName`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3f1fb-120">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="3f1fb-121">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f1fb-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f1fb-122">Requirements</span></span>  
 <span data-ttu-id="3f1fb-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f1fb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f1fb-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f1fb-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f1fb-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3f1fb-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f1fb-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f1fb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f1fb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f1fb-127">See Also</span></span>  
 [<span data-ttu-id="3f1fb-128">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f1fb-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3f1fb-129">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f1fb-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
