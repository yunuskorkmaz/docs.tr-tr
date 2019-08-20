---
title: -refonly (C# derleyici seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606491"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="714ba-102">-refonly (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="714ba-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="714ba-103">**-Refonly** seçeneği, bir başvuru derlemesinin birincil çıktı olarak bir uygulama derlemesi yerine çıkış olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="714ba-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="714ba-104">Başvuru derlemeleri yürütülene kadar parametresi,pdb'leriçıktısınıyenidendevredışıbırakır.`-refonly`</span><span class="sxs-lookup"><span data-stu-id="714ba-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="714ba-105">Bu seçenek, MSBuild 'in [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) Project özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="714ba-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="714ba-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="714ba-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="714ba-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="714ba-107">Remarks</span></span>

<span data-ttu-id="714ba-108">Yalnızca meta veri derlemelerinde kendi yöntem gövdeleri tek `throw null` bir gövdele değiştirilmiştir, ancak anonim türler hariç tüm üyeleri dahil edin.</span><span class="sxs-lookup"><span data-stu-id="714ba-108">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="714ba-109">Gövdeler kullanmanın `throw null` nedeni (gövdeden farklı olarak), Peverify 'ın çalıştırılabilmesi ve geçmesi (Bu nedenle meta verilerin tamamlanmasının doğrulanması).</span><span class="sxs-lookup"><span data-stu-id="714ba-109">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="714ba-110">Başvuru derlemeleri bir derleme düzeyi `ReferenceAssembly` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="714ba-110">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="714ba-111">Bu öznitelik kaynakta belirtilebilir (derleyicinin onu birleştirmesini gerektirmez).</span><span class="sxs-lookup"><span data-stu-id="714ba-111">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="714ba-112">Bu öznitelik nedeniyle, çalışma zamanları yürütme için başvuru derlemelerini yüklemeyi reddeder (ancak yine de yalnızca yansıma modunda yüklenebilirler).</span><span class="sxs-lookup"><span data-stu-id="714ba-112">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="714ba-113">Derlemeleri yansıtan araçların başvuru derlemelerini yalnızca yansıma olarak yüklediklerinden emin olunması gerekir, aksi takdirde çalışma zamanından bir türde hatası alırlar.</span><span class="sxs-lookup"><span data-stu-id="714ba-113">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="714ba-114">Başvuru derlemeleri meta verileri (özel Üyeler) yalnızca meta veri derlemelerinden daha da kaldırır:</span><span class="sxs-lookup"><span data-stu-id="714ba-114">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="714ba-115">Bir başvuru derlemesinin yalnızca API yüzeyinde ihtiyacı olan başvurular vardır.</span><span class="sxs-lookup"><span data-stu-id="714ba-115">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="714ba-116">Gerçek derlemenin belirli uygulamalarla ilgili ek başvuruları olabilir.</span><span class="sxs-lookup"><span data-stu-id="714ba-116">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="714ba-117">Örneğin, için `class C { private void M() { dynamic d = 1; ... } }` başvuru derlemesi için `dynamic`gereken herhangi bir türe başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="714ba-117">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="714ba-118">Özel işlev-Üyeler (Yöntemler, Özellikler ve olaylar) kaldırma işleminin derleme observably etkisi olmadığı durumlarda kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="714ba-118">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="714ba-119"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Öznitelik yoksa, iç işlev üyeleri için aynı işlemi yapın.</span><span class="sxs-lookup"><span data-stu-id="714ba-119">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="714ba-120">Ancak tüm türler (özel veya iç içe türler dahil) başvuru Derlemeleriyle tutulur.</span><span class="sxs-lookup"><span data-stu-id="714ba-120">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="714ba-121">Tüm öznitelikler (hatta iç olmasalar bile) tutulur.</span><span class="sxs-lookup"><span data-stu-id="714ba-121">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="714ba-122">Tüm sanal yöntemler tutulur.</span><span class="sxs-lookup"><span data-stu-id="714ba-122">All virtual methods are kept.</span></span> <span data-ttu-id="714ba-123">Açık arabirim uygulamaları tutulur.</span><span class="sxs-lookup"><span data-stu-id="714ba-123">Explicit interface implementations are kept.</span></span> <span data-ttu-id="714ba-124">Açıkça uygulanan özellikler ve olaylar, erişimcileri sanal olduğundan (ve bu nedenle saklanır) tutulur.</span><span class="sxs-lookup"><span data-stu-id="714ba-124">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="714ba-125">Bir yapının tüm alanları tutulur.</span><span class="sxs-lookup"><span data-stu-id="714ba-125">All fields of a struct are kept.</span></span> <span data-ttu-id="714ba-126">(Bu,-C#-7,1 geliştirme sonrası için bir adaydır)</span><span class="sxs-lookup"><span data-stu-id="714ba-126">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="714ba-127">`-refonly` [Ve`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="714ba-127">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="714ba-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="714ba-128">See also</span></span>

- [<span data-ttu-id="714ba-129">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="714ba-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="714ba-130">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="714ba-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
