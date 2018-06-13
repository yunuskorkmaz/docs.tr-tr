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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ed8bbbd9699fe707d638bb8d07064e508b6f2fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447778"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="e39a8-102">IMetaDataImport::EnumFieldsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e39a8-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="e39a8-103">Belirtilen ada sahip belirtilen türde fieldDef simgesi belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e39a8-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e39a8-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e39a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e39a8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e39a8-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e39a8-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="e39a8-107">[in] Numaralandırılacak alanları olan tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="e39a8-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="e39a8-108">[in] Numaralandırma kapsamını sınırlar alanın adı.</span><span class="sxs-lookup"><span data-stu-id="e39a8-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="e39a8-109">[out] Dizi fieldDef simgesi belirteçleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e39a8-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e39a8-110">[in] En büyük boyutunu `rFields` dizi.</span><span class="sxs-lookup"><span data-stu-id="e39a8-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e39a8-111">[out] Döndürülen fieldDef simgesi belirteçleri gerçek sayısını `rFields`.</span><span class="sxs-lookup"><span data-stu-id="e39a8-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e39a8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e39a8-112">Remarks</span></span>  
 <span data-ttu-id="e39a8-113">Farklı [Imetadataımport::enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` belirtilen ada sahip olmayan tüm alan belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="e39a8-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e39a8-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e39a8-114">Return Value</span></span>  
  
|<span data-ttu-id="e39a8-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e39a8-115">HRESULT</span></span>|<span data-ttu-id="e39a8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e39a8-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e39a8-117">`EnumFieldsWithName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e39a8-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e39a8-118">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="e39a8-118">There are no fields to enumerate.</span></span> <span data-ttu-id="e39a8-119">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e39a8-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e39a8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e39a8-120">Requirements</span></span>  
 <span data-ttu-id="e39a8-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e39a8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e39a8-122">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e39a8-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e39a8-123">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e39a8-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e39a8-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e39a8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39a8-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e39a8-125">See Also</span></span>  
 [<span data-ttu-id="e39a8-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e39a8-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e39a8-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e39a8-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
