---
title: "IMetaDataImport::EnumUserStrings Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3d9c802318203db2ccd6043cded3c7730b18b0cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="31ba6-102">IMetaDataImport::EnumUserStrings Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31ba6-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="31ba6-103">Geçerli meta veri kapsamı sabit kodlanmış dizelerde temsil eden dize belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="31ba6-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ba6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31ba6-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31ba6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31ba6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="31ba6-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31ba6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="31ba6-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31ba6-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="31ba6-108">[out] Dize belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="31ba6-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="31ba6-109">[in] En büyük boyutunu `rStrings` dizi.</span><span class="sxs-lookup"><span data-stu-id="31ba6-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="31ba6-110">[out] Döndürülen dize belirteçleri sayısı `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="31ba6-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31ba6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="31ba6-111">Return Value</span></span>  
  
|<span data-ttu-id="31ba6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31ba6-112">HRESULT</span></span>|<span data-ttu-id="31ba6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31ba6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="31ba6-114">`EnumUserStrings`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="31ba6-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="31ba6-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="31ba6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="31ba6-116">Bu durumda, `pcStrings` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="31ba6-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31ba6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31ba6-117">Remarks</span></span>  
 <span data-ttu-id="31ba6-118">Dize belirteçleri tarafından oluşturulan [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31ba6-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="31ba6-119">Bu yöntem, bir meta veri tarayıcı yerine bir derleyici tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="31ba6-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ba6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31ba6-120">Requirements</span></span>  
 <span data-ttu-id="31ba6-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31ba6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31ba6-122">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31ba6-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31ba6-123">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="31ba6-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31ba6-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31ba6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ba6-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31ba6-125">See Also</span></span>  
 [<span data-ttu-id="31ba6-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31ba6-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="31ba6-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31ba6-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
