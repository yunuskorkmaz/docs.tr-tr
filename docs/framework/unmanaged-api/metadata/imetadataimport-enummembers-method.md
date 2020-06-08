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
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492065"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="353ff-102">IMetaDataImport::EnumMembers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="353ff-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="353ff-103">Belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="353ff-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353ff-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="353ff-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="353ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="353ff-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="353ff-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="353ff-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="353ff-107">'ndaki Üyeleri numaralandırılmış olan türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="353ff-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="353ff-108">dışı MemberDef belirteçlerini tutmak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="353ff-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="353ff-109">'ndaki Dizinin en büyük boyutu `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="353ff-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="353ff-110">dışı İçinde döndürülen MemberDef belirteçlerinin gerçek sayısı `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="353ff-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="353ff-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="353ff-111">Return Value</span></span>  
  
|<span data-ttu-id="353ff-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="353ff-112">HRESULT</span></span>|<span data-ttu-id="353ff-113">Description</span><span class="sxs-lookup"><span data-stu-id="353ff-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="353ff-114">`EnumMembers`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="353ff-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="353ff-115">Numaralandırılacak MemberDef belirteçleri yok.</span><span class="sxs-lookup"><span data-stu-id="353ff-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="353ff-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="353ff-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="353ff-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="353ff-117">Remarks</span></span>  
 <span data-ttu-id="353ff-118">Bir sınıf için üye koleksiyonları numaralandırılırken, `EnumMembers` doğrudan sınıfında tanımlanmış üyeleri (alanlar ve Yöntemler, ancak Özellikler veya olaylar **değil** ) döndürür.</span><span class="sxs-lookup"><span data-stu-id="353ff-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="353ff-119">Sınıf, devralınan Üyeler için bir uygulama sağladığından bile, sınıfın devraldığı herhangi bir üye döndürmez.</span><span class="sxs-lookup"><span data-stu-id="353ff-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="353ff-120">Devralınan üyeleri listelemek için çağıran, devralma zincirini açıkça yürümelidir.</span><span class="sxs-lookup"><span data-stu-id="353ff-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="353ff-121">Devralma zincirinin kurallarının, özgün meta verileri oluşturan dile veya derleyiciye göre değişebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="353ff-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="353ff-122">Özellikler ve olaylar tarafından numaralandırılmıyor `EnumMembers` .</span><span class="sxs-lookup"><span data-stu-id="353ff-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="353ff-123">Bunları listelemek için, [EnumProperties](imetadataimport-enumproperties-method.md) veya [trmevents](imetadataimport-enumevents-method.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="353ff-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="353ff-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="353ff-124">Requirements</span></span>  
 <span data-ttu-id="353ff-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="353ff-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353ff-126">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="353ff-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="353ff-127">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="353ff-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="353ff-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353ff-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353ff-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="353ff-129">See also</span></span>

- [<span data-ttu-id="353ff-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="353ff-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="353ff-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="353ff-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
