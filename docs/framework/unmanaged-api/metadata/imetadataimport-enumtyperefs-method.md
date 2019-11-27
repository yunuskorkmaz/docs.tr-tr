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
ms.openlocfilehash: 778ebf1d4fad0c8703964be88fdc3ff8c033bc28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449988"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="6f27b-102">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f27b-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="6f27b-103">Geçerli meta veri kapsamında tanımlanan TypeRef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="6f27b-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f27b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f27b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f27b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f27b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6f27b-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f27b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6f27b-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f27b-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="6f27b-108">dışı TypeRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="6f27b-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6f27b-109">'ndaki `rTypeRefs` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="6f27b-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="6f27b-110">dışı `rTypeRefs`döndürülen TypeRef belirteçleri sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f27b-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f27b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6f27b-111">Return Value</span></span>  
  
|<span data-ttu-id="6f27b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f27b-112">HRESULT</span></span>|<span data-ttu-id="6f27b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f27b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6f27b-114">`EnumTypeRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6f27b-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6f27b-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="6f27b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6f27b-116">Bu durumda `pcTypeRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="6f27b-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f27b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f27b-117">Remarks</span></span>  
 <span data-ttu-id="6f27b-118">TypeRef belirteci bir türe başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6f27b-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f27b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f27b-119">Requirements</span></span>  
 <span data-ttu-id="6f27b-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f27b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f27b-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6f27b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f27b-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6f27b-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f27b-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f27b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f27b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f27b-124">See also</span></span>

- [<span data-ttu-id="6f27b-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f27b-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6f27b-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f27b-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
