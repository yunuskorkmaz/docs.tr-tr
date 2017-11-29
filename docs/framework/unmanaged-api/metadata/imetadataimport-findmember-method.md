---
title: "IMetaDataImport::FindMember Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a47060575d14e1206e715ea2bfd2ea750bd49c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="01e28-102">IMetaDataImport::FindMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01e28-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="01e28-103">Bir işaretçi MemberDef alan veya içine yöntemi için belirteç alır belirtilen tarafından <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="01e28-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01e28-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01e28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01e28-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="01e28-106">[in] Sınıf veya aramak için üye barındırır arabirimi için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="01e28-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="01e28-107">Bu değer ise `mdTokenNil`, bir genel değişkeni veya genel işlevi için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="01e28-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="01e28-108">[in] Aranacak üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="01e28-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="01e28-109">[in] Üyenin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01e28-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="01e28-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="01e28-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="01e28-111">[out] Eşleşen MemberDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01e28-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01e28-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01e28-112">Remarks</span></span>  
 <span data-ttu-id="01e28-113">Kapsayan sınıf ya da arabirimi kullanarak üyesi belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="01e28-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="01e28-114">Bir sınıf ya da arabirimi aynı ada sahip birden çok üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="01e28-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="01e28-115">Bu durumda, benzersiz bir eşleşme bulmak için üyenin imza geçirin.</span><span class="sxs-lookup"><span data-stu-id="01e28-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="01e28-116">İmza geçirilen `FindMember` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="01e28-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="01e28-117">İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="01e28-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="01e28-118">Belirteç yerel TypeDef tabloya dizinidir.</span><span class="sxs-lookup"><span data-stu-id="01e28-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="01e28-119">Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve bu imza olarak giriş için giriş kullanmasına `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="01e28-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="01e28-120">`FindMember`doğrudan sınıfta veya arabirimde tanımlanan üyelerini bulur; devralınan üyeleri bulmaz.</span><span class="sxs-lookup"><span data-stu-id="01e28-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01e28-121">`FindMember`bir yardımcı yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="01e28-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="01e28-122">Çağırır [Imetadataımport::findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); bu çağrı bir eşleşme bulamazsa `FindMember` sonra çağırır [Imetadataımport::findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="01e28-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e28-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01e28-123">Requirements</span></span>  
 <span data-ttu-id="01e28-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01e28-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e28-125">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01e28-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01e28-126">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="01e28-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01e28-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e28-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e28-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01e28-128">See Also</span></span>  
 [<span data-ttu-id="01e28-129">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="01e28-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="01e28-130">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="01e28-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
