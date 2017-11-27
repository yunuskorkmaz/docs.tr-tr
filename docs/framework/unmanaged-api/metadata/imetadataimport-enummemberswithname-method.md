---
title: "IMetaDataImport::EnumMembersWithName Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembersWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64568fb185cd8a18e43639568ecb67fcfa350dba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="05327-102">IMetaDataImport::EnumMembersWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05327-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="05327-103">Belirtilen ada sahip belirtilen türün üyeleri temsil eden MemberDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="05327-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05327-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05327-104">Syntax</span></span>  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05327-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05327-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="05327-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05327-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="05327-107">[in] Üyeleri listeleme türüyle temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="05327-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="05327-108">[in] Numaralayıcı kapsamını sınırlar üye adı.</span><span class="sxs-lookup"><span data-stu-id="05327-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="05327-109">[out] MemberDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="05327-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="05327-110">[in] En büyük boyutunu `rMembers` dizi.</span><span class="sxs-lookup"><span data-stu-id="05327-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="05327-111">[out] Döndürülen MemberDef belirteçleri gerçek sayısını `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="05327-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05327-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05327-112">Remarks</span></span>  
 <span data-ttu-id="05327-113">Bu yöntem, alanları ve yöntemleri, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="05327-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="05327-114">Farklı [Imetadataımport::enummembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` belirtilen ada sahip olmayan tüm alan ve üye belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="05327-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05327-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05327-115">Return Value</span></span>  
  
|<span data-ttu-id="05327-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05327-116">HRESULT</span></span>|<span data-ttu-id="05327-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05327-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="05327-118">`EnumTypeDefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="05327-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="05327-119">Numaralandırılacak hiçbir MemberDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="05327-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="05327-120">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="05327-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05327-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05327-121">Requirements</span></span>  
 <span data-ttu-id="05327-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05327-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05327-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05327-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05327-124">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="05327-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05327-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05327-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05327-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05327-126">See Also</span></span>  
 [<span data-ttu-id="05327-127">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="05327-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="05327-128">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="05327-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
