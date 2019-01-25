---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 51029c071b3c5bdefe5af798f01238086b8e6d4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589798"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="2ec4c-102">-refonly (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2ec4c-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="2ec4c-103">**- Refonly** seçeneği, başvuru bütünleştirilmiş kodu çıkış olmalıdır nerede bir dosya yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="2ec4c-104">Bu şekilde dönüşür `metadataPeStream` yayma API.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ec4c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ec4c-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="2ec4c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ec4c-106">Arguments</span></span>

 <span data-ttu-id="2ec4c-107">`filepath` Başvuru bütünleştirilmiş kodu için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="2ec4c-108">Bu genellikle, birincil derlemenin eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="2ec4c-109">Başvuru derlemesinde yerleştirmek için (MSBuild tarafından kullanılır) önerilen kuralı olan bir "ref /" Birincil derleme göreli alt klasör.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ec4c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ec4c-110">Remarks</span></span>

<span data-ttu-id="2ec4c-111">Yalnızca meta veri bütünleştirilmiş kodları sahip tek bir yerine kendi metot gövdeleri `throw null` gövde, ancak anonim türler hariç tüm üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="2ec4c-112">Kullanılmasının nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğünü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="2ec4c-113">Başvuru derlemelerini içeren bir derleme düzeyi `ReferenceAssembly` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="2ec4c-114">Bu özniteliği, kaynakta belirtilebilir (sonra derleyici bu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="2ec4c-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="2ec4c-115">Bu öznitelik nedeniyle yürütme için başvuru derlemeleri yüklemeye çalışma zamanları reddeder (ancak bunlar yine de salt yansıma modunda olabilir).</span><span class="sxs-lookup"><span data-stu-id="2ec4c-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="2ec4c-116">Bunlar salt yansıma olarak başvuru derlemelerini yüklemek emin olmak için derlemeleri ihtiyacından yansıtan araçları, aksi takdirde bunlar typeload hata çalışma zamanını şuradan alır.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="2ec4c-117">Daha fazla başvuru bütünleştirilmiş kodları meta verilerini (özel üyeler) yalnızca meta veri derlemelerden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="2ec4c-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="2ec4c-118">Başvuru bütünleştirilmiş kodu, yalnızca bir API yüzeyi ihtiyacı olanları için başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="2ec4c-119">Gerçek derleme ilgili belirli uygulamalar için ek başvurular sahip.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="2ec4c-120">Örneğin, başvuru bütünleştirilmiş kodu için `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="2ec4c-121">Özel işlev-üyeler (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="2ec4c-122">Varsa hiçbir `InternalsVisibleTo` öznitelikleri, iç işlev üyeleri için aynı yapın.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="2ec4c-123">Ancak, tüm türler (özel veya iç içe türler dahil), başvuru bütünleştirilmiş kodları içinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="2ec4c-124">Tüm öznitelikleri (hatta iç olanlar) tutulur.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="2ec4c-125">Tüm sanal yöntemleri korunur.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-125">All virtual methods are kept.</span></span> <span data-ttu-id="2ec4c-126">Açık arabirim uygulamalarını tutulur.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="2ec4c-127">Kendi erişimciler sanal (ve bu nedenle tutulur gibi) açıkça uygulanan özellikleri ve olayları tutulur.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="2ec4c-128">Bir yapının tüm alanlarını tutulur.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-128">All fields of a struct are kept.</span></span> <span data-ttu-id="2ec4c-129">(Bu gönderi için adayıdır-C#-7.1 iyileştirme)</span><span class="sxs-lookup"><span data-stu-id="2ec4c-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="2ec4c-130">`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-130">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ec4c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ec4c-131">See also</span></span>

- [<span data-ttu-id="2ec4c-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2ec4c-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="2ec4c-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="2ec4c-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
