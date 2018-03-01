---
title: IMetaDataEmit::MergeEnd Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="ef44d-102">IMetaDataEmit::MergeEnd Metodu</span><span class="sxs-lookup"><span data-stu-id="ef44d-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="ef44d-103">Birleştirmeler geçerli kapsam için bir veya daha fazla önceki çağrıları tarafından belirtilen tüm meta veri kapsamları [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="ef44d-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef44d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef44d-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef44d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef44d-105">Parameters</span></span>  
 <span data-ttu-id="ef44d-106">Bu yöntem parametre almaz.</span><span class="sxs-lookup"><span data-stu-id="ef44d-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef44d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef44d-107">Remarks</span></span>  
 <span data-ttu-id="ef44d-108">Bu yordam gerçek birleştirme meta verilerin tetikler, tüm kapsamlar çağrıları koyarak belirtilen alma `IMetaDataEmit::Merge`, geçerli çıkış kapsam içine.</span><span class="sxs-lookup"><span data-stu-id="ef44d-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="ef44d-109">Aşağıdaki özel koşullar birleştirme için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ef44d-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="ef44d-110">Meta veri alma kapsamında benzersiz olduğundan modülü sürüm tanıtıcısını (MVID) hiçbir zaman alınır.</span><span class="sxs-lookup"><span data-stu-id="ef44d-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="ef44d-111">Varolan modülü genelinde özellik üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ef44d-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="ef44d-112">Modülü özellikleri zaten geçerli kapsam için ayarlandıysa, hiçbir modülü özellikleri içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="ef44d-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="ef44d-113">Modülü özellikleri geçerli kapsamda ayarlanmamış, yalnızca zaman ilk karşılaşılan sonra ancak bunlar içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="ef44d-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="ef44d-114">Bu modülü özellikleri yeniden aldıysanız, yinelenen oldukları.</span><span class="sxs-lookup"><span data-stu-id="ef44d-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="ef44d-115">(MVID dışında) tüm modülü özelliklerinin değerlerini karşılaştırılır ve yinelenen bulunan, bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ef44d-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="ef44d-116">Tür tanımları için (`TypeDef`), yinelenen geçerli kapsam birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ef44d-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="ef44d-117">`TypeDef`nesneleri her karşı çoğaltmaları denetlenir *tam nesne adı* + *GUID* + *sürüm numarası*.</span><span class="sxs-lookup"><span data-stu-id="ef44d-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="ef44d-118">Adı veya GUID bir eşleşme yoktur ve herhangi bir diğer iki farklı ise, bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ef44d-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="ef44d-119">Aksi durumda, tüm üç öğe eşleşiyorsa `MergeEnd` girişleri gerçekten Tekrarların; sağlamak için basit bir denetim gerçekleştirir değilse, bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="ef44d-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="ef44d-120">Bu basit onay arar:</span><span class="sxs-lookup"><span data-stu-id="ef44d-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="ef44d-121">Aynı sırada gerçekleşen aynı üye bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="ef44d-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="ef44d-122">Olarak işaretlenmiş üyeleri `mdPrivateScope` (bkz [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırması) bu iade; bulunmayan özel birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ef44d-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="ef44d-123">Aynı sınıf düzeni.</span><span class="sxs-lookup"><span data-stu-id="ef44d-123">The same class layout.</span></span>  
  
     <span data-ttu-id="ef44d-124">Bunun anlamı bir `TypeDef` nesne her zaman tam olarak ve tutarlı bir şekilde tanımlanması gerekir her meta veri kapsamda durumda bildirilmiş; bunun üye uygulamalarını (için bir sınıf) birden çok derleme biriminden yayılır, tam tanımı olarak kabul edilir Her kapsamda varsa ve her bir kapsama artımlı.</span><span class="sxs-lookup"><span data-stu-id="ef44d-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="ef44d-125">Parametre adları sözleşmesine ilgili varsa, örneğin, bunlar aynı şekilde her kapsam içine yayınlaması gerekir; ilgili değilseniz, bunların meta verileri yayınlaması gerektiğini değil.</span><span class="sxs-lookup"><span data-stu-id="ef44d-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="ef44d-126">Özel durum olan bir `TypeDef` nesne artımlı üyeleri olarak işaretlenmiş olabilir `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="ef44d-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="ef44d-127">Bunlar, karşılaşmadan üzerine `MergeEnd` artımlı olarak bakmadan çoğaltmalar için geçerli bir kapsama ekler.</span><span class="sxs-lookup"><span data-stu-id="ef44d-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="ef44d-128">Derleyici özel kapsam anlar olduğundan derleyici kural zorlama için sorumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef44d-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="ef44d-129">Göreli sanal adresleri (RVAs) içeri aktarılan veya birleştirilmiş; Derleyici, bu bilgileri yeniden yayma olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="ef44d-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="ef44d-130">Özel öznitelikler yalnızca bağlı olan öğe birleştirildiğinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ef44d-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="ef44d-131">Örneğin, bir sınıfla ilişkilendirilen özel öznitelikler sınıfı ilk karşılaşıldığında birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ef44d-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="ef44d-132">Özel öznitelikler ilişkilendirilen bir `TypeDef` veya `MemberDef` , derleme birimine (örneğin, bir üye derleme zaman damgası) belirli, bunlar birleştirilmez ve kaldırmak veya bu tür meta verilerini güncelleştirmek için derleyici kadar olur.</span><span class="sxs-lookup"><span data-stu-id="ef44d-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef44d-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef44d-133">Requirements</span></span>  
 <span data-ttu-id="ef44d-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef44d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef44d-135">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ef44d-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef44d-136">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ef44d-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef44d-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef44d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef44d-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef44d-138">See Also</span></span>  
 [<span data-ttu-id="ef44d-139">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef44d-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ef44d-140">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef44d-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
