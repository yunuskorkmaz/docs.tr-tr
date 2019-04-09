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
ms.openlocfilehash: de0fe4a51fbb49e80377b6b434bf3b72ddb90f02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081629"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="c49a7-102">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c49a7-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="c49a7-103">Geçerli meta veri kapsamda tanımlanan TypeRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c49a7-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c49a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c49a7-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c49a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c49a7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c49a7-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c49a7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c49a7-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c49a7-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="c49a7-108">[out] TypeRef simgeleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="c49a7-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c49a7-109">[in] En büyük boyutunu `rTypeRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="c49a7-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="c49a7-110">[out] Döndürülen TypeRef belirteçleri sayısı için bir işaretçi `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="c49a7-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c49a7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c49a7-111">Return Value</span></span>  
  
|<span data-ttu-id="c49a7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c49a7-112">HRESULT</span></span>|<span data-ttu-id="c49a7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c49a7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeRefs` <span data-ttu-id="c49a7-114">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c49a7-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c49a7-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="c49a7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c49a7-116">Bu durumda, `pcTypeRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="c49a7-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c49a7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c49a7-117">Remarks</span></span>  
 <span data-ttu-id="c49a7-118">TypeRef belirteci bir türü bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c49a7-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c49a7-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c49a7-119">Requirements</span></span>  
 <span data-ttu-id="c49a7-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c49a7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c49a7-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c49a7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c49a7-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c49a7-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c49a7-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c49a7-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c49a7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c49a7-124">See also</span></span>

- [<span data-ttu-id="c49a7-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c49a7-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c49a7-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c49a7-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
