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
ms.openlocfilehash: abbd35fe390cc09951b762a5fd671d2d34a57c6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177898"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="03a6c-102">IMetaDataImport::FindMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03a6c-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="03a6c-103">Diğer bir deyişle MemberRef belirteci üyesi için bir işaretçiye başvuru alır içine tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.</span><span class="sxs-lookup"><span data-stu-id="03a6c-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03a6c-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03a6c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03a6c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="03a6c-106">[in] Sınıf veya üye başvurusu aranacak kapsayan arabirimi TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="03a6c-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="03a6c-107">Bu değer ise `mdTokenNil`, genel değişken veya işlev genel başvurusu için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="03a6c-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="03a6c-108">[in] Aranacak üyesi başvuru adı.</span><span class="sxs-lookup"><span data-stu-id="03a6c-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="03a6c-109">[in] Üye başvurusu ikili meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03a6c-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="03a6c-110">[in] Bayt cinsinden boyutu `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="03a6c-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="03a6c-111">[out] Eşleşen MemberRef belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03a6c-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03a6c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03a6c-112">Remarks</span></span>  
 <span data-ttu-id="03a6c-113">Kapsayan sınıfı veya arabirimi kullanılarak üyesi belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="03a6c-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="03a6c-114">İmza geçirilen `FindMemberRef` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="03a6c-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="03a6c-115">İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="03a6c-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="03a6c-116">Belirteç, yerel TypeDef tablosuna bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="03a6c-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="03a6c-117">Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza, giriş olarak kullanmak `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="03a6c-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="03a6c-118">`FindMemberRef` sınıf veya arabirim içinde tanımlanmış olan üye başvuruları bulur; devralınan üye başvuruları bulmaz.</span><span class="sxs-lookup"><span data-stu-id="03a6c-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a6c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03a6c-119">Requirements</span></span>  
 <span data-ttu-id="03a6c-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03a6c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a6c-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="03a6c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03a6c-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="03a6c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03a6c-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03a6c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a6c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03a6c-124">See also</span></span>

- [<span data-ttu-id="03a6c-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03a6c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="03a6c-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03a6c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
