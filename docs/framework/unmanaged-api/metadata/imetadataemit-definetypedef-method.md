---
title: IMetaDataEmit::DefineTypeDef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450221"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="34867-102">IMetaDataEmit::DefineTypeDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34867-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="34867-103">Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="34867-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34867-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34867-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34867-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34867-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="34867-106">'ndaki Unicode 'daki türün adı.</span><span class="sxs-lookup"><span data-stu-id="34867-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="34867-107">[in] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="34867-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="34867-108">Bu, `CoreTypeAttr` değerlerinin bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="34867-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="34867-109">'ndaki Taban sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="34867-109">[in] The token of the base class.</span></span> <span data-ttu-id="34867-110">`mdTypeDef` ya da `mdTypeRef` belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34867-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="34867-111">'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="34867-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="34867-112">dışı `mdTypeDef` belirteci atandı.</span><span class="sxs-lookup"><span data-stu-id="34867-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34867-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34867-113">Remarks</span></span>  
 <span data-ttu-id="34867-114">`dwTypeDefFlags` bir bayrak, oluşturulan türün ortak bir tür sistem başvuru türü (sınıf veya arabirim) mi yoksa ortak bir tür sistemi değer türü mi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="34867-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="34867-115">Sağlanan parametrelere bağlı olarak, bu yöntem bir yan etkisi olarak, bu tür tarafından devralınan veya uygulanan her arabirim için bir `mdInterfaceImpl` kaydı da oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="34867-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="34867-116">Ancak, bu yöntem bu `mdInterfaceImpl` belirteçlerinin hiçbirini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="34867-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="34867-117">Bir istemci daha sonra bir `mdInterfaceImpl` belirtecini eklemek veya değiştirmek isterse, bunları numaralandırmak için `IMetaDataImport` arabirimini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="34867-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="34867-118">`[default]` arabiriminin COM semantiğini kullanmak istiyorsanız, varsayılan arabirimi `rtkImplements`ilk öğe olarak sağlamalısınız; sınıfında ayarlanan özel bir öznitelik, sınıfın varsayılan bir arabirime sahip olduğunu gösterir (Bu, her zaman sınıf için bildirildiği ilk `mdInterfaceImpl` belirteç olarak varsayılır).</span><span class="sxs-lookup"><span data-stu-id="34867-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="34867-119">`rtkImplements` dizisinin her öğesi bir `mdTypeDef` veya `mdTypeRef` belirteci barındırır.</span><span class="sxs-lookup"><span data-stu-id="34867-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="34867-120">Dizideki son öğe `mdTokenNil`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34867-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34867-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34867-121">Requirements</span></span>  
 <span data-ttu-id="34867-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34867-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34867-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="34867-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34867-124">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="34867-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34867-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34867-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34867-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34867-126">See also</span></span>

- [<span data-ttu-id="34867-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34867-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="34867-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34867-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
