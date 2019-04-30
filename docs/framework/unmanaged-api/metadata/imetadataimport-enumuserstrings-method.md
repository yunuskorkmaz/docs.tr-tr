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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777935"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="b1bad-102">IMetaDataImport::EnumUserStrings Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1bad-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="b1bad-103">Dize belirteçleri sabit kodlanmış dizeleri geçerli meta veri kapsamda temsil eden numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b1bad-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1bad-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1bad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1bad-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b1bad-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1bad-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b1bad-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1bad-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="b1bad-108">[out] Dize belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="b1bad-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b1bad-109">[in] En büyük boyutunu `rStrings` dizisi.</span><span class="sxs-lookup"><span data-stu-id="b1bad-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="b1bad-110">[out] Döndürülen dize belirteçleri sayısı `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="b1bad-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1bad-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1bad-111">Return Value</span></span>  
  
|<span data-ttu-id="b1bad-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1bad-112">HRESULT</span></span>|<span data-ttu-id="b1bad-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1bad-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b1bad-114">`EnumUserStrings` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b1bad-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b1bad-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b1bad-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b1bad-116">Bu durumda, `pcStrings` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="b1bad-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1bad-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1bad-117">Remarks</span></span>  
 <span data-ttu-id="b1bad-118">Dize belirteçleri oluşturan [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b1bad-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="b1bad-119">Bu yöntem, bir meta veri tarayıcısı yerine bir derleyici tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b1bad-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bad-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1bad-120">Requirements</span></span>  
 <span data-ttu-id="b1bad-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bad-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bad-122">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b1bad-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1bad-123">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b1bad-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1bad-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1bad-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bad-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1bad-125">See also</span></span>

- [<span data-ttu-id="b1bad-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1bad-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b1bad-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1bad-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
