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
ms.openlocfilehash: 65dbbeb76c1f31044fddf6df69c4daf63617c079
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480396"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="e0a22-102">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0a22-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="e0a22-103">Geçerli meta veri kapsamda tanımlanan TypeRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e0a22-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0a22-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0a22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0a22-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e0a22-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0a22-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e0a22-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0a22-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="e0a22-108">[out] TypeRef simgeleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="e0a22-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e0a22-109">[in] En büyük boyutunu `rTypeRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="e0a22-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="e0a22-110">[out] Döndürülen TypeRef belirteçleri sayısı için bir işaretçi `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="e0a22-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0a22-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e0a22-111">Return Value</span></span>  
  
|<span data-ttu-id="e0a22-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0a22-112">HRESULT</span></span>|<span data-ttu-id="e0a22-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0a22-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e0a22-114">`EnumTypeRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e0a22-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e0a22-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e0a22-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e0a22-116">Bu durumda, `pcTypeRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e0a22-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0a22-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0a22-117">Remarks</span></span>  
 <span data-ttu-id="e0a22-118">TypeRef belirteci bir türü bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0a22-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0a22-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0a22-119">Requirements</span></span>  
 <span data-ttu-id="e0a22-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a22-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a22-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e0a22-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0a22-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e0a22-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0a22-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a22-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a22-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0a22-124">See also</span></span>
- [<span data-ttu-id="e0a22-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0a22-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e0a22-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0a22-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
