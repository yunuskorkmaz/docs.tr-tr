---
title: IMetaDataImport::EnumMembers Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8d871f2ecbd96d5bda781b2ae11b94efd409442
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128407"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="89893-102">IMetaDataImport::EnumMembers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89893-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="89893-103">Belirtilen türün üyelerini temsil eden MemberDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="89893-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89893-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89893-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89893-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89893-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="89893-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="89893-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="89893-107">[in] Numaralandırılacak üyeleri olan türü temsil eden bir tür tanımı belirteci.</span><span class="sxs-lookup"><span data-stu-id="89893-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="89893-108">[out] Dizi MemberDef belirteçleri tutmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89893-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="89893-109">[in] En büyük boyutunu `rMembers` dizisi.</span><span class="sxs-lookup"><span data-stu-id="89893-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="89893-110">[out] Döndürülen MemberDef belirteçleri gerçek sayısını `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="89893-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89893-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89893-111">Return Value</span></span>  
  
|<span data-ttu-id="89893-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89893-112">HRESULT</span></span>|<span data-ttu-id="89893-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89893-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="89893-114">`EnumMembers` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="89893-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="89893-115">Numaralandırılacak hiçbir MemberDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="89893-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="89893-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="89893-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89893-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89893-117">Remarks</span></span>  
 <span data-ttu-id="89893-118">Koleksiyonlar bir sınıfın üyelerinin sıralanırken `EnumMembers` yalnızca üyeleri döndürür (alanlar ve yöntemler, ancak **değil** özellikleri veya olayları) doğrudan sınıf üzerinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="89893-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="89893-119">Bile sınıfı, bu devralınan üyeleri için bir uygulama sağlar sınıfını devralan herhangi bir üye döndürmez.</span><span class="sxs-lookup"><span data-stu-id="89893-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="89893-120">Devralınan üyeleri listeleme için arayan açıkça devralma zincirini yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="89893-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="89893-121">Devralma zincirini kurallarını özgün metaverileri gereğince yayılan derleyici ve dil bağlı olarak farklılık gösterebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="89893-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="89893-122">Özellikler ve olaylar değil numaralandırılan tarafından `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="89893-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="89893-123">Bu listeleme için kullanın [EnumProperties](imetadataimport-enumproperties-method.md) veya [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="89893-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="89893-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89893-124">Requirements</span></span>  
 <span data-ttu-id="89893-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89893-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89893-126">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="89893-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89893-127">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="89893-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89893-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89893-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89893-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89893-129">See also</span></span>

- [<span data-ttu-id="89893-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89893-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="89893-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89893-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
