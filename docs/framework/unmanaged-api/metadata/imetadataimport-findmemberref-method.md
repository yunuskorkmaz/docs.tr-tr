---
title: IMetaDataImport::FindMemberRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3736d604b7e77028a2b99d462d88ae207df926c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448029"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="8a9e3-102">IMetaDataImport::FindMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a9e3-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="8a9e3-103">Üye için MemberRef belirteci için bir işaretçi başvuru diğer bir deyişle alır içine tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a9e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a9e3-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a9e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a9e3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8a9e3-106">[in] Sınıf veya aramak için üye başvuru barındırır arabirimi için TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="8a9e3-107">Bu değer ise `mdTokenNil`, genel değişken veya işlev genel başvurusu için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a9e3-108">[in] Aranacak üye referansın adı.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8a9e3-109">[in] Üye başvuru ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8a9e3-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="8a9e3-111">[out] Eşleşen MemberRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a9e3-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a9e3-112">Remarks</span></span>  
 <span data-ttu-id="8a9e3-113">Kapsayan sınıf ya da arabirimi kullanarak üyesi belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="8a9e3-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="8a9e3-114">İmza geçirilen `FindMemberRef` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="8a9e3-115">İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="8a9e3-116">Belirteç yerel TypeDef tabloya dizinidir.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="8a9e3-117">Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve girdi olarak bu imza kullanmak `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="8a9e3-118">`FindMemberRef` doğrudan sınıfta veya arabirimde tanımlanan üye başvuruları bulur; devralınan üye başvuruları bulmaz.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a9e3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a9e3-119">Requirements</span></span>  
 <span data-ttu-id="8a9e3-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a9e3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a9e3-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a9e3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a9e3-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8a9e3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a9e3-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a9e3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9e3-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a9e3-124">See Also</span></span>  
 [<span data-ttu-id="8a9e3-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a9e3-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8a9e3-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a9e3-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
