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
ms.openlocfilehash: 0c7e96c50e59902cde4686f908047a86dd2b6a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503750"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="3304a-102">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3304a-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="3304a-103">Geçerli meta veri kapsamında tanımlanan TypeRef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3304a-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3304a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3304a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3304a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3304a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3304a-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3304a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3304a-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3304a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="3304a-108">dışı TypeRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="3304a-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3304a-109">'ndaki Dizinin en büyük boyutu `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="3304a-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="3304a-110">dışı İçinde döndürülen TypeRef belirteçleri sayısına yönelik bir işaretçi `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="3304a-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3304a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3304a-111">Return Value</span></span>  
  
|<span data-ttu-id="3304a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3304a-112">HRESULT</span></span>|<span data-ttu-id="3304a-113">Description</span><span class="sxs-lookup"><span data-stu-id="3304a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3304a-114">`EnumTypeRefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3304a-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3304a-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="3304a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3304a-116">Bu durumda, `pcTypeRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3304a-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3304a-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3304a-117">Remarks</span></span>  
 <span data-ttu-id="3304a-118">TypeRef belirteci bir türe başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3304a-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3304a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3304a-119">Requirements</span></span>  
 <span data-ttu-id="3304a-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3304a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3304a-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3304a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3304a-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3304a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3304a-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3304a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3304a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3304a-124">See also</span></span>

- [<span data-ttu-id="3304a-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3304a-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3304a-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3304a-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
