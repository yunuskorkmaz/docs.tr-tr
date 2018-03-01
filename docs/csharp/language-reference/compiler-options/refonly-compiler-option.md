---
title: "-refonly (C# Derleyici Seçenekleri)"
ms.date: 07/08/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25b0f6e024e194dff641fd5069755d0ea112a50b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="c0265-102">-refonly (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c0265-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="c0265-103">**- Refonly** seçeneği, bir referans derlemesini çıkış uygulaması derleme, birincil çıktı olarak yerine olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0265-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="c0265-104">`-refonly` Parametre sessiz bir şekilde devre dışı bırakır pdb, kayıt çıkarma başvuru derlemeleri yürütülemez gibi.</span><span class="sxs-lookup"><span data-stu-id="c0265-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0265-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0265-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="c0265-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0265-106">Remarks</span></span>

<span data-ttu-id="c0265-107">Yalnızca meta veri derleme sahip tek bir tıklatmayla yerine kendi yöntem gövdeleri `throw null` gövde, ancak anonim türler dışındaki tüm üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c0265-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="c0265-108">Kullanmanın nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="c0265-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="c0265-109">Başvuru derlemeleri içeren bir derleme düzeyi `ReferenceAssembly` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c0265-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="c0265-110">Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="c0265-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="c0265-111">Bu öznitelik nedeniyle çalışma zamanları başvuru yürütme derlemelerde yük reddeder (ancak bunlar hala salt yansıma modunda yüklenmiş olabilir).</span><span class="sxs-lookup"><span data-stu-id="c0265-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="c0265-112">Başvuru derlemeleri salt yansıma olarak yük emin olmak için derlemeleri gerekir yansıtacak Araçlar, aksi halde bunlar bir typeload çalışma zamanı hatasıyla karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="c0265-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="c0265-113">Daha fazla başvuru derlemeleri meta veriler (özel üyeler) yalnızca meta veri derlemelerden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="c0265-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="c0265-114">Bir referans derlemesini yalnızca API yüzeyi gerekeni için başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c0265-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="c0265-115">Gerçek derleme belirli uygulamalar için ilgili ek başvurular olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0265-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="c0265-116">Örneği için başvuru bütünleştirilmiş kod `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="c0265-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="c0265-117">Özel işlevi-üyeleri (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c0265-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="c0265-118">Varsa hiçbir `InternalsVisibleTo` öznitelikleri, iç işlevi üyeleri için aynı yapın.</span><span class="sxs-lookup"><span data-stu-id="c0265-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="c0265-119">Ancak (özel veya iç içe geçmiş türler dahil) tüm türleri başvuru derlemeleri tutulur.</span><span class="sxs-lookup"><span data-stu-id="c0265-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="c0265-120">Tüm öznitelikleri (hatta iç olanlar) korunur.</span><span class="sxs-lookup"><span data-stu-id="c0265-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="c0265-121">Tüm sanal yöntemleri korunur.</span><span class="sxs-lookup"><span data-stu-id="c0265-121">All virtual methods are kept.</span></span> <span data-ttu-id="c0265-122">Açık arabirim uygulamaları tutulur.</span><span class="sxs-lookup"><span data-stu-id="c0265-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="c0265-123">Kendi erişimciler sanal (ve dolayısıyla korunması gibi) açıkça gerçekleştirilen özellikleri ve olayları tutulur.</span><span class="sxs-lookup"><span data-stu-id="c0265-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="c0265-124">Yapı tüm alanları tutulur.</span><span class="sxs-lookup"><span data-stu-id="c0265-124">All fields of a struct are kept.</span></span> <span data-ttu-id="c0265-125">(Bu bir post adaydır-C#-7.1 iyileştirme)</span><span class="sxs-lookup"><span data-stu-id="c0265-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="c0265-126">`-refonly` Ve [ `-refout` ](refout-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="c0265-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0265-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0265-127">See also</span></span>
 [<span data-ttu-id="c0265-128">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c0265-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="c0265-129">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="c0265-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
