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
ms.openlocfilehash: e5d4ddd43b27d733a63c2e0dc5e92ffd2ba94a7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175440"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="afa87-102">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afa87-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="afa87-103">Geçerli meta veri kapsamında tanımlanan TypeRef belirteçlerini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="afa87-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afa87-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afa87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afa87-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="afa87-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="afa87-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="afa87-107">Bu yöntemin ilk araması için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="afa87-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="afa87-108">[çıkış] TypeRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="afa87-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="afa87-109">[içinde] `rTypeRefs` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="afa87-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="afa87-110">[çıkış] TypeRef belirteçlerinin sayısına işaretçi. `rTypeRefs`</span><span class="sxs-lookup"><span data-stu-id="afa87-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afa87-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="afa87-111">Return Value</span></span>  
  
|<span data-ttu-id="afa87-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="afa87-112">HRESULT</span></span>|<span data-ttu-id="afa87-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afa87-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="afa87-114">`EnumTypeRefs`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="afa87-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="afa87-115">Sayısala rendelemek için hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="afa87-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="afa87-116">Bu durumda, `pcTypeRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="afa87-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afa87-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afa87-117">Remarks</span></span>  
 <span data-ttu-id="afa87-118">TypeRef belirteci, bir türe yapılan başvuruyciyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="afa87-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afa87-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afa87-119">Requirements</span></span>  
 <span data-ttu-id="afa87-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afa87-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afa87-121">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="afa87-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afa87-122">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="afa87-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afa87-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afa87-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa87-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afa87-124">See also</span></span>

- [<span data-ttu-id="afa87-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa87-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="afa87-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa87-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
