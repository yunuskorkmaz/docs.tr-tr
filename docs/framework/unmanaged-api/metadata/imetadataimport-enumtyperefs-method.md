---
title: IMetaDataImport::EnumTypeRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8a4fe2a65244156abe1bb0da4266f949ddd3df6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447080"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="46638-102">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46638-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="46638-103">Geçerli meta veri kapsamda tanımlı TypeRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="46638-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46638-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46638-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46638-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46638-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="46638-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46638-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="46638-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46638-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="46638-108">[out] TypeRef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="46638-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="46638-109">[in] En büyük boyutunu `rTypeRefs` dizi.</span><span class="sxs-lookup"><span data-stu-id="46638-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="46638-110">[out] Döndürülen TypeRef belirteçleri sayısını gösteren bir işaretçi `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="46638-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46638-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="46638-111">Return Value</span></span>  
  
|<span data-ttu-id="46638-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46638-112">HRESULT</span></span>|<span data-ttu-id="46638-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46638-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="46638-114">`EnumTypeRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="46638-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="46638-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="46638-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="46638-116">Bu durumda, `pcTypeRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="46638-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46638-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46638-117">Remarks</span></span>  
 <span data-ttu-id="46638-118">TypeRef belirteci türüne bir başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46638-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46638-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46638-119">Requirements</span></span>  
 <span data-ttu-id="46638-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46638-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46638-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="46638-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46638-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="46638-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46638-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46638-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46638-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46638-124">See Also</span></span>  
 [<span data-ttu-id="46638-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46638-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="46638-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46638-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
