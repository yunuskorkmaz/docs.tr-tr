---
title: IMetaDataImport::EnumFieldsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177348"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="263be-102">IMetaDataImport::EnumFieldsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="263be-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="263be-103">Belirtilen türdeki FieldDef belirteçlerini belirtilen adla oyuvarlar.</span><span class="sxs-lookup"><span data-stu-id="263be-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="263be-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="263be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="263be-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="263be-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="263be-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="263be-107">[içinde] Alanları numaralandırılacak türden belirteç.</span><span class="sxs-lookup"><span data-stu-id="263be-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="263be-108">[içinde] Numaralandırmanın kapsamını sınırlayan alan adı.</span><span class="sxs-lookup"><span data-stu-id="263be-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="263be-109">[çıkış] Dizi FieldDef belirteçleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="263be-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="263be-110">[içinde] `rFields` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="263be-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="263be-111">[çıkış] FieldDef belirteçlerinin gerçek sayısı `rFields`.</span><span class="sxs-lookup"><span data-stu-id="263be-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="263be-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="263be-112">Remarks</span></span>  
 <span data-ttu-id="263be-113">[IMetaDataImport::EnumFields'ın](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)aksine, `EnumFieldsWithName` belirtilen ada sahip olmayan tüm alan belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="263be-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="263be-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="263be-114">Return Value</span></span>  
  
|<span data-ttu-id="263be-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="263be-115">HRESULT</span></span>|<span data-ttu-id="263be-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="263be-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="263be-117">`EnumFieldsWithName`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="263be-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="263be-118">Sayısalolarak sayısala erdirecek alan yok.</span><span class="sxs-lookup"><span data-stu-id="263be-118">There are no fields to enumerate.</span></span> <span data-ttu-id="263be-119">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="263be-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="263be-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="263be-120">Requirements</span></span>  
 <span data-ttu-id="263be-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="263be-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263be-122">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="263be-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="263be-123">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="263be-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="263be-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263be-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263be-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="263be-125">See also</span></span>

- [<span data-ttu-id="263be-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="263be-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="263be-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="263be-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
