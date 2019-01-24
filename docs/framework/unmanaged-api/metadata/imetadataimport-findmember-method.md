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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 267a36fbbdf48472bc35581ce98af5cd7a9cef9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550376"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="3824b-102">IMetaDataImport::FindMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3824b-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="3824b-103">Bir işaretçi için MemberDef alan veya alınmış yöntemi için belirteç alır tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="3824b-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3824b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3824b-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3824b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3824b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3824b-106">[in] Sınıf veya üye aranacak kapsayan arabirimi TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="3824b-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="3824b-107">Bu değer ise `mdTokenNil`, bir genel değişken veya işlev genel arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="3824b-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="3824b-108">[in] Aranacak üyesinin adı.</span><span class="sxs-lookup"><span data-stu-id="3824b-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3824b-109">[in] İkili meta veri imzası üyenin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3824b-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3824b-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3824b-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="3824b-111">[out] Eşleşen MemberDef belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3824b-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3824b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3824b-112">Remarks</span></span>  
 <span data-ttu-id="3824b-113">Kapsayan sınıfı veya arabirimi kullanılarak üyesi belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="3824b-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="3824b-114">Sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="3824b-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="3824b-115">Bu durumda, benzersiz bir eşleşme bulmak için üyenin imzasını geçirin.</span><span class="sxs-lookup"><span data-stu-id="3824b-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="3824b-116">İmza geçirilen `FindMember` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="3824b-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="3824b-117">İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3824b-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="3824b-118">Belirteç, yerel TypeDef tablosuna bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="3824b-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="3824b-119">Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza olarak giriş için giriş kullanmasına `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="3824b-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="3824b-120">`FindMember` sınıf veya arabirim içinde tanımlanmış üyeler bulur; devralınan üyeleri bulmaz.</span><span class="sxs-lookup"><span data-stu-id="3824b-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3824b-121">`FindMember` bir yardımcı yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="3824b-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="3824b-122">Çağrı [Imetadataımport::findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); bu çağrı bir eşleşme bulamazsa `FindMember` sonra çağıran [Imetadataımport::findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="3824b-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3824b-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3824b-123">Requirements</span></span>  
 <span data-ttu-id="3824b-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3824b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3824b-125">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3824b-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3824b-126">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3824b-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3824b-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3824b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3824b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3824b-128">See also</span></span>
- [<span data-ttu-id="3824b-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3824b-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3824b-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3824b-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
