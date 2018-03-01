---
title: "IMetaDataImport::EnumFieldsWithName Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77b5ba7e191d9aa0f1587e4ac1ec25e655c27b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="9abb6-102">IMetaDataImport::EnumFieldsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9abb6-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="9abb6-103">Belirtilen ada sahip belirtilen türde fieldDef simgesi belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="9abb6-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abb6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9abb6-104">Syntax</span></span>  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9abb6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9abb6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9abb6-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9abb6-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="9abb6-107">[in] Numaralandırılacak alanları olan tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="9abb6-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="9abb6-108">[in] Numaralandırma kapsamını sınırlar alanın adı.</span><span class="sxs-lookup"><span data-stu-id="9abb6-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="9abb6-109">[out] Dizi fieldDef simgesi belirteçleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9abb6-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9abb6-110">[in] En büyük boyutunu `rFields` dizi.</span><span class="sxs-lookup"><span data-stu-id="9abb6-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9abb6-111">[out] Döndürülen fieldDef simgesi belirteçleri gerçek sayısını `rFields`.</span><span class="sxs-lookup"><span data-stu-id="9abb6-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9abb6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9abb6-112">Remarks</span></span>  
 <span data-ttu-id="9abb6-113">Farklı [Imetadataımport::enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` belirtilen ada sahip olmayan tüm alan belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="9abb6-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9abb6-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9abb6-114">Return Value</span></span>  
  
|<span data-ttu-id="9abb6-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9abb6-115">HRESULT</span></span>|<span data-ttu-id="9abb6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9abb6-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9abb6-117">`EnumFieldsWithName`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9abb6-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9abb6-118">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="9abb6-118">There are no fields to enumerate.</span></span> <span data-ttu-id="9abb6-119">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="9abb6-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9abb6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9abb6-120">Requirements</span></span>  
 <span data-ttu-id="9abb6-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9abb6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9abb6-122">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9abb6-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9abb6-123">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9abb6-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9abb6-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9abb6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abb6-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9abb6-125">See Also</span></span>  
 [<span data-ttu-id="9abb6-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9abb6-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9abb6-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9abb6-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
