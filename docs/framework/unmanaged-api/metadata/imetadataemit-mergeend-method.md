---
title: IMetaDataEmit::MergeEnd Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4e3045476fc68dbeb545b7394b373be4ff881c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584285"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="14000-102">IMetaDataEmit::MergeEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14000-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="14000-103">Birleştirmeleri geçerli kapsam için bir veya daha fazla önceki çağrılar tarafından belirtilen tüm meta veri kapsamları [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="14000-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14000-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14000-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
## <a name="parameters"></a><span data-ttu-id="14000-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14000-105">Parameters</span></span>  
 <span data-ttu-id="14000-106">Bu yöntem parametre almaz.</span><span class="sxs-lookup"><span data-stu-id="14000-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14000-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14000-107">Remarks</span></span>  
 <span data-ttu-id="14000-108">Bu yordam meta verilerinin gerçek birleştirme tetiklenir, tüm çağrıları koyarak Belirtilen kapsam içeri `IMetaDataEmit::Merge`, geçerli çıkış kapsama.</span><span class="sxs-lookup"><span data-stu-id="14000-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="14000-109">Birleştirme için aşağıdaki özel koşullar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="14000-109">The following special conditions apply to the merge:</span></span>  
  
- <span data-ttu-id="14000-110">Meta veri içeri aktarma kapsamı içinde benzersiz olduğu için modülü sürüm tanımlayıcısı (MVID) hiçbir zaman aktarılır.</span><span class="sxs-lookup"><span data-stu-id="14000-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
- <span data-ttu-id="14000-111">Mevcut hiçbir modül genelinde özellik üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="14000-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="14000-112">Hiçbir modül özellik modülü özellikleri geçerli kapsam için zaten belirlenmişse içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="14000-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="14000-113">Modülü özellikleri geçerli kapsamda ayarlanmamış ise yalnızca zaman ilk karşılaşılan sonra ancak bunlar içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="14000-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="14000-114">Bu modülü özellikleri yeniden karşılaşılırsa, çoğaltmaları değildirler.</span><span class="sxs-lookup"><span data-stu-id="14000-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="14000-115">Tüm modül özelliklerini (dışında MVID) değerlerini karşılaştırılır ve yinelenen öğeler bulundu, bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="14000-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
- <span data-ttu-id="14000-116">Tür tanımları (`TypeDef`), yinelemelere geçerli kapsam birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="14000-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="14000-117">`TypeDef` nesneleri her karşı çoğaltmaları denetlenir *nesne tam adı* + *GUID* + *sürüm numarası*.</span><span class="sxs-lookup"><span data-stu-id="14000-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="14000-118">Bir eşleşme adı veya GUID ve diğer iki öğelerden farklı ise, bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="14000-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="14000-119">Aksi durumda, tüm üç öğe eşleşiyorsa `MergeEnd` girişleri çoğaltmaları; aslında olduğundan emin olmak için basit bir denetim gerçekleştirir Aksi takdirde bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="14000-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="14000-120">Bu basit bir onay arar:</span><span class="sxs-lookup"><span data-stu-id="14000-120">This cursory check looks for:</span></span>  
  
    - <span data-ttu-id="14000-121">Aynı sırada gerçekleşen aynı üye bildirim kullanımları.</span><span class="sxs-lookup"><span data-stu-id="14000-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="14000-122">Olarak işaretlenmiş üyeleri `mdPrivateScope` (bkz [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırması) bu iade; bulunmayan özel birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="14000-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    - <span data-ttu-id="14000-123">Aynı sınıf düzeni.</span><span class="sxs-lookup"><span data-stu-id="14000-123">The same class layout.</span></span>  
  
     <span data-ttu-id="14000-124">Diğer bir deyişle bir `TypeDef` nesne her zaman tam olarak ve tutarlı bir şekilde tanımlanmalıdır her meta veri kapsamında, BT bildirilir; bunun üye uygulamalarını (için bir sınıf) arasında birden çok derleme biriminden yayılır, tam tanımı olarak kabul edilir Her kapsamda varsa ve her kapsam için artımlı.</span><span class="sxs-lookup"><span data-stu-id="14000-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="14000-125">Parametre adları sözleşmesine uygun olan, örneğin, bunlar aynı şekilde her kapsamına yayılan gerekir; ilgili olmayan, bunların meta verilere yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="14000-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="14000-126">Özel durum olan bir `TypeDef` nesne artımlı üyeleri olarak işaretlenmiş olabilir `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="14000-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="14000-127">Bunlar, karşılaşıldığında üzerinde `MergeEnd` artımlı olarak çoğaltmaları olmadan geçerli bir kapsama ekler.</span><span class="sxs-lookup"><span data-stu-id="14000-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="14000-128">Derleyici özel kapsam anlayan olduğundan derleyici kurallar uygulamaktan sorumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14000-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
- <span data-ttu-id="14000-129">Göreli sanal adreslerine (RVA) içeri aktarılan veya birleştirilmiş; Derleyici bu bilgileri yeniden yayma bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="14000-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
- <span data-ttu-id="14000-130">Özel öznitelikler, bağlı öğe birleştirildiğinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="14000-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="14000-131">Örneğin, sınıf ilk karşılaşıldığında bir sınıf ile ilişkili özel öznitelikler birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="14000-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="14000-132">Özel öznitelikler ilişkilendirilen bir `TypeDef` veya `MemberDef` derleme birimi (örneğin, bir üye derleme zaman damgasını) özgü olan, birleştirilmiş değil ve kaldırın veya bu tür meta verileri güncelleştirmek için derleyici en fazla olan.</span><span class="sxs-lookup"><span data-stu-id="14000-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14000-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14000-133">Requirements</span></span>  
 <span data-ttu-id="14000-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14000-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14000-135">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="14000-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14000-136">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="14000-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14000-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14000-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14000-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14000-138">See also</span></span>

- [<span data-ttu-id="14000-139">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14000-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="14000-140">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14000-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
