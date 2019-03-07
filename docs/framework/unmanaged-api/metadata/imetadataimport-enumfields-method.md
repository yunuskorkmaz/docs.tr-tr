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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18cf59553468e2408f3898d8233bd05d453db17b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471972"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="7b1a6-102">IMetaDataImport::EnumFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b1a6-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="7b1a6-103">FieldDef simgesi belirteçleri için belirtilen TypeDef belirteci tarafından başvurulan türünü numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b1a6-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b1a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b1a6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7b1a6-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="7b1a6-107">[in] Numaralandırılacak alanları sınıfı TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="7b1a6-108">[out] FieldDef simgesi belirteçleri listesi.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7b1a6-109">[in] En büyük boyutunu `rFields` dizisi.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7b1a6-110">[out] Döndürülen fieldDef simgesi belirteçleri gerçek sayısını `rFields`.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b1a6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7b1a6-111">Return Value</span></span>  
  
|<span data-ttu-id="7b1a6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b1a6-112">HRESULT</span></span>|<span data-ttu-id="7b1a6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b1a6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7b1a6-114">`EnumFields` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7b1a6-115">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-115">There are no fields to enumerate.</span></span> <span data-ttu-id="7b1a6-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b1a6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b1a6-117">Requirements</span></span>  
 <span data-ttu-id="7b1a6-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b1a6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1a6-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7b1a6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b1a6-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7b1a6-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7b1a6-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b1a6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1a6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b1a6-122">See also</span></span>
- [<span data-ttu-id="7b1a6-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b1a6-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7b1a6-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b1a6-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
