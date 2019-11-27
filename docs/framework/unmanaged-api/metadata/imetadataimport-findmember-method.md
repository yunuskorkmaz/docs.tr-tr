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
ms.openlocfilehash: 7a46fa5319a1badc0cf28dcdbf535a6ed017c9c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437920"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="88e26-102">IMetaDataImport::FindMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88e26-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="88e26-103">Belirtilen <xref:System.Type> alınmış ve belirtilen ad ve meta veri imzasına sahip olan alan veya yöntem için MemberDef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="88e26-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88e26-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88e26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88e26-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="88e26-106">'ndaki Aranacak üyeyi kapsayan sınıf veya arabirim için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="88e26-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="88e26-107">Bu değer `mdTokenNil`ise, arama genel değişken veya genel işlev için yapılır.</span><span class="sxs-lookup"><span data-stu-id="88e26-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="88e26-108">'ndaki Aranacak üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="88e26-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="88e26-109">'ndaki Üyenin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88e26-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="88e26-110">'ndaki `pvSigBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="88e26-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="88e26-111">dışı Eşleşen MemberDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88e26-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88e26-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88e26-112">Remarks</span></span>  
 <span data-ttu-id="88e26-113">Üyeyi kapsayan sınıfını veya arabirimini (`td`), adını (`szName`) ve isteğe bağlı olarak imzasını (`pvSigBlob`) kullanarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88e26-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="88e26-114">Bir sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="88e26-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="88e26-115">Bu durumda, benzersiz eşleşmeyi bulmak için üyenin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="88e26-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="88e26-116">İmzaların belirli bir kapsama bağlandığı için `FindMember` geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88e26-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="88e26-117">İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="88e26-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="88e26-118">Belirteç, yerel TypeDef tablosunun bir dizinidir.</span><span class="sxs-lookup"><span data-stu-id="88e26-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="88e26-119">Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı `FindMember`giriş olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88e26-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="88e26-120">`FindMember` yalnızca doğrudan sınıfta veya arabirimde tanımlanmış olan üyeleri bulur; devralınan üyeleri bulamaz.</span><span class="sxs-lookup"><span data-stu-id="88e26-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88e26-121">`FindMember` bir yardımcı yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="88e26-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="88e26-122">[IMetaDataImport:: FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); öğesini çağırır Bu çağrı bir eşleşme bulamazsa, `FindMember` sonra [IMetaDataImport:: FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)' ı çağırır.</span><span class="sxs-lookup"><span data-stu-id="88e26-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88e26-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88e26-123">Requirements</span></span>  
 <span data-ttu-id="88e26-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88e26-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88e26-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="88e26-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88e26-126">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="88e26-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88e26-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88e26-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e26-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88e26-128">See also</span></span>

- [<span data-ttu-id="88e26-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88e26-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="88e26-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88e26-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
