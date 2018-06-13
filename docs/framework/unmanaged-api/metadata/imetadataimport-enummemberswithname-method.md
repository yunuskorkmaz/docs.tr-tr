---
title: IMetaDataImport::EnumMembersWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5fca698adc4d08d805fec2ff80af377366674b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445961"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="9f107-102">IMetaDataImport::EnumMembersWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f107-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="9f107-103">Belirtilen ada sahip belirtilen türün üyeleri temsil eden MemberDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="9f107-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f107-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f107-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9f107-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f107-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9f107-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f107-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="9f107-107">[in] Üyeleri listeleme türüyle temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="9f107-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="9f107-108">[in] Numaralayıcı kapsamını sınırlar üye adı.</span><span class="sxs-lookup"><span data-stu-id="9f107-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="9f107-109">[out] MemberDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="9f107-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9f107-110">[in] En büyük boyutunu `rMembers` dizi.</span><span class="sxs-lookup"><span data-stu-id="9f107-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9f107-111">[out] Döndürülen MemberDef belirteçleri gerçek sayısını `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="9f107-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f107-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f107-112">Remarks</span></span>  
 <span data-ttu-id="9f107-113">Bu yöntem, alanları ve yöntemleri, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="9f107-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="9f107-114">Farklı [Imetadataımport::enummembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` belirtilen ada sahip olmayan tüm alan ve üye belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="9f107-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f107-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9f107-115">Return Value</span></span>  
  
|<span data-ttu-id="9f107-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f107-116">HRESULT</span></span>|<span data-ttu-id="9f107-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f107-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9f107-118">`EnumTypeDefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9f107-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9f107-119">Numaralandırılacak hiçbir MemberDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="9f107-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="9f107-120">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="9f107-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9f107-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f107-121">Requirements</span></span>  
 <span data-ttu-id="9f107-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f107-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f107-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f107-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f107-124">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9f107-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f107-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f107-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f107-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f107-126">See Also</span></span>  
 [<span data-ttu-id="9f107-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f107-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9f107-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f107-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
