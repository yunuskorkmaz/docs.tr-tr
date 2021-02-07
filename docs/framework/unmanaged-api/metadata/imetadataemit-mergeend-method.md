---
description: ': Imetadatayayma:: MergeEnd yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: aac48b9bafb60cee4e3d73232d9f9c00cca7f796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745885"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="f136a-103">IMetaDataEmit::MergeEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f136a-103">IMetaDataEmit::MergeEnd Method</span></span>

<span data-ttu-id="f136a-104">[Imetadatayayma:: Merge](imetadataemit-merge-method.md)için bir veya daha fazla önceki çağrı tarafından belirtilen tüm meta veri kapsamlarını geçerli kapsama birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f136a-104">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](imetadataemit-merge-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="f136a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f136a-105">Syntax</span></span>

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a><span data-ttu-id="f136a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f136a-106">Parameters</span></span>

<span data-ttu-id="f136a-107">Bu yöntem hiçbir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="f136a-107">This method takes no parameters.</span></span>

## <a name="remarks"></a><span data-ttu-id="f136a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f136a-108">Remarks</span></span>

<span data-ttu-id="f136a-109">Bu yordam, önceki çağrıları tarafından belirtilen tüm içeri aktarma kapsamlarından geçerli çıkış kapsamına gerçek meta verilerin birleştirilmesini tetikler `IMetaDataEmit::Merge` .</span><span class="sxs-lookup"><span data-stu-id="f136a-109">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>

<span data-ttu-id="f136a-110">Aşağıdaki özel koşullar birleştirme için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f136a-110">The following special conditions apply to the merge:</span></span>

- <span data-ttu-id="f136a-111">İçeri aktarma kapsamındaki meta veriler için benzersiz olduğundan, bir modül sürümü tanımlayıcısı (MVıD) hiçbir şekilde içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="f136a-111">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>

- <span data-ttu-id="f136a-112">Modül genelinde mevcut özelliklerin üzerine yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="f136a-112">No existing module-wide properties are overwritten.</span></span>

  <span data-ttu-id="f136a-113">Geçerli kapsam için modül özellikleri zaten ayarlandıysa, hiçbir modül özelliği içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="f136a-113">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="f136a-114">Ancak, geçerli kapsamda modül özellikleri ayarlanmamışsa, ilk kez karşılaşıldığında yalnızca bir kez içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="f136a-114">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="f136a-115">Bu modül özelliklerine yeniden karşılaşılırsa, bunlar yinelemelerdir.</span><span class="sxs-lookup"><span data-stu-id="f136a-115">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="f136a-116">Tüm modül özelliklerinin (MVıD hariç) değerleri karşılaştırılaysa ve yinelenen öğeler bulunmazsa bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="f136a-116">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>

- <span data-ttu-id="f136a-117">Tür tanımları ( `TypeDef` ) için, geçerli kapsamda birleştirilmemiş bir yineleme yok.</span><span class="sxs-lookup"><span data-stu-id="f136a-117">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="f136a-118">`TypeDef`nesneler, *tam nitelikli nesne adı*  +  *GUID*  +  *sürüm numarasına* göre yinelemeler için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f136a-118">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="f136a-119">Ad veya GUID üzerinde bir eşleşme varsa ve diğer iki öğe farklıysa, bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="f136a-119">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="f136a-120">Aksi takdirde, üç öğe de eşleşiyorsa, `MergeEnd` girişlerin gerçekten yinelendiğinden emin olmak için bir Amna hatlarıyla denetimi yapar; değilse bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="f136a-120">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="f136a-121">Bu Amna hatlarıyla denetimi şuna bakar:</span><span class="sxs-lookup"><span data-stu-id="f136a-121">This cursory check looks for:</span></span>

  - <span data-ttu-id="f136a-122">Aynı sırada oluşan aynı üye bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="f136a-122">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="f136a-123">İşaretlenen Üyeler `mdPrivateScope` (bkz. [Cormethodadttr](cormethodattr-enumeration.md) sabit listesi) Bu denetim kapsamında değildir; özel olarak birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f136a-123">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>

  - <span data-ttu-id="f136a-124">Aynı sınıf düzeni.</span><span class="sxs-lookup"><span data-stu-id="f136a-124">The same class layout.</span></span>

  <span data-ttu-id="f136a-125">Bu `TypeDef` , bir nesnenin, bildirildiği her meta veri kapsamında her zaman tam ve tutarlı bir şekilde tanımlanması gerektiği anlamına gelir; üye uygulamaları (bir sınıf için) birden çok derleme birimine yayılıyorsa, tam tanımın her kapsamda mevcut olduğu kabul edilir ve her kapsam için artımlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f136a-125">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="f136a-126">Örneğin, parametre adları sözleşmeyle ilgiliyse, her kapsama aynı şekilde yayılmaları gerekir; Bunlar ilgili değilse meta verilere yayılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f136a-126">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>

  <span data-ttu-id="f136a-127">Özel durum, bir `TypeDef` nesne, işaretlenmiş artımlı üyelere sahip olabilir `mdPrivateScope` .</span><span class="sxs-lookup"><span data-stu-id="f136a-127">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="f136a-128">`MergeEnd`Bunlarla karşılaşmadan, yinelenenleri, yinelemeleri dikkate almadan geçerli kapsama ekler.</span><span class="sxs-lookup"><span data-stu-id="f136a-128">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="f136a-129">Derleyici özel kapsamı anladığından, derleyicinin kuralları zorlarken sorumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f136a-129">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>

- <span data-ttu-id="f136a-130">Göreli sanal adresler (RVA) içeri aktarılmaz veya birleştirilmez; Derleyicinin bu bilgileri yeniden yayma beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f136a-130">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>

- <span data-ttu-id="f136a-131">Özel öznitelikler yalnızca, eklendiği öğe birleştirildiğinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f136a-131">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="f136a-132">Örneğin, bir sınıfla ilişkili özel öznitelikler, sınıf ilk kez karşılaşıldığında birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f136a-132">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="f136a-133">Özel öznitelikler, `TypeDef` derleme birimine özgü olan bir veya ile ilişkilendirilmişse `MemberDef` (bir üyenin derlenmesi zaman damgası gibi), birleştirilmez ve bu meta verileri kaldırmak veya güncelleştirmek için derleyiciye kadar olur.</span><span class="sxs-lookup"><span data-stu-id="f136a-133">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="f136a-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f136a-134">Requirements</span></span>

<span data-ttu-id="f136a-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f136a-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f136a-136">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f136a-136">**Header:** Cor.h</span></span>

<span data-ttu-id="f136a-137">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f136a-137">**Library:** Used as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="f136a-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f136a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f136a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f136a-139">See also</span></span>

- [<span data-ttu-id="f136a-140">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f136a-140">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f136a-141">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f136a-141">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
