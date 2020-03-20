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
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177276"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="83125-102">IMetaDataImport::FindMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83125-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="83125-103">Belirtilen <xref:System.Type> ad ve meta veri imzasına sahip alan veya yöntem için ÜyeDef belirteci için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="83125-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83125-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83125-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83125-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83125-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="83125-106">[içinde] Üyenin aranması gereken sınıf veya arabirim için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="83125-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="83125-107">Bu değer `mdTokenNil`ise, arama genel değişken veya genel işlev için yapılır.</span><span class="sxs-lookup"><span data-stu-id="83125-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="83125-108">[içinde] Aranacak üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="83125-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="83125-109">[içinde] Üyenin ikili meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83125-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="83125-110">[içinde] `pvSigBlob`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="83125-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="83125-111">[çıkış] Eşleşen ÜyeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83125-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83125-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83125-112">Remarks</span></span>  
 <span data-ttu-id="83125-113">Üyeyi çevreleyen sınıfını veya arayüzünü`td`( ),`szName`adını ( ),`pvSigBlob`ve isteğe bağlı olarak imzasını ( ) kullanarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83125-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="83125-114">Bir sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="83125-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="83125-115">Bu durumda, benzersiz eşleşmeyi bulmak için üyenin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="83125-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="83125-116">İmzalar belirli `FindMember` bir kapsama bağlı olduğundan, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83125-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="83125-117">İmza, çevreleyen sınıfı veya değer türünü tanımlayan bir belirteç katıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="83125-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="83125-118">Belirteç, yerel TypeDef tablosuna bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="83125-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="83125-119">Geçerli kapsam bağlamının dışında bir çalışma zamanı imzası oluşturamazsınız ve bu imzayı `FindMember`giriş olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="83125-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="83125-120">`FindMember`yalnızca doğrudan sınıf veya arabirimde tanımlanmış üyeleri bulur; devralınan üyeleri bulamaz.</span><span class="sxs-lookup"><span data-stu-id="83125-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83125-121">`FindMember`yardımcı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="83125-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="83125-122">Bu [iMetaDataImport çağırır::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); bu arama eşleşme bulamazsa, `FindMember` o zaman [iMetaDataImport çağırır::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="83125-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83125-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83125-123">Requirements</span></span>  
 <span data-ttu-id="83125-124">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83125-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83125-125">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83125-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83125-126">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="83125-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83125-127">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83125-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83125-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83125-128">See also</span></span>

- [<span data-ttu-id="83125-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83125-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="83125-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83125-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
