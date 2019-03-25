---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 24f5cba5650777f4844923844708d287798c445c
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409269"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="da6c4-102">-refonly (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="da6c4-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="da6c4-103">**- Refonly** seçeneği, bir başvuru bütünleştirilmiş kodu çıkış birincil çıktı olarak bir uygulama derleme yerine olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="da6c4-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="da6c4-104">`-refonly` Parametre sessiz bir şekilde devre dışı bırakır pdb, çıktısı olarak başvuru bütünleştirilmiş kodları yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="da6c4-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="da6c4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da6c4-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="da6c4-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da6c4-106">Remarks</span></span>

<span data-ttu-id="da6c4-107">Yalnızca meta veri bütünleştirilmiş kodları sahip tek bir yerine kendi metot gövdeleri `throw null` gövde, ancak anonim türler hariç tüm üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="da6c4-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="da6c4-108">Kullanılmasının nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğünü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="da6c4-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="da6c4-109">Başvuru derlemelerini içeren bir derleme düzeyi `ReferenceAssembly` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="da6c4-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="da6c4-110">Bu özniteliği, kaynakta belirtilebilir (sonra derleyici bu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="da6c4-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="da6c4-111">Bu öznitelik nedeniyle yürütme için başvuru derlemeleri yüklemeye çalışma zamanları reddeder (ancak bunlar yine de salt yansıma modunda olabilir).</span><span class="sxs-lookup"><span data-stu-id="da6c4-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="da6c4-112">Bunlar salt yansıma olarak başvuru derlemelerini yüklemek emin olmak için derlemeleri ihtiyacından yansıtan araçları, aksi takdirde bunlar typeload hata çalışma zamanını şuradan alır.</span><span class="sxs-lookup"><span data-stu-id="da6c4-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="da6c4-113">Daha fazla başvuru bütünleştirilmiş kodları meta verilerini (özel üyeler) yalnızca meta veri derlemelerden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="da6c4-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="da6c4-114">Başvuru bütünleştirilmiş kodu, yalnızca bir API yüzeyi ihtiyacı olanları için başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="da6c4-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="da6c4-115">Gerçek derleme ilgili belirli uygulamalar için ek başvurular sahip.</span><span class="sxs-lookup"><span data-stu-id="da6c4-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="da6c4-116">Örneğin, başvuru bütünleştirilmiş kodu için `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="da6c4-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="da6c4-117">Özel işlev-üyeler (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="da6c4-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="da6c4-118">Varsa hiçbir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelikleri, iç işlev üyeleri için aynı yapın.</span><span class="sxs-lookup"><span data-stu-id="da6c4-118">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="da6c4-119">Ancak, tüm türler (özel veya iç içe türler dahil), başvuru bütünleştirilmiş kodları içinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="da6c4-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="da6c4-120">Tüm öznitelikleri (hatta iç olanlar) tutulur.</span><span class="sxs-lookup"><span data-stu-id="da6c4-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="da6c4-121">Tüm sanal yöntemleri korunur.</span><span class="sxs-lookup"><span data-stu-id="da6c4-121">All virtual methods are kept.</span></span> <span data-ttu-id="da6c4-122">Açık arabirim uygulamalarını tutulur.</span><span class="sxs-lookup"><span data-stu-id="da6c4-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="da6c4-123">Kendi erişimciler sanal (ve bu nedenle tutulur gibi) açıkça uygulanan özellikleri ve olayları tutulur.</span><span class="sxs-lookup"><span data-stu-id="da6c4-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="da6c4-124">Bir yapının tüm alanlarını tutulur.</span><span class="sxs-lookup"><span data-stu-id="da6c4-124">All fields of a struct are kept.</span></span> <span data-ttu-id="da6c4-125">(Bu gönderi için adayıdır-C#-7.1 iyileştirme)</span><span class="sxs-lookup"><span data-stu-id="da6c4-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="da6c4-126">`-refonly` Ve [ `-refout` ](refout-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="da6c4-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="da6c4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da6c4-127">See also</span></span>

- [<span data-ttu-id="da6c4-128">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="da6c4-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="da6c4-129">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="da6c4-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
