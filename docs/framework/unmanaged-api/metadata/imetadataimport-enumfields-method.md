---
title: IMetaDataImport::EnumFields Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: be2845d1d660d86447cfbb6f2845a8e68b727e66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175518"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="db3e0-102">IMetaDataImport::EnumFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db3e0-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="db3e0-103">Belirtilen TypeDef belirteci tarafından başvurulan tür için FieldDef belirteçleri sayısalleştirir.</span><span class="sxs-lookup"><span data-stu-id="db3e0-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db3e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db3e0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db3e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db3e0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="db3e0-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="db3e0-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="db3e0-107">[içinde] Alanları numaralandırılacak sınıfın TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="db3e0-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="db3e0-108">[çıkış] FieldDef belirteçleri listesi.</span><span class="sxs-lookup"><span data-stu-id="db3e0-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="db3e0-109">[içinde] `rFields` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="db3e0-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="db3e0-110">[çıkış] FieldDef belirteçlerinin gerçek sayısı `rFields`.</span><span class="sxs-lookup"><span data-stu-id="db3e0-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db3e0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="db3e0-111">Return Value</span></span>  
  
|<span data-ttu-id="db3e0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db3e0-112">HRESULT</span></span>|<span data-ttu-id="db3e0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db3e0-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="db3e0-114">`EnumFields`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="db3e0-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="db3e0-115">Sayısalolarak sayısala erdirecek alan yok.</span><span class="sxs-lookup"><span data-stu-id="db3e0-115">There are no fields to enumerate.</span></span> <span data-ttu-id="db3e0-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="db3e0-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db3e0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db3e0-117">Requirements</span></span>  
 <span data-ttu-id="db3e0-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db3e0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db3e0-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db3e0-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db3e0-120">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="db3e0-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db3e0-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db3e0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db3e0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db3e0-122">See also</span></span>

- [<span data-ttu-id="db3e0-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db3e0-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="db3e0-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db3e0-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
