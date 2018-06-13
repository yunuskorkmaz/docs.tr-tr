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
ms.openlocfilehash: 98b99493e54b123d37eb281455180b9a25baddd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446836"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="13faa-102">IMetaDataImport::EnumUserStrings Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13faa-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="13faa-103">Geçerli meta veri kapsamı sabit kodlanmış dizelerde temsil eden dize belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="13faa-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13faa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13faa-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13faa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13faa-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="13faa-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13faa-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="13faa-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13faa-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="13faa-108">[out] Dize belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="13faa-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="13faa-109">[in] En büyük boyutunu `rStrings` dizi.</span><span class="sxs-lookup"><span data-stu-id="13faa-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="13faa-110">[out] Döndürülen dize belirteçleri sayısı `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="13faa-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13faa-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13faa-111">Return Value</span></span>  
  
|<span data-ttu-id="13faa-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13faa-112">HRESULT</span></span>|<span data-ttu-id="13faa-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13faa-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="13faa-114">`EnumUserStrings` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13faa-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="13faa-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="13faa-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="13faa-116">Bu durumda, `pcStrings` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="13faa-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13faa-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13faa-117">Remarks</span></span>  
 <span data-ttu-id="13faa-118">Dize belirteçleri tarafından oluşturulan [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="13faa-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="13faa-119">Bu yöntem, bir meta veri tarayıcı yerine bir derleyici tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="13faa-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13faa-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13faa-120">Requirements</span></span>  
 <span data-ttu-id="13faa-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13faa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13faa-122">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13faa-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13faa-123">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13faa-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13faa-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13faa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13faa-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13faa-125">See Also</span></span>  
 [<span data-ttu-id="13faa-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13faa-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="13faa-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13faa-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
