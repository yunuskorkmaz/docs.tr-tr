---
title: -refout (C# derleyici seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602508"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="1d69f-102">-refout (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1d69f-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="1d69f-103">**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d69f-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="1d69f-104">Bu, yayma `metadataPeStream` API 'sine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="1d69f-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="1d69f-105">Bu seçenek, MSBuild 'in [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) Project özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1d69f-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d69f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d69f-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="1d69f-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="1d69f-107">Arguments</span></span>

 <span data-ttu-id="1d69f-108">`filepath`Başvuru derlemesinin FilePath 'i.</span><span class="sxs-lookup"><span data-stu-id="1d69f-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="1d69f-109">Genellikle birincil derlemenin ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="1d69f-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="1d69f-110">Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="1d69f-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d69f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d69f-111">Remarks</span></span>

<span data-ttu-id="1d69f-112">Yalnızca meta veri derlemelerinde kendi yöntem gövdeleri tek `throw null` bir gövdele değiştirilmiştir, ancak anonim türler hariç tüm üyeleri dahil edin.</span><span class="sxs-lookup"><span data-stu-id="1d69f-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="1d69f-113">Gövdeler kullanmanın `throw null` nedeni (gövdeden farklı olarak), Peverify 'ın çalıştırılabilmesi ve geçmesi (Bu nedenle meta verilerin tamamlanmasının doğrulanması).</span><span class="sxs-lookup"><span data-stu-id="1d69f-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="1d69f-114">Başvuru derlemeleri bir derleme düzeyi `ReferenceAssembly` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="1d69f-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="1d69f-115">Bu öznitelik kaynakta belirtilebilir (derleyicinin onu birleştirmesini gerektirmez).</span><span class="sxs-lookup"><span data-stu-id="1d69f-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="1d69f-116">Bu öznitelik nedeniyle, çalışma zamanları yürütme için başvuru derlemelerini yüklemeyi reddeder (ancak yine de yalnızca yansıma modunda yüklenebilirler).</span><span class="sxs-lookup"><span data-stu-id="1d69f-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="1d69f-117">Derlemeleri yansıtan araçların başvuru derlemelerini yalnızca yansıma olarak yüklediklerinden emin olunması gerekir, aksi takdirde çalışma zamanından bir türde hatası alırlar.</span><span class="sxs-lookup"><span data-stu-id="1d69f-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="1d69f-118">Başvuru derlemeleri meta verileri (özel Üyeler) yalnızca meta veri derlemelerinden daha da kaldırır:</span><span class="sxs-lookup"><span data-stu-id="1d69f-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="1d69f-119">Bir başvuru derlemesinin yalnızca API yüzeyinde ihtiyacı olan başvurular vardır.</span><span class="sxs-lookup"><span data-stu-id="1d69f-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="1d69f-120">Gerçek derlemenin belirli uygulamalarla ilgili ek başvuruları olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d69f-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="1d69f-121">Örneğin, için `class C { private void M() { dynamic d = 1; ... } }` başvuru derlemesi için `dynamic`gereken herhangi bir türe başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="1d69f-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="1d69f-122">Özel işlev-Üyeler (Yöntemler, Özellikler ve olaylar) kaldırma işleminin derleme observably etkisi olmadığı durumlarda kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1d69f-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="1d69f-123"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Öznitelik yoksa, iç işlev üyeleri için aynı işlemi yapın.</span><span class="sxs-lookup"><span data-stu-id="1d69f-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="1d69f-124">Ancak tüm türler (özel veya iç içe türler dahil) başvuru Derlemeleriyle tutulur.</span><span class="sxs-lookup"><span data-stu-id="1d69f-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="1d69f-125">Tüm öznitelikler (hatta iç olmasalar bile) tutulur.</span><span class="sxs-lookup"><span data-stu-id="1d69f-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="1d69f-126">Tüm sanal yöntemler tutulur.</span><span class="sxs-lookup"><span data-stu-id="1d69f-126">All virtual methods are kept.</span></span> <span data-ttu-id="1d69f-127">Açık arabirim uygulamaları tutulur.</span><span class="sxs-lookup"><span data-stu-id="1d69f-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="1d69f-128">Açıkça uygulanan özellikler ve olaylar, erişimcileri sanal olduğundan (ve bu nedenle saklanır) tutulur.</span><span class="sxs-lookup"><span data-stu-id="1d69f-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="1d69f-129">Bir yapının tüm alanları tutulur.</span><span class="sxs-lookup"><span data-stu-id="1d69f-129">All fields of a struct are kept.</span></span> <span data-ttu-id="1d69f-130">(Bu,-C#-7,1 geliştirme sonrası için bir adaydır)</span><span class="sxs-lookup"><span data-stu-id="1d69f-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="1d69f-131">`-refout` [Ve`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="1d69f-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d69f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d69f-132">See also</span></span>

- [<span data-ttu-id="1d69f-133">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1d69f-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1d69f-134">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="1d69f-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
