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
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177313"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="3038d-102">IMetaDataImport::EnumMembersWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3038d-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="3038d-103">Belirtilen türdeki üyeleri temsil eden ÜyeDef belirteçlerini belirtilen adla oyalar.</span><span class="sxs-lookup"><span data-stu-id="3038d-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3038d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3038d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3038d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3038d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3038d-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3038d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="3038d-107">[içinde] Üyelerini sayısala dizecek türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="3038d-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="3038d-108">[içinde] Üyenin kapsamını sınırlayan üye adı.</span><span class="sxs-lookup"><span data-stu-id="3038d-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="3038d-109">[çıkış] ÜyeDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="3038d-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3038d-110">[içinde] `rMembers` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="3038d-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3038d-111">[çıkış] ÜyeDef belirteçlerinin gerçek sayısı `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="3038d-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3038d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3038d-112">Remarks</span></span>  
 <span data-ttu-id="3038d-113">Bu yöntem alanları ve yöntemleri, ancak özellikleri veya olayları sayısallar.</span><span class="sxs-lookup"><span data-stu-id="3038d-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="3038d-114">[IMetaDataImport aksine::EnumMembers,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md) `EnumMembersWithName` belirtilen adı olmayan tüm alan ve üye belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="3038d-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3038d-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3038d-115">Return Value</span></span>  
  
|<span data-ttu-id="3038d-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3038d-116">HRESULT</span></span>|<span data-ttu-id="3038d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3038d-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3038d-118">`EnumTypeDefs`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3038d-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3038d-119">Sayısala kaydolacak ÜyeDef belirteçleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="3038d-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="3038d-120">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3038d-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3038d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3038d-121">Requirements</span></span>  
 <span data-ttu-id="3038d-122">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3038d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3038d-123">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3038d-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3038d-124">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="3038d-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3038d-125">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3038d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3038d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3038d-126">See also</span></span>

- [<span data-ttu-id="3038d-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3038d-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3038d-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3038d-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
