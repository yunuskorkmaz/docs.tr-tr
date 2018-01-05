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
ms.workload: dotnet
ms.openlocfilehash: 9f16e66f83925104c4be1e69a476e398f33295a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="68524-102">IMetaDataImport::EnumMethodsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68524-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="68524-103">Belirtilen ada sahip ve belirtilen TypeDef belirteç tarafından başvurulan türü tarafından tanımlanan yöntemlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="68524-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68524-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68524-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="68524-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68524-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="68524-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68524-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="68524-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68524-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="68524-108">[in] Numaralandırılacak olan yöntemleri türünü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="68524-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="68524-109">[in] Numaralandırma kapsamını sınırlar adı.</span><span class="sxs-lookup"><span data-stu-id="68524-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="68524-110">[out] MethodDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="68524-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="68524-111">[in] En büyük boyutunu `rMethods` dizi.</span><span class="sxs-lookup"><span data-stu-id="68524-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="68524-112">[out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="68524-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68524-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68524-113">Remarks</span></span>  
 <span data-ttu-id="68524-114">Bu yöntem, alanları ve yöntemleri, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="68524-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="68524-115">Farklı [Imetadataımport::enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` belirtilen ada sahip olmayan tüm yöntemi belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="68524-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68524-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68524-116">Return Value</span></span>  
  
|<span data-ttu-id="68524-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68524-117">HRESULT</span></span>|<span data-ttu-id="68524-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68524-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="68524-119">`EnumMethodsWithName`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="68524-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="68524-120">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="68524-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="68524-121">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="68524-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68524-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68524-122">Requirements</span></span>  
 <span data-ttu-id="68524-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68524-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68524-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="68524-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68524-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="68524-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68524-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68524-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68524-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68524-127">See Also</span></span>  
 [<span data-ttu-id="68524-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68524-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="68524-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68524-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
