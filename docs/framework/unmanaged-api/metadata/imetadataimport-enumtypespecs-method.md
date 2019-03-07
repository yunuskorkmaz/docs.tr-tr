---
title: IMetaDataImport::EnumTypeSpecs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4babdd6e0cea0d951b4cd8708d8007d431f97cf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500297"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="bf65d-102">IMetaDataImport::EnumTypeSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf65d-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="bf65d-103">Geçerli meta veri kapsamda tanımlanan TypeSpec'te belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="bf65d-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf65d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf65d-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf65d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf65d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bf65d-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bf65d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bf65d-107">Bu değer, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf65d-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="bf65d-108">[out] TypeSpec'te simgeleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="bf65d-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bf65d-109">[in] En büyük boyutunu `rTypeSpecs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="bf65d-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="bf65d-110">[out] Döndürülen TypeSpec'te belirteçleri sayısı `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="bf65d-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf65d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bf65d-111">Return Value</span></span>  
  
|<span data-ttu-id="bf65d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf65d-112">HRESULT</span></span>|<span data-ttu-id="bf65d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf65d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bf65d-114">`EnumTypeSpecs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bf65d-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bf65d-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bf65d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bf65d-116">Bu durumda, `pcTypeSpecs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="bf65d-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf65d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf65d-117">Remarks</span></span>  
 <span data-ttu-id="bf65d-118">TypeSpec'te belirteçleri oluşturan [Imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bf65d-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf65d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf65d-119">Requirements</span></span>  
 <span data-ttu-id="bf65d-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf65d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf65d-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bf65d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf65d-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bf65d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf65d-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf65d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf65d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf65d-124">See also</span></span>
- [<span data-ttu-id="bf65d-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf65d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bf65d-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf65d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
