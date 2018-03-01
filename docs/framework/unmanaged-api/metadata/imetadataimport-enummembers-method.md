---
title: "IMetaDataImport::EnumMembers Yöntemi"
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
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa7dabad0e555fe965cba4e5cbc69c10c9826b8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="ef224-102">IMetaDataImport::EnumMembers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef224-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="ef224-103">Belirtilen türün üyeleri temsil eden MemberDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ef224-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef224-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef224-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef224-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef224-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ef224-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ef224-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="ef224-107">[in] Numaralandırılacak üyeleri olan türünü temsil eden bir TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="ef224-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="ef224-108">[out] MemberDef belirteçleri tutmak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="ef224-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ef224-109">[in] En büyük boyutunu `rMembers` dizi.</span><span class="sxs-lookup"><span data-stu-id="ef224-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ef224-110">[out] Döndürülen MemberDef belirteçleri gerçek sayısını `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="ef224-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef224-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ef224-111">Return Value</span></span>  
  
|<span data-ttu-id="ef224-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef224-112">HRESULT</span></span>|<span data-ttu-id="ef224-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef224-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ef224-114">`EnumMembers`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ef224-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ef224-115">Numaralandırılacak hiçbir MemberDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="ef224-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="ef224-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="ef224-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef224-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef224-117">Remarks</span></span>  
 <span data-ttu-id="ef224-118">Koleksiyonlar için bir sınıf üyeleri numaralandırılırken `EnumMembers` yalnızca doğrudan sınıfında tanımlanan üyeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef224-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="ef224-119">Sınıfı, bu devralınan üyeler için bir uygulama sağlar olsa bile sınıfının devraldığı, herhangi bir üye döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ef224-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="ef224-120">Devralınan üyeleri Numaralandırılacak çağıran açıkça devralma zincirini yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef224-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="ef224-121">Devralma zincirini kurallarını orijinal meta verileri yayılan derleyici ve dil bağlı olarak değişebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ef224-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef224-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef224-122">Requirements</span></span>  
 <span data-ttu-id="ef224-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef224-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef224-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ef224-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef224-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ef224-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef224-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef224-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef224-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef224-127">See Also</span></span>  
 [<span data-ttu-id="ef224-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef224-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ef224-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef224-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
