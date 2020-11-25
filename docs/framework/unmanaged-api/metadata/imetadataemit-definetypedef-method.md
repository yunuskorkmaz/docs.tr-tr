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
ms.openlocfilehash: 2e75b6322e40fe010e9e0a3412a99c0d3460afae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719378"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="41d18-102">IMetaDataEmit::DefineTypeDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41d18-102">IMetaDataEmit::DefineTypeDef Method</span></span>

<span data-ttu-id="41d18-103">Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="41d18-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d18-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="41d18-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41d18-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41d18-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="41d18-106">'ndaki Unicode 'daki türün adı.</span><span class="sxs-lookup"><span data-stu-id="41d18-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="41d18-107">[in] `TypeDef` özelliklerine.</span><span class="sxs-lookup"><span data-stu-id="41d18-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="41d18-108">Bu bir değer bit değeridir `CoreTypeAttr` .</span><span class="sxs-lookup"><span data-stu-id="41d18-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="41d18-109">'ndaki Taban sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="41d18-109">[in] The token of the base class.</span></span> <span data-ttu-id="41d18-110">`mdTypeDef`Ya da bir `mdTypeRef` belirteç olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41d18-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="41d18-111">'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="41d18-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="41d18-112">dışı `mdTypeDef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="41d18-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41d18-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41d18-113">Remarks</span></span>  

 <span data-ttu-id="41d18-114">İçindeki bayrak `dwTypeDefFlags` , oluşturulan türün ortak bir tür sistem başvuru türü (sınıf veya arabirim) mi yoksa ortak bir tür sistemi değer türü mi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="41d18-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="41d18-115">Sağlanan parametrelere bağlı olarak, bu yöntem yan bir efekt olarak `mdInterfaceImpl` Bu tür tarafından devralınan veya uygulanan her arabirim için bir kayıt da oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="41d18-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="41d18-116">Ancak, bu yöntem bu belirteçlerden herhangi birini döndürmez `mdInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="41d18-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="41d18-117">Bir istemci daha sonra bir belirteç eklemek veya bir belirteci değiştirmek isterse `mdInterfaceImpl` , `IMetaDataImport` bunları numaralandırmak için arabirimini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41d18-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="41d18-118">Arabirimin COM semantiğini kullanmak istiyorsanız `[default]` , varsayılan arabirimi ' de ilk öğe olarak sağlamalısınız `rtkImplements` ; sınıfta ayarlanan özel bir öznitelik, sınıfın varsayılan bir arabirime sahip olduğunu belirtir (Bu, her zaman `mdInterfaceImpl` sınıf için belirtilen ilk belirteç olduğunu varsayacaktır).</span><span class="sxs-lookup"><span data-stu-id="41d18-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="41d18-119">Dizideki her öğe `rtkImplements` bir `mdTypeDef` veya `mdTypeRef` belirtecini barındırır.</span><span class="sxs-lookup"><span data-stu-id="41d18-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="41d18-120">Dizideki son öğe olmalıdır `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="41d18-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d18-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41d18-121">Requirements</span></span>  

 <span data-ttu-id="41d18-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41d18-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d18-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="41d18-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41d18-124">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="41d18-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41d18-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d18-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d18-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41d18-126">See also</span></span>

- [<span data-ttu-id="41d18-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41d18-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="41d18-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41d18-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
