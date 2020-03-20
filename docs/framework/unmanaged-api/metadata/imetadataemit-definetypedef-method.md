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
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175765"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="263f2-102">IMetaDataEmit::DefineTypeDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="263f2-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="263f2-103">Ortak bir dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="263f2-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="263f2-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="263f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="263f2-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="263f2-106">[içinde] Unicode'daki türün adı.</span><span class="sxs-lookup"><span data-stu-id="263f2-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="263f2-107">[içinde] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="263f2-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="263f2-108">Bu `CoreTypeAttr` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="263f2-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="263f2-109">[içinde] Taban sınıfın belirteci.</span><span class="sxs-lookup"><span data-stu-id="263f2-109">[in] The token of the base class.</span></span> <span data-ttu-id="263f2-110">Ya bir `mdTypeDef` belirteç `mdTypeRef` ya da bir belirteç olmalı.</span><span class="sxs-lookup"><span data-stu-id="263f2-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="263f2-111">[içinde] Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir dizi belirteç.</span><span class="sxs-lookup"><span data-stu-id="263f2-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="263f2-112">[çıkış] Atanan `mdTypeDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="263f2-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="263f2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="263f2-113">Remarks</span></span>  
 <span data-ttu-id="263f2-114">Bir `dwTypeDefFlags` bayrak, oluşturulan türün ortak bir tür sistem başvuru türü (sınıf veya arabirim) veya ortak bir tür sistem değer türü olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="263f2-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="263f2-115">Sağlanan parametrelere bağlı olarak, bu yöntem, bir yan etki `mdInterfaceImpl` olarak, aynı zamanda bu tür tarafından devralınan veya uygulanan her arabirim için bir kayıt oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="263f2-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="263f2-116">Ancak, bu yöntem bu `mdInterfaceImpl` belirteçlerin hiçbirini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="263f2-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="263f2-117">İstemci daha sonra bir `mdInterfaceImpl` belirteç eklemek veya `IMetaDataImport` değiştirmek isterse, bunları sayısallandırmak için arabirimi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="263f2-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="263f2-118">`[default]` Arabirimin COM semantiklerini kullanmak istiyorsanız, varsayılan arabirimi ilk öğe olarak `rtkImplements`sağlamanız gerekir; sınıfa ayarlanan özel bir öznitelik, sınıfın varsayılan arabirimi olduğunu gösterir (bu her zaman sınıf için bildirilen ilk `mdInterfaceImpl` belirteç olarak kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="263f2-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="263f2-119">`rtkImplements` Dizinin her öğesi bir `mdTypeDef` `mdTypeRef` veya belirteç tutar.</span><span class="sxs-lookup"><span data-stu-id="263f2-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="263f2-120">Dizideki son öğe `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="263f2-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="263f2-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="263f2-121">Requirements</span></span>  
 <span data-ttu-id="263f2-122">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="263f2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263f2-123">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="263f2-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="263f2-124">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="263f2-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="263f2-125">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263f2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263f2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="263f2-126">See also</span></span>

- [<span data-ttu-id="263f2-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="263f2-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="263f2-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="263f2-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
