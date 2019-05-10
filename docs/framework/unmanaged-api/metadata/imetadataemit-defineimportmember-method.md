---
title: IMetaDataEmit::DefineImportMember Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8851b3090685b19c4a7ef711d5adab232e46872e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665047"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="09011-102">IMetaDataEmit::DefineImportMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09011-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="09011-103">Bir türün veya geçerli kapsam dışında tanımlanan ve bu başvuru için bir belirteç tanımlar modülü belirtilen üyesine bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="09011-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09011-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09011-104">Syntax</span></span>  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09011-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09011-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="09011-106">[in] Bir [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) hedef üye içe derleme temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="09011-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="09011-107">[in] Tarafından belirtilen derleme için karma içeren bir dizi `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="09011-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="09011-108">[in] Bayt sayısı `pbHashValue` dizisi.</span><span class="sxs-lookup"><span data-stu-id="09011-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="09011-109">[in] Bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) hedef üye içe meta veri kapsamı temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="09011-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="09011-110">[in] Hedef üye belirleyen meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="09011-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="09011-111">Belirteç olabilir bir `mdMethodDef` (için üye yöntemi) `mdProperty` (bir üye özelliği için) veya `mdFieldDef` (için bir üye alan) belirteci.</span><span class="sxs-lookup"><span data-stu-id="09011-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="09011-112">[in] Bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) hedef üye içe içine derleme temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="09011-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="09011-113">[in] `mdTypeRef` Veya `mdModuleRef` typ nebo modul belirteci, sırasıyla, hedef üye sahip.</span><span class="sxs-lookup"><span data-stu-id="09011-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="09011-114">[out] `mdMemberRef` Üye başvurusu için geçerli kapsamda tanımlı belirteç.</span><span class="sxs-lookup"><span data-stu-id="09011-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09011-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09011-115">Remarks</span></span>  
 <span data-ttu-id="09011-116">`DefineImportMember` Yöntemi tarafından belirtilen üye, şuna `mbMember`, yani tarafından belirtilen başka bir kapsamda tanımlı `pImport`ve özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="09011-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="09011-117">Çağırmak için bu bilgileri kullanır [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) üyesi başvuru oluşturmak için geçerli kapsamda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="09011-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="09011-118">Genellikle, önce kullanırsınız `DefineImportMember` yöntemi oluşturmanız gerekir, geçerli kapsam, bir tür başvurusu veya hedef üyenin üst sınıf, arabirim veya modül için modülü başvurusu.</span><span class="sxs-lookup"><span data-stu-id="09011-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="09011-119">Bu başvuru için meta veri belirteci sonra geçirilen `tkParent` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="09011-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="09011-120">Derleyici veya bağlayıcı tarafından daha çözümlenir, hedef üyenin üst başvuru oluşturmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="09011-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="09011-121">Özetlersek:</span><span class="sxs-lookup"><span data-stu-id="09011-121">To summarize:</span></span>  
  
- <span data-ttu-id="09011-122">Hedef alan veya yöntem üyesiyse, kullanın [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) veya [Imetadataemit::defineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) geçerli kapsamda bir tür başvurusu için oluşturmak üzere yöntemi Üyenin üst sınıfta veya üst arabirimi.</span><span class="sxs-lookup"><span data-stu-id="09011-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="09011-123">Genel bir değişken veya genel işlev (diğer bir deyişle, bir üyesi değil bir sınıf veya arabirim) hedef üye ise kullanın [Imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) geçerli kapsamda üyenin üst için bir modül başvurusu oluşturmak için yöntemi Modül.</span><span class="sxs-lookup"><span data-stu-id="09011-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="09011-124">Hedef üyenin üst daha sonra derleyici veya bağlayıcı tarafından çözümlenir, ardından geçirin `mdTokenNil` içinde `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="09011-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="09011-125">Tek senaryo, bu geçerlidir genel bir işlev olduğunda veya genel değişkeni geçerli bir modüle sonuçta bağlanacak bir .obj dosyasından içeri aktarılan ve meta veriler birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="09011-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09011-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09011-126">Requirements</span></span>  
 <span data-ttu-id="09011-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09011-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09011-128">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="09011-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09011-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="09011-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09011-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09011-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09011-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09011-131">See also</span></span>

- [<span data-ttu-id="09011-132">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09011-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="09011-133">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09011-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
