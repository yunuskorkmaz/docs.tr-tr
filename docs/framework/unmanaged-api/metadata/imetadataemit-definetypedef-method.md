---
description: ': Imetadatayayma::D efineTypeDef yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: ca0c74b8c067771e9f45a8c00639d75c9ad08de1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784047"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="b1163-103">IMetaDataEmit::DefineTypeDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1163-103">IMetaDataEmit::DefineTypeDef Method</span></span>

<span data-ttu-id="b1163-104">Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="b1163-104">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1163-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1163-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1163-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1163-106">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="b1163-107">'ndaki Unicode 'daki türün adı.</span><span class="sxs-lookup"><span data-stu-id="b1163-107">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="b1163-108">[in] `TypeDef` özelliklerine.</span><span class="sxs-lookup"><span data-stu-id="b1163-108">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="b1163-109">Bu bir değer bit değeridir `CoreTypeAttr` .</span><span class="sxs-lookup"><span data-stu-id="b1163-109">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="b1163-110">'ndaki Taban sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="b1163-110">[in] The token of the base class.</span></span> <span data-ttu-id="b1163-111">`mdTypeDef`Ya da bir `mdTypeRef` belirteç olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1163-111">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="b1163-112">'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="b1163-112">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="b1163-113">dışı `mdTypeDef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="b1163-113">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1163-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1163-114">Remarks</span></span>  

 <span data-ttu-id="b1163-115">İçindeki bayrak `dwTypeDefFlags` , oluşturulan türün ortak bir tür sistem başvuru türü (sınıf veya arabirim) mi yoksa ortak bir tür sistemi değer türü mi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1163-115">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="b1163-116">Sağlanan parametrelere bağlı olarak, bu yöntem yan bir efekt olarak `mdInterfaceImpl` Bu tür tarafından devralınan veya uygulanan her arabirim için bir kayıt da oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b1163-116">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="b1163-117">Ancak, bu yöntem bu belirteçlerden herhangi birini döndürmez `mdInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="b1163-117">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="b1163-118">Bir istemci daha sonra bir belirteç eklemek veya bir belirteci değiştirmek isterse `mdInterfaceImpl` , `IMetaDataImport` bunları numaralandırmak için arabirimini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1163-118">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="b1163-119">Arabirimin COM semantiğini kullanmak istiyorsanız `[default]` , varsayılan arabirimi ' de ilk öğe olarak sağlamalısınız `rtkImplements` ; sınıfta ayarlanan özel bir öznitelik, sınıfın varsayılan bir arabirime sahip olduğunu belirtir (Bu, her zaman `mdInterfaceImpl` sınıf için belirtilen ilk belirteç olduğunu varsayacaktır).</span><span class="sxs-lookup"><span data-stu-id="b1163-119">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="b1163-120">Dizideki her öğe `rtkImplements` bir `mdTypeDef` veya `mdTypeRef` belirtecini barındırır.</span><span class="sxs-lookup"><span data-stu-id="b1163-120">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="b1163-121">Dizideki son öğe olmalıdır `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="b1163-121">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1163-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1163-122">Requirements</span></span>  

 <span data-ttu-id="b1163-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1163-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1163-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b1163-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1163-125">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b1163-125">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1163-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1163-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1163-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1163-127">See also</span></span>

- [<span data-ttu-id="b1163-128">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1163-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b1163-129">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1163-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
