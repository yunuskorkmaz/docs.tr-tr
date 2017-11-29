---
title: "IMetaDataImport::FindMemberRef Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMemberRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: efb8a3a74997c6894eff6fafb87e933a6d2cf7bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="fb703-102">IMetaDataImport::FindMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb703-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="fb703-103">Üye için MemberRef belirteci için bir işaretçi başvuru diğer bir deyişle alır içine tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="fb703-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb703-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb703-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb703-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb703-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fb703-106">[in] Sınıf veya aramak için üye başvuru barındırır arabirimi için TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="fb703-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="fb703-107">Bu değer ise `mdTokenNil`, genel değişken veya işlev genel başvurusu için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="fb703-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="fb703-108">[in] Aranacak üye referansın adı.</span><span class="sxs-lookup"><span data-stu-id="fb703-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fb703-109">[in] Üye başvuru ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb703-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fb703-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fb703-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="fb703-111">[out] Eşleşen MemberRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb703-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb703-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb703-112">Remarks</span></span>  
 <span data-ttu-id="fb703-113">Kapsayan sınıf ya da arabirimi kullanarak üyesi belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="fb703-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="fb703-114">İmza geçirilen `FindMemberRef` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb703-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="fb703-115">İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fb703-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="fb703-116">Belirteç yerel TypeDef tabloya dizinidir.</span><span class="sxs-lookup"><span data-stu-id="fb703-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="fb703-117">Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve girdi olarak bu imza kullanmak `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="fb703-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="fb703-118">`FindMemberRef`doğrudan sınıfta veya arabirimde tanımlanan üye başvuruları bulur; devralınan üye başvuruları bulmaz.</span><span class="sxs-lookup"><span data-stu-id="fb703-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb703-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb703-119">Requirements</span></span>  
 <span data-ttu-id="fb703-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb703-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb703-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb703-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb703-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fb703-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb703-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb703-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb703-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb703-124">See Also</span></span>  
 [<span data-ttu-id="fb703-125">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb703-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fb703-126">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb703-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
