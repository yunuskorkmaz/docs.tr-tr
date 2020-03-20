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
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175492"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="d2c3c-102">IMetaDataImport::EnumMembers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2c3c-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="d2c3c-103">Belirtilen tipteki üyeleri temsil eden ÜyeDef belirteçlerini oyalar.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c3c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2c3c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2c3c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2c3c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d2c3c-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="d2c3c-107">[içinde] Üyeleri numaralandırılacak türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="d2c3c-108">[çıkış] ÜyeDef belirteçlerini tutmak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d2c3c-109">[içinde] `rMembers` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d2c3c-110">[çıkış] ÜyeDef belirteçlerinin gerçek sayısı `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2c3c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d2c3c-111">Return Value</span></span>  
  
|<span data-ttu-id="d2c3c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2c3c-112">HRESULT</span></span>|<span data-ttu-id="d2c3c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2c3c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d2c3c-114">`EnumMembers`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d2c3c-115">Sayısala kaydolacak ÜyeDef belirteçleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="d2c3c-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2c3c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2c3c-117">Remarks</span></span>  
 <span data-ttu-id="d2c3c-118">Bir sınıf için üye koleksiyonlarını toplarken, `EnumMembers` yalnızca üyeler (alanlar ve yöntemler, ancak özellikler veya olaylar) doğrudan sınıf üzerinde tanımlanan döndürür. **not**</span><span class="sxs-lookup"><span data-stu-id="d2c3c-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="d2c3c-119">Sınıf, devralınan üyeler için bir uygulama sağlasa bile, sınıfın devraldığı hiçbir üyeyi döndürmez.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="d2c3c-120">Devralınan üyeleri doğrulamak için, arayan açıkça devralma zincirinde yürümelidir.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="d2c3c-121">Devralma zincirinin kurallarının, özgün meta verileri yayan dile veya derleyiciye bağlı olarak değişebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="d2c3c-122">Özellikler ve olaylar `EnumMembers`tarafından numaralandırılmez.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="d2c3c-123">Bunları sayısallandırmak için [EnumProperties](imetadataimport-enumproperties-method.md) veya [EnumEvents'i](imetadataimport-enumevents-method.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d2c3c-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2c3c-124">Requirements</span></span>  
 <span data-ttu-id="d2c3c-125">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2c3c-126">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d2c3c-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2c3c-127">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="d2c3c-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2c3c-128">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2c3c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c3c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-129">See also</span></span>

- [<span data-ttu-id="d2c3c-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2c3c-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d2c3c-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2c3c-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
