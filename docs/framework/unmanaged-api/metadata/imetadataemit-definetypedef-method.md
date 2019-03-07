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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf2ca9719cdf62637292bdb39437d36f4b3fcd49
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494417"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="3e2b5-102">IMetaDataEmit::DefineTypeDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e2b5-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="3e2b5-103">Ortak dil çalışma zamanı tür için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e2b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e2b5-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e2b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e2b5-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="3e2b5-106">[in] Unicode türünün adı.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="3e2b5-107">[in] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="3e2b5-108">Bu, bir bit maskesi, `CoreTypeAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="3e2b5-109">[in] Belirteç temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-109">[in] The token of the base class.</span></span> <span data-ttu-id="3e2b5-110">Aşağıdakilerden biri olması gereken bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="3e2b5-111">[in] Bu sınıf veya arabirim uyguladığı arabirimlerin belirtme belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="3e2b5-112">[out] `mdTypeDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e2b5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e2b5-113">Remarks</span></span>  
 <span data-ttu-id="3e2b5-114">Eklenen bir bayrak `dwTypeDefFlags` oluşturulan türü bir ortak tür sistemi başvuru türü (sınıfı veya arabirimi) ya da bir ortak tür sistemi değer türü olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="3e2b5-115">Belirtilen parametreler bağlı olarak, bu yöntem bir yan etkisi da oluşturabilir bir `mdInterfaceImpl` devralınan veya bu tür tarafından uygulanan her arabirim için kayıt.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="3e2b5-116">Ancak, bu yöntem bunlardan birine döndürmeyen `mdInterfaceImpl` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="3e2b5-117">Daha sonra eklemek veya değiştirmek bir istemci istiyorsa, bir `mdInterfaceImpl` belirteci, bunu kullanmalı `IMetaDataImport` bunları numaralandırmak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="3e2b5-118">COM semantikleri kullanmak istiyorsanız `[default]` arabirimi, sağladığınız varsayılan arabirimi ilk öğesi olarak `rtkImplements`; sınıfın varsayılan bir arabirim vardır sınıfına özel bir öznitelik belirtir (hangi olduğu her zaman varsayılır İlk `mdInterfaceImpl` belirteci bildirilen sınıf için).</span><span class="sxs-lookup"><span data-stu-id="3e2b5-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="3e2b5-119">Her öğeyi `rtkImplements` dizi içeren bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="3e2b5-120">Dizi içerisindeki son öğe olmalıdır `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e2b5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e2b5-121">Requirements</span></span>  
 <span data-ttu-id="3e2b5-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e2b5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e2b5-123">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3e2b5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e2b5-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3e2b5-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e2b5-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e2b5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2b5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e2b5-126">See also</span></span>
- [<span data-ttu-id="3e2b5-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e2b5-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3e2b5-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e2b5-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
