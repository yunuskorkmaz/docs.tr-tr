---
title: IMetaDataImport::EnumMethodsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cea47f8300c57362abae0c10223559319ecb2469
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448849"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="643f0-102">IMetaDataImport::EnumMethodsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="643f0-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="643f0-103">Belirtilen ada sahip ve belirtilen TypeDef belirteç tarafından başvurulan türü tarafından tanımlanan yöntemlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="643f0-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="643f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="643f0-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="643f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="643f0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="643f0-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="643f0-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="643f0-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="643f0-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="643f0-108">[in] Numaralandırılacak olan yöntemleri türünü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="643f0-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="643f0-109">[in] Numaralandırma kapsamını sınırlar adı.</span><span class="sxs-lookup"><span data-stu-id="643f0-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="643f0-110">[out] MethodDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="643f0-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="643f0-111">[in] En büyük boyutunu `rMethods` dizi.</span><span class="sxs-lookup"><span data-stu-id="643f0-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="643f0-112">[out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="643f0-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="643f0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="643f0-113">Remarks</span></span>  
 <span data-ttu-id="643f0-114">Bu yöntem, alanları ve yöntemleri, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="643f0-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="643f0-115">Farklı [Imetadataımport::enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` belirtilen ada sahip olmayan tüm yöntemi belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="643f0-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="643f0-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="643f0-116">Return Value</span></span>  
  
|<span data-ttu-id="643f0-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="643f0-117">HRESULT</span></span>|<span data-ttu-id="643f0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="643f0-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="643f0-119">`EnumMethodsWithName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="643f0-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="643f0-120">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="643f0-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="643f0-121">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="643f0-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="643f0-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="643f0-122">Requirements</span></span>  
 <span data-ttu-id="643f0-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="643f0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="643f0-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="643f0-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="643f0-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="643f0-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="643f0-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643f0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643f0-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="643f0-127">See Also</span></span>  
 [<span data-ttu-id="643f0-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="643f0-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="643f0-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="643f0-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
