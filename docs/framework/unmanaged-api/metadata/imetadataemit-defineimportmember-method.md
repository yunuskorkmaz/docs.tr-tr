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
ms.openlocfilehash: 2facc63023a20dd6aaac64d7d036324c31658bc8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501319"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="ca6b0-102">IMetaDataEmit::DefineImportMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca6b0-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="ca6b0-103">Geçerli kapsamın dışında tanımlanan bir tür veya modülün belirtilen üyesine bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca6b0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ca6b0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ca6b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca6b0-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="ca6b0-106">'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ca6b0-107">'ndaki Tarafından belirtilen derlemenin karmasını içeren bir dizi `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="ca6b0-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ca6b0-108">'ndaki Dizideki bayt sayısı `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="ca6b0-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="ca6b0-109">'ndaki Hedef üyenin içeri aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="ca6b0-110">'ndaki Hedef üyeyi belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="ca6b0-111">Belirteç bir `mdMethodDef` (üye yöntemi için), `mdProperty` (üye özelliği için) veya `mdFieldDef` (bir üye alanı için) belirteci olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="ca6b0-112">'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="ca6b0-113">'ndaki `mdTypeRef` `mdModuleRef` Hedef üyeye sahip olan, sırasıyla tür veya modül için belirteç.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="ca6b0-114">dışı `mdMemberRef`Üye başvurusu için geçerli kapsamda tanımlanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca6b0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca6b0-115">Remarks</span></span>  
 <span data-ttu-id="ca6b0-116">Yöntemi tarafından belirtilen, tarafından belirtilen `DefineImportMember` `mbMember` başka bir kapsamda tanımlanan üyeyi arar `pImport` ve özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="ca6b0-117">Bu bilgileri, üye başvurusunu oluşturmak için geçerli kapsamdaki [ımetadatayayma::D efineMemberRef](imetadataemit-definememberref-method.md) metodunu çağırmak üzere kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="ca6b0-118">Genellikle, yöntemini kullanmadan önce, `DefineImportMember` hedef üyenin üst sınıfı, arabirimi veya modülü için geçerli kapsamda, bir tür başvurusu veya modül başvurusu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="ca6b0-119">Bu başvurunun meta veri belirteci daha sonra `tkParent` bağımsız değişkenine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="ca6b0-120">Derleyici veya bağlayıcı tarafından daha sonra çözülebiliyorsa, hedef üyenin üst öğesine bir başvuru oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="ca6b0-121">Özetlersek:</span><span class="sxs-lookup"><span data-stu-id="ca6b0-121">To summarize:</span></span>  
  
- <span data-ttu-id="ca6b0-122">Hedef üye bir alan veya yöntem ise, üyenin üst sınıfı veya üst arabirimi için geçerli kapsamda bir tür başvurusu oluşturmak için [ımetadatayayma::D efineTypeRefByName](imetadataemit-definetyperefbyname-method.md) veya [ımetadatayayma::D Efineımporttype](imetadataemit-defineimporttype-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="ca6b0-123">Hedef üye bir genel değişken veya genel işlevse (yani, bir sınıfın veya arabirimin üyesi değil), üyenin üst modülünün geçerli kapsamındaki bir modül başvurusu oluşturmak için [ımetadatayayma::D efineModuleRef](imetadataemit-definemoduleref-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="ca6b0-124">Hedef üyenin üst öğesi daha sonra derleyici veya bağlayıcı tarafından çözülecektir, sonra da geçiş yapın `mdTokenNil` `tkParent` .</span><span class="sxs-lookup"><span data-stu-id="ca6b0-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="ca6b0-125">Bu tek senaryo, genel bir işlev veya genel değişken, son olarak geçerli modüle ve birleştirilmiş meta veriler ile bağlantılandırılan bir. obj dosyasından içeri aktarılırken yapılır.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6b0-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca6b0-126">Requirements</span></span>  
 <span data-ttu-id="ca6b0-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6b0-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6b0-128">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ca6b0-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca6b0-129">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ca6b0-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca6b0-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6b0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6b0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca6b0-131">See also</span></span>

- [<span data-ttu-id="ca6b0-132">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca6b0-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ca6b0-133">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca6b0-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
