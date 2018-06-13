---
title: -refout (C# Derleyici Seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: cb0e26b03841c093f223b3013a0d3c52ffd914c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215283"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="e896b-102">-refout (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e896b-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="e896b-103">**- Refout** seçeneği, bir dosya yolu burada referans derlemesini gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e896b-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="e896b-104">Bu şekilde dönüşür `metadataPeStream` yayma API'sindeki.</span><span class="sxs-lookup"><span data-stu-id="e896b-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="e896b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e896b-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="e896b-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e896b-106">Arguments</span></span>

 <span data-ttu-id="e896b-107">`filepath` Başvuru derleme için filepath.</span><span class="sxs-lookup"><span data-stu-id="e896b-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="e896b-108">Bu genellikle birincil derlemesi eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="e896b-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="e896b-109">(MSBuild tarafından kullanılır) önerilen kuralı başvuru bütünleştirilmiş kodunda yerleştirmektir bir "ref /" Birincil derleme göreli alt klasör.</span><span class="sxs-lookup"><span data-stu-id="e896b-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="e896b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e896b-110">Remarks</span></span>

<span data-ttu-id="e896b-111">Yalnızca meta veri derleme sahip tek bir tıklatmayla yerine kendi yöntem gövdeleri `throw null` gövde, ancak anonim türler dışındaki tüm üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e896b-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="e896b-112">Kullanmanın nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="e896b-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="e896b-113">Başvuru derlemeleri içeren bir derleme düzeyi `ReferenceAssembly` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e896b-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="e896b-114">Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="e896b-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="e896b-115">Bu öznitelik nedeniyle çalışma zamanları başvuru yürütme derlemelerde yük reddeder (ancak bunlar hala salt yansıma modunda yüklenmiş olabilir).</span><span class="sxs-lookup"><span data-stu-id="e896b-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="e896b-116">Başvuru derlemeleri salt yansıma olarak yük emin olmak için derlemeleri gerekir yansıtacak Araçlar, aksi halde bunlar bir typeload çalışma zamanı hatasıyla karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="e896b-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="e896b-117">Daha fazla başvuru derlemeleri meta veriler (özel üyeler) yalnızca meta veri derlemelerden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="e896b-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="e896b-118">Bir referans derlemesini yalnızca API yüzeyi gerekeni için başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e896b-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="e896b-119">Gerçek derleme belirli uygulamalar için ilgili ek başvurular olabilir.</span><span class="sxs-lookup"><span data-stu-id="e896b-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="e896b-120">Örneği için başvuru bütünleştirilmiş kod `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e896b-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="e896b-121">Özel işlevi-üyeleri (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e896b-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="e896b-122">Varsa hiçbir `InternalsVisibleTo` öznitelikleri, iç işlevi üyeleri için aynı yapın.</span><span class="sxs-lookup"><span data-stu-id="e896b-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="e896b-123">Ancak (özel veya iç içe geçmiş türler dahil) tüm türleri başvuru derlemeleri tutulur.</span><span class="sxs-lookup"><span data-stu-id="e896b-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="e896b-124">Tüm öznitelikleri (hatta iç olanlar) korunur.</span><span class="sxs-lookup"><span data-stu-id="e896b-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="e896b-125">Tüm sanal yöntemleri korunur.</span><span class="sxs-lookup"><span data-stu-id="e896b-125">All virtual methods are kept.</span></span> <span data-ttu-id="e896b-126">Açık arabirim uygulamaları tutulur.</span><span class="sxs-lookup"><span data-stu-id="e896b-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="e896b-127">Kendi erişimciler sanal (ve dolayısıyla korunması gibi) açıkça gerçekleştirilen özellikleri ve olayları tutulur.</span><span class="sxs-lookup"><span data-stu-id="e896b-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="e896b-128">Yapı tüm alanları tutulur.</span><span class="sxs-lookup"><span data-stu-id="e896b-128">All fields of a struct are kept.</span></span> <span data-ttu-id="e896b-129">(Bu bir post adaydır-C#-7.1 iyileştirme)</span><span class="sxs-lookup"><span data-stu-id="e896b-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="e896b-130">`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="e896b-130">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="e896b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e896b-131">See Also</span></span>
 [<span data-ttu-id="e896b-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e896b-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="e896b-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="e896b-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
