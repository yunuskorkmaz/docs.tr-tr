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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175869"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="05ec5-102">IMetaDataEmit::DefineImportMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05ec5-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="05ec5-103">Geçerli kapsam dışında tanımlanan bir tür veya modülün belirtilen üyesine bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05ec5-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ec5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05ec5-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="05ec5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05ec5-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="05ec5-106">[içinde] Hedef üyenin içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="05ec5-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="05ec5-107">[içinde] Tarafından belirtilen derleme için karma içeren `pAssemImport`bir dizi.</span><span class="sxs-lookup"><span data-stu-id="05ec5-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="05ec5-108">[içinde] Dizideki `pbHashValue` bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="05ec5-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="05ec5-109">[içinde] Hedef üyenin içe aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="05ec5-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="05ec5-110">[içinde] Hedef üyeyi belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="05ec5-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="05ec5-111">Belirteç bir `mdMethodDef` (üye yöntemi için), `mdProperty` (üye özellik `mdFieldDef` için) veya (üye alan için) belirteç olabilir.</span><span class="sxs-lookup"><span data-stu-id="05ec5-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="05ec5-112">[içinde] Hedef üyenin içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="05ec5-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="05ec5-113">[içinde] Hedef `mdTypeRef` `mdModuleRef` üyenin sahibi olan tür veya modülün belirteci.</span><span class="sxs-lookup"><span data-stu-id="05ec5-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="05ec5-114">[çıkış] `mdMemberRef` Üye başvurusu için geçerli kapsamda tanımlanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="05ec5-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05ec5-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05ec5-115">Remarks</span></span>  
 <span data-ttu-id="05ec5-116">Yöntem, `DefineImportMember` başka bir kapsamda `mbMember`tanımlanan, belirtilen `pImport`üyeyi arar ve özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="05ec5-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="05ec5-117">Bu bilgileri, üye başvurusu oluşturmak için geçerli kapsamdaki [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) yöntemini aramak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="05ec5-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="05ec5-118">Genellikle, `DefineImportMember` yöntemi kullanmadan önce, geçerli kapsamda, hedef üyenin ana sınıfı, arabirimi veya modülü için bir tür başvurusu veya modül başvurusu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05ec5-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="05ec5-119">Bu başvuru için meta veri belirteci `tkParent` sonra bağımsız değişkengeçirilir.</span><span class="sxs-lookup"><span data-stu-id="05ec5-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="05ec5-120">Derleyici veya bağlayıcı tarafından daha sonra çözülecekse, hedef üyenin üst öğesine bir başvuru oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="05ec5-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="05ec5-121">Özetlersek:</span><span class="sxs-lookup"><span data-stu-id="05ec5-121">To summarize:</span></span>  
  
- <span data-ttu-id="05ec5-122">Hedef üye bir alan veya yöntemse, [iMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) veya [iMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) yöntemini kullanarak, geçerli kapsamda, üyenin üst sınıfı veya üst arabirimi için bir tür başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05ec5-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="05ec5-123">Hedef üye küresel bir değişken veya global bir işlevse (yani bir sınıfın veya arabirimin üyesi değilse), üyenin ana modülü için geçerli kapsamda bir modül başvurusu oluşturmak için [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="05ec5-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="05ec5-124">Hedef üyenin üst öğesi daha sonra derleyici veya bağlayıcı tarafından `mdTokenNil` çözülecekse, 'yi `tkParent`geçin.</span><span class="sxs-lookup"><span data-stu-id="05ec5-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="05ec5-125">Bunun geçerli olduğu tek senaryo, küresel bir işlev in veya global değişkenin sonunda geçerli modüle bağlanacak ve meta veriler birleştirilecek bir .obj dosyasından içe aktarıldığı zamandır.</span><span class="sxs-lookup"><span data-stu-id="05ec5-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ec5-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05ec5-126">Requirements</span></span>  
 <span data-ttu-id="05ec5-127">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ec5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ec5-128">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05ec5-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05ec5-129">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="05ec5-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05ec5-130">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ec5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ec5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05ec5-131">See also</span></span>

- [<span data-ttu-id="05ec5-132">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05ec5-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="05ec5-133">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05ec5-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
