---
description: ': IMetaDataImport:: EnumTypeRefs yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1155357e82c08660a852225f0b1a54629cbee0ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670638"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="2e0c5-103">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e0c5-103">IMetaDataImport::EnumTypeRefs Method</span></span>

<span data-ttu-id="2e0c5-104">Geçerli meta veri kapsamında tanımlanan TypeRef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-104">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0c5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e0c5-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e0c5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e0c5-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="2e0c5-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2e0c5-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-108">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="2e0c5-109">dışı TypeRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-109">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2e0c5-110">'ndaki Dizinin en büyük boyutu `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="2e0c5-110">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="2e0c5-111">dışı İçinde döndürülen TypeRef belirteçleri sayısına yönelik bir işaretçi `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="2e0c5-111">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e0c5-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e0c5-112">Return Value</span></span>  
  
|<span data-ttu-id="2e0c5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e0c5-113">HRESULT</span></span>|<span data-ttu-id="2e0c5-114">Description</span><span class="sxs-lookup"><span data-stu-id="2e0c5-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2e0c5-115">`EnumTypeRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-115">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2e0c5-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="2e0c5-117">Bu durumda, `pcTypeRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-117">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e0c5-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e0c5-118">Remarks</span></span>  

 <span data-ttu-id="2e0c5-119">TypeRef belirteci bir türe başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-119">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e0c5-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e0c5-120">Requirements</span></span>  

 <span data-ttu-id="2e0c5-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e0c5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e0c5-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2e0c5-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e0c5-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2e0c5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e0c5-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e0c5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e0c5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e0c5-125">See also</span></span>

- [<span data-ttu-id="2e0c5-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e0c5-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2e0c5-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e0c5-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
