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
ms.openlocfilehash: 79c9a54a44ae1751cb8b1b57379ccfd6485f6e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448197"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="38160-102">IMetaDataImport::FindMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38160-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="38160-103">Bir işaretçi MemberDef alan veya içine yöntemi için belirteç alır belirtilen tarafından <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="38160-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38160-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38160-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38160-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38160-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="38160-106">[in] Sınıf veya aramak için üye barındırır arabirimi için TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="38160-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="38160-107">Bu değer ise `mdTokenNil`, bir genel değişkeni veya genel işlevi için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="38160-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="38160-108">[in] Aranacak üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="38160-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="38160-109">[in] Üyenin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38160-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="38160-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="38160-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="38160-111">[out] Eşleşen MemberDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38160-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38160-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38160-112">Remarks</span></span>  
 <span data-ttu-id="38160-113">Kapsayan sınıf ya da arabirimi kullanarak üyesi belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="38160-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="38160-114">Bir sınıf ya da arabirimi aynı ada sahip birden çok üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="38160-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="38160-115">Bu durumda, benzersiz bir eşleşme bulmak için üyenin imza geçirin.</span><span class="sxs-lookup"><span data-stu-id="38160-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="38160-116">İmza geçirilen `FindMember` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38160-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="38160-117">İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="38160-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="38160-118">Belirteç yerel TypeDef tabloya dizinidir.</span><span class="sxs-lookup"><span data-stu-id="38160-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="38160-119">Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve bu imza olarak giriş için giriş kullanmasına `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="38160-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="38160-120">`FindMember` doğrudan sınıfta veya arabirimde tanımlanan üyelerini bulur; devralınan üyeleri bulmaz.</span><span class="sxs-lookup"><span data-stu-id="38160-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38160-121">`FindMember` bir yardımcı yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="38160-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="38160-122">Çağırır [Imetadataımport::findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); bu çağrı bir eşleşme bulamazsa `FindMember` sonra çağırır [Imetadataımport::findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="38160-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38160-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38160-123">Requirements</span></span>  
 <span data-ttu-id="38160-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38160-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38160-125">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38160-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38160-126">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="38160-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38160-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38160-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38160-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38160-128">See Also</span></span>  
 [<span data-ttu-id="38160-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38160-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="38160-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38160-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
