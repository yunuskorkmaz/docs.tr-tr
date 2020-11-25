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
ms.openlocfilehash: 92503df60ae44dfd44819fe3eda8e6a0549b2b66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721001"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="8e00c-102">IMetaDataImport::EnumMembers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e00c-102">IMetaDataImport::EnumMembers Method</span></span>

<span data-ttu-id="8e00c-103">Belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8e00c-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e00c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8e00c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e00c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e00c-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="8e00c-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8e00c-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="8e00c-107">'ndaki Üyeleri numaralandırılmış olan türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="8e00c-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="8e00c-108">dışı MemberDef belirteçlerini tutmak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="8e00c-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8e00c-109">'ndaki Dizinin en büyük boyutu `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="8e00c-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8e00c-110">dışı İçinde döndürülen MemberDef belirteçlerinin gerçek sayısı `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="8e00c-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e00c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e00c-111">Return Value</span></span>  
  
|<span data-ttu-id="8e00c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e00c-112">HRESULT</span></span>|<span data-ttu-id="8e00c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e00c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8e00c-114">`EnumMembers` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8e00c-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8e00c-115">Numaralandırılacak MemberDef belirteçleri yok.</span><span class="sxs-lookup"><span data-stu-id="8e00c-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="8e00c-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="8e00c-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e00c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e00c-117">Remarks</span></span>  

 <span data-ttu-id="8e00c-118">Bir sınıf için üye koleksiyonları numaralandırılırken, `EnumMembers` doğrudan sınıfında tanımlanmış üyeleri (alanlar ve Yöntemler, ancak Özellikler veya olaylar **değil** ) döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e00c-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="8e00c-119">Sınıf, devralınan Üyeler için bir uygulama sağladığından bile, sınıfın devraldığı herhangi bir üye döndürmez.</span><span class="sxs-lookup"><span data-stu-id="8e00c-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="8e00c-120">Devralınan üyeleri listelemek için çağıran, devralma zincirini açıkça yürümelidir.</span><span class="sxs-lookup"><span data-stu-id="8e00c-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="8e00c-121">Devralma zincirinin kurallarının, özgün meta verileri oluşturan dile veya derleyiciye göre değişebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8e00c-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="8e00c-122">Özellikler ve olaylar tarafından numaralandırılmıyor `EnumMembers` .</span><span class="sxs-lookup"><span data-stu-id="8e00c-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="8e00c-123">Bunları listelemek için, [EnumProperties](imetadataimport-enumproperties-method.md) veya [trmevents](imetadataimport-enumevents-method.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e00c-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="8e00c-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e00c-124">Requirements</span></span>  

 <span data-ttu-id="8e00c-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e00c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e00c-126">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8e00c-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e00c-127">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8e00c-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e00c-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e00c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e00c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e00c-129">See also</span></span>

- [<span data-ttu-id="8e00c-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e00c-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8e00c-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e00c-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
