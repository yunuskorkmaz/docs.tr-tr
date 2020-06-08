---
title: IMetaDataImport::FindMember Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503685"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="b47e6-102">IMetaDataImport::FindMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b47e6-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="b47e6-103">Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan alan veya yöntem Için MemberDef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b47e6-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47e6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b47e6-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b47e6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b47e6-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b47e6-106">'ndaki Aranacak üyeyi kapsayan sınıf veya arabirim için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="b47e6-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="b47e6-107">Bu değer ise `mdTokenNil` , arama genel değişken veya genel işlev için yapılır.</span><span class="sxs-lookup"><span data-stu-id="b47e6-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b47e6-108">'ndaki Aranacak üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="b47e6-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b47e6-109">'ndaki Üyenin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b47e6-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b47e6-110">'ndaki Bayt cinsinden boyut `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="b47e6-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b47e6-111">dışı Eşleşen MemberDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b47e6-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b47e6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b47e6-112">Remarks</span></span>  
 <span data-ttu-id="b47e6-113">Üyeyi kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="b47e6-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="b47e6-114">Bir sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="b47e6-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="b47e6-115">Bu durumda, benzersiz eşleşmeyi bulmak için üyenin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="b47e6-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="b47e6-116">`FindMember`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b47e6-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b47e6-117">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b47e6-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b47e6-118">Belirteç, yerel TypeDef tablosunun bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="b47e6-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="b47e6-119">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı girişi yapılacak girdi olarak kullanabilirsiniz `FindMember` .</span><span class="sxs-lookup"><span data-stu-id="b47e6-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="b47e6-120">`FindMember`yalnızca sınıfta veya arabirimde doğrudan tanımlanmış olan üyeleri bulur; devralınan üyeleri bulamaz.</span><span class="sxs-lookup"><span data-stu-id="b47e6-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b47e6-121">`FindMember`bir yardımcı yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="b47e6-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="b47e6-122">[IMetaDataImport:: FindMethod](imetadataimport-findmethod-method.md); öğesini çağırır Bu çağrı bir eşleşme bulamazsa, `FindMember` [IMetaDataImport:: FindField](imetadataimport-findfield-method.md)' ı çağırır.</span><span class="sxs-lookup"><span data-stu-id="b47e6-122">It calls [IMetaDataImport::FindMethod](imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b47e6-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b47e6-123">Requirements</span></span>  
 <span data-ttu-id="b47e6-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b47e6-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b47e6-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b47e6-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b47e6-126">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b47e6-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b47e6-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b47e6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47e6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b47e6-128">See also</span></span>

- [<span data-ttu-id="b47e6-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b47e6-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b47e6-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b47e6-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
