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
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200187"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="d47eb-102">IMetaDataImport::EnumMethodsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d47eb-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="d47eb-103">Belirtilen ada sahip ve belirtilen TypeDef belirteci tarafından başvurulan tür tarafından tanımlanan yöntemlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d47eb-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d47eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d47eb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d47eb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d47eb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d47eb-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d47eb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d47eb-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d47eb-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="d47eb-108">[in] Numaralandırılacak yöntemleri türünü temsil eden bir tür tanımı belirteci.</span><span class="sxs-lookup"><span data-stu-id="d47eb-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="d47eb-109">[in] Numaralandırma kapsamını sınırlayan adı.</span><span class="sxs-lookup"><span data-stu-id="d47eb-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="d47eb-110">[out] Dizi MethodDef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d47eb-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d47eb-111">[in] En büyük boyutunu `rMethods` dizisi.</span><span class="sxs-lookup"><span data-stu-id="d47eb-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d47eb-112">[out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="d47eb-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d47eb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d47eb-113">Remarks</span></span>  
 <span data-ttu-id="d47eb-114">Bu yöntem, alanlar ve yöntemler, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d47eb-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="d47eb-115">Farklı [Imetadataımport::enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` belirtilen ada sahip olmayan tüm yöntemi belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="d47eb-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d47eb-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d47eb-116">Return Value</span></span>  
  
|<span data-ttu-id="d47eb-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d47eb-117">HRESULT</span></span>|<span data-ttu-id="d47eb-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d47eb-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` <span data-ttu-id="d47eb-119">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d47eb-119">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d47eb-120">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="d47eb-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="d47eb-121">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="d47eb-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d47eb-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d47eb-122">Requirements</span></span>  
 <span data-ttu-id="d47eb-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d47eb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d47eb-124">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d47eb-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d47eb-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d47eb-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d47eb-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d47eb-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d47eb-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d47eb-127">See also</span></span>

- [<span data-ttu-id="d47eb-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47eb-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d47eb-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d47eb-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
