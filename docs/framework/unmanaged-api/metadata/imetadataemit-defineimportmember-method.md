---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D Efineımportmember yöntemi'
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
ms.openlocfilehash: 91c6ea70d38b8d4f73570ed19d86bacca30ebae5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753464"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="c965c-103">IMetaDataEmit::DefineImportMember Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c965c-103">IMetaDataEmit::DefineImportMember Method</span></span>

<span data-ttu-id="c965c-104">Geçerli kapsamın dışında tanımlanan bir tür veya modülün belirtilen üyesine bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c965c-104">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c965c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c965c-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c965c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c965c-106">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="c965c-107">'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c965c-107">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c965c-108">'ndaki Tarafından belirtilen derlemenin karmasını içeren bir dizi `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="c965c-108">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c965c-109">'ndaki Dizideki bayt sayısı `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="c965c-109">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="c965c-110">'ndaki Hedef üyenin içeri aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c965c-110">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="c965c-111">'ndaki Hedef üyeyi belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="c965c-111">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="c965c-112">Belirteç bir `mdMethodDef` (üye yöntemi için), `mdProperty` (üye özelliği için) veya `mdFieldDef` (bir üye alanı için) belirteci olabilir.</span><span class="sxs-lookup"><span data-stu-id="c965c-112">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="c965c-113">'ndaki Hedef üyenin içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c965c-113">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="c965c-114">'ndaki `mdTypeRef` `mdModuleRef` Hedef üyeye sahip olan, sırasıyla tür veya modül için belirteç.</span><span class="sxs-lookup"><span data-stu-id="c965c-114">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="c965c-115">dışı `mdMemberRef` Üye başvurusu için geçerli kapsamda tanımlanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="c965c-115">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c965c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c965c-116">Remarks</span></span>  

 <span data-ttu-id="c965c-117">Yöntemi tarafından belirtilen, tarafından belirtilen `DefineImportMember` `mbMember` başka bir kapsamda tanımlanan üyeyi arar `pImport` ve özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="c965c-117">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="c965c-118">Bu bilgileri, üye başvurusunu oluşturmak için geçerli kapsamdaki [ımetadatayayma::D efineMemberRef](imetadataemit-definememberref-method.md) metodunu çağırmak üzere kullanır.</span><span class="sxs-lookup"><span data-stu-id="c965c-118">It uses this information to call the [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="c965c-119">Genellikle, yöntemini kullanmadan önce, `DefineImportMember` hedef üyenin üst sınıfı, arabirimi veya modülü için geçerli kapsamda, bir tür başvurusu veya modül başvurusu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c965c-119">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="c965c-120">Bu başvurunun meta veri belirteci daha sonra `tkParent` bağımsız değişkenine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c965c-120">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="c965c-121">Derleyici veya bağlayıcı tarafından daha sonra çözülebiliyorsa, hedef üyenin üst öğesine bir başvuru oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c965c-121">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="c965c-122">Özetlemek gerekirse:</span><span class="sxs-lookup"><span data-stu-id="c965c-122">To summarize:</span></span>  
  
- <span data-ttu-id="c965c-123">Hedef üye bir alan veya yöntem ise, üyenin üst sınıfı veya üst arabirimi için geçerli kapsamda bir tür başvurusu oluşturmak için [ımetadatayayma::D efineTypeRefByName](imetadataemit-definetyperefbyname-method.md) veya [ımetadatayayma::D Efineımporttype](imetadataemit-defineimporttype-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c965c-123">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="c965c-124">Hedef üye bir genel değişken veya genel işlevse (yani, bir sınıfın veya arabirimin üyesi değil), üyenin üst modülünün geçerli kapsamındaki bir modül başvurusu oluşturmak için [ımetadatayayma::D efineModuleRef](imetadataemit-definemoduleref-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c965c-124">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="c965c-125">Hedef üyenin üst öğesi daha sonra derleyici veya bağlayıcı tarafından çözülecektir, sonra da geçiş yapın `mdTokenNil` `tkParent` .</span><span class="sxs-lookup"><span data-stu-id="c965c-125">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="c965c-126">Bu tek senaryo, genel bir işlev veya genel değişken, son olarak geçerli modüle ve birleştirilmiş meta veriler ile bağlantılandırılan bir. obj dosyasından içeri aktarılırken yapılır.</span><span class="sxs-lookup"><span data-stu-id="c965c-126">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c965c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c965c-127">Requirements</span></span>  

 <span data-ttu-id="c965c-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c965c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c965c-129">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c965c-129">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c965c-130">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c965c-130">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c965c-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c965c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c965c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c965c-132">See also</span></span>

- [<span data-ttu-id="c965c-133">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c965c-133">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c965c-134">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c965c-134">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
