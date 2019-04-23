---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 34f7b62c0d9a14c52dde0ddd4ac0d5c29a3b5b75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976618"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="b3817-102">-refonly (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b3817-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="b3817-103">**- Refonly** seçeneği, başvuru bütünleştirilmiş kodu çıkış olmalıdır nerede bir dosya yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3817-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="b3817-104">Bu şekilde dönüşür `metadataPeStream` yayma API.</span><span class="sxs-lookup"><span data-stu-id="b3817-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="b3817-105">Bu seçenek karşılık gelen [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) proje MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="b3817-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3817-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3817-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="b3817-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3817-107">Arguments</span></span>

 <span data-ttu-id="b3817-108">`filepath` Başvuru bütünleştirilmiş kodu için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="b3817-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="b3817-109">Bu genellikle, birincil derlemenin eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b3817-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="b3817-110">Başvuru derlemesinde yerleştirmek için (MSBuild tarafından kullanılır) önerilen kuralı olan bir "ref /" Birincil derleme göreli alt klasör.</span><span class="sxs-lookup"><span data-stu-id="b3817-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3817-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3817-111">Remarks</span></span>

<span data-ttu-id="b3817-112">Yalnızca meta veri bütünleştirilmiş kodları sahip tek bir yerine kendi metot gövdeleri `throw null` gövde, ancak anonim türler hariç tüm üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b3817-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="b3817-113">Kullanılmasının nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğünü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="b3817-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="b3817-114">Başvuru derlemelerini içeren bir derleme düzeyi `ReferenceAssembly` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b3817-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="b3817-115">Bu özniteliği, kaynakta belirtilebilir (sonra derleyici bu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="b3817-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="b3817-116">Bu öznitelik nedeniyle yürütme için başvuru derlemeleri yüklemeye çalışma zamanları reddeder (ancak bunlar yine de salt yansıma modunda olabilir).</span><span class="sxs-lookup"><span data-stu-id="b3817-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="b3817-117">Bunlar salt yansıma olarak başvuru derlemelerini yüklemek emin olmak için derlemeleri ihtiyacından yansıtan araçları, aksi takdirde bunlar typeload hata çalışma zamanını şuradan alır.</span><span class="sxs-lookup"><span data-stu-id="b3817-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="b3817-118">Daha fazla başvuru bütünleştirilmiş kodları meta verilerini (özel üyeler) yalnızca meta veri derlemelerden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="b3817-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="b3817-119">Başvuru bütünleştirilmiş kodu, yalnızca bir API yüzeyi ihtiyacı olanları için başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b3817-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="b3817-120">Gerçek derleme ilgili belirli uygulamalar için ek başvurular sahip.</span><span class="sxs-lookup"><span data-stu-id="b3817-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="b3817-121">Örneğin, başvuru bütünleştirilmiş kodu için `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="b3817-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="b3817-122">Özel işlev-üyeler (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b3817-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="b3817-123">Varsa hiçbir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelikleri, iç işlev üyeleri için aynı yapın.</span><span class="sxs-lookup"><span data-stu-id="b3817-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="b3817-124">Ancak, tüm türler (özel veya iç içe türler dahil), başvuru bütünleştirilmiş kodları içinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="b3817-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="b3817-125">Tüm öznitelikleri (hatta iç olanlar) tutulur.</span><span class="sxs-lookup"><span data-stu-id="b3817-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="b3817-126">Tüm sanal yöntemleri korunur.</span><span class="sxs-lookup"><span data-stu-id="b3817-126">All virtual methods are kept.</span></span> <span data-ttu-id="b3817-127">Açık arabirim uygulamalarını tutulur.</span><span class="sxs-lookup"><span data-stu-id="b3817-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="b3817-128">Kendi erişimciler sanal (ve bu nedenle tutulur gibi) açıkça uygulanan özellikleri ve olayları tutulur.</span><span class="sxs-lookup"><span data-stu-id="b3817-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="b3817-129">Bir yapının tüm alanlarını tutulur.</span><span class="sxs-lookup"><span data-stu-id="b3817-129">All fields of a struct are kept.</span></span> <span data-ttu-id="b3817-130">(Bu gönderi için adayıdır-C#-7.1 iyileştirme)</span><span class="sxs-lookup"><span data-stu-id="b3817-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="b3817-131">`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="b3817-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3817-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3817-132">See also</span></span>

- [<span data-ttu-id="b3817-133">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b3817-133">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="b3817-134">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="b3817-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
