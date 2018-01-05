---
title: "IMetaDataEmit::DefineTypeDef Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeDef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8fed37605252139428aa40bb3785c242d95cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="2ff72-102">IMetaDataEmit::DefineTypeDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ff72-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="2ff72-103">Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="2ff72-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff72-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ff72-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ff72-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ff72-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="2ff72-106">[in] Unicode türünün adı.</span><span class="sxs-lookup"><span data-stu-id="2ff72-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="2ff72-107">[in] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="2ff72-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="2ff72-108">Bu, bir bit maskesi olan `CoreTypeAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="2ff72-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="2ff72-109">[in] Belirtecin temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="2ff72-109">[in] The token of the base class.</span></span> <span data-ttu-id="2ff72-110">Aşağıdakilerden biri olması gereken bir `mdTypeDef` veya bir `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="2ff72-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="2ff72-111">[in] Bu sınıf veya arabirimi uygulayan arabirimlerini belirtme belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="2ff72-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="2ff72-112">[out] `mdTypeDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="2ff72-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff72-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ff72-113">Remarks</span></span>  
 <span data-ttu-id="2ff72-114">Bir bayrak `dwTypeDefFlags` oluşturulan türü bir ortak sistem başvuru türü (sınıf veya arabirim) veya ortak bir sistem değer türü olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ff72-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="2ff72-115">Belirtilen parametreler bağlı olarak, bu yöntem bir yan etkisi da oluşturabilir bir `mdInterfaceImpl` devralınan veya bu türü tarafından uygulanan her bir arabirim için kayıt.</span><span class="sxs-lookup"><span data-stu-id="2ff72-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="2ff72-116">Ancak, bu yöntem herhangi birini döndürmez `mdInterfaceImpl` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="2ff72-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="2ff72-117">Daha sonra eklemek veya değiştirmek bir istemci istiyorsa, bir `mdInterfaceImpl` belirteç, bunu kullanmalı `IMetaDataImport` bunları numaralandırmak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="2ff72-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="2ff72-118">COM semantiği kullanmak istiyorsanız, `[default]` arabirimi, sağladığınız varsayılan arabirimi ilk öğe olarak `rtkImplements`; set sınıfı üzerinde özel bir öznitelik sınıfı varsayılan arabirimi olduğunu gösterir (hangi olduğu her zaman varsayılır İlk `mdInterfaceImpl` belirteci bildirilen sınıfı için).</span><span class="sxs-lookup"><span data-stu-id="2ff72-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="2ff72-119">Her öğeye `rtkImplements` dizi ayrı tutma bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="2ff72-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="2ff72-120">Dizi son öğesi olmalı `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="2ff72-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff72-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ff72-121">Requirements</span></span>  
 <span data-ttu-id="2ff72-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff72-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff72-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ff72-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ff72-124">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2ff72-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ff72-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff72-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff72-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ff72-126">See Also</span></span>  
 [<span data-ttu-id="2ff72-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ff72-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2ff72-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ff72-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
