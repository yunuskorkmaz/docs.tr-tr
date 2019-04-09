---
title: IMetaDataImport::EnumUserStrings Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4be12e46851b11a5e6db60c351094a356fa61f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082951"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="0e7b6-102">IMetaDataImport::EnumUserStrings Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e7b6-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="0e7b6-103">Dize belirteçleri sabit kodlanmış dizeleri geçerli meta veri kapsamda temsil eden numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e7b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e7b6-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e7b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e7b6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0e7b6-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0e7b6-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="0e7b6-108">[out] Dize belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0e7b6-109">[in] En büyük boyutunu `rStrings` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="0e7b6-110">[out] Döndürülen dize belirteçleri sayısı `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e7b6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e7b6-111">Return Value</span></span>  
  
|<span data-ttu-id="0e7b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e7b6-112">HRESULT</span></span>|<span data-ttu-id="0e7b6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e7b6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumUserStrings` <span data-ttu-id="0e7b6-114">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0e7b6-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0e7b6-116">Bu durumda, `pcStrings` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e7b6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e7b6-117">Remarks</span></span>  
 <span data-ttu-id="0e7b6-118">Dize belirteçleri oluşturan [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="0e7b6-119">Bu yöntem, bir meta veri tarayıcısı yerine bir derleyici tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e7b6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e7b6-120">Requirements</span></span>  
 <span data-ttu-id="0e7b6-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e7b6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e7b6-122">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0e7b6-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e7b6-123">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0e7b6-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0e7b6-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0e7b6-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e7b6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e7b6-125">See also</span></span>

- [<span data-ttu-id="0e7b6-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e7b6-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0e7b6-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e7b6-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
