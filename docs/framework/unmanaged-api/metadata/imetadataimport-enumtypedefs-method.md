---
title: IMetaDataImport::EnumTypeDefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 2d6e86a7f5a93b900e79907f8ee0762869d7f737
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177291"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="76325-102">IMetaDataImport::EnumTypeDefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76325-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="76325-103">Geçerli kapsamdaki tüm türleri temsil eden TypeDef belirteçlerini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="76325-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76325-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76325-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76325-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76325-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="76325-106">[çıkış] Yeni sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="76325-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="76325-107">Bu yöntemin ilk araması için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76325-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="76325-108">[içinde] TypeDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="76325-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="76325-109">[içinde] `rTypeDefs` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="76325-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="76325-110">[çıkış] TypeDef belirteçlerinin sayısı `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="76325-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76325-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="76325-111">Return Value</span></span>  
  
|<span data-ttu-id="76325-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76325-112">HRESULT</span></span>|<span data-ttu-id="76325-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76325-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="76325-114">`EnumTypeDefs`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="76325-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="76325-115">Sayısala rendelemek için hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="76325-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="76325-116">Bu durumda, `pcTypeDefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="76325-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76325-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76325-117">Remarks</span></span>  
 <span data-ttu-id="76325-118">TypeDef belirteci, bir sınıf veya arabirim gibi bir türü ve genişletilebilirlik mekanizması yla eklenen herhangi bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="76325-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76325-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76325-119">Requirements</span></span>  
 <span data-ttu-id="76325-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76325-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76325-121">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76325-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76325-122">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="76325-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76325-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76325-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76325-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76325-124">See also</span></span>

- [<span data-ttu-id="76325-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76325-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="76325-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76325-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
