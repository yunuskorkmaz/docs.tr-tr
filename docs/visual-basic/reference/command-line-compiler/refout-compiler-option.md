---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3d7f5f9065ba53bd037d7307f62c9acad913b8e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638713"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="d3b1f-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3b1f-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="d3b1f-103">**- Refonly** seçeneği, başvuru bütünleştirilmiş kodu çıkış olmalıdır nerede bir dosya yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="d3b1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3b1f-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="d3b1f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d3b1f-105">Arguments</span></span>

 <span data-ttu-id="d3b1f-106">`filepath` Başvuru bütünleştirilmiş kodunun dosya adı ve yolu.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="d3b1f-107">Genellikle bir alt birincil derlemesi klasörde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="d3b1f-108">Başvuru derlemesinde yerleştirmek için (MSBuild tarafından kullanılır) önerilen kuralı olan bir "ref /" Birincil derleme göreli alt klasör.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="d3b1f-109">Tüm klasörleri `filepath` bulunmalıdır; derleyici bunları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="d3b1f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3b1f-110">Remarks</span></span>

<span data-ttu-id="d3b1f-111">Visual Basic destekler `-refout` 15.3 sürümünden başlayarak geçin.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="d3b1f-112">Başvuru bütünleştirilmiş kodları meta verileri ancak hiçbir uygulama kodu içeren yalnızca meta veri derlemelerdir.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="d3b1f-113">Bunlar, anonim türler dışında her şeyi için tür ve üye bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="d3b1f-114">Kendi metot gövdeleri tek bir değiştirilir `throw null` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="d3b1f-115">Kullanılmasının nedeni `throw null` (gövde yok)'yerine metot gövdeleri olduğu PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğünü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="d3b1f-116">Başvuru derlemelerini içeren bir derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="d3b1f-117">Bu özniteliği, kaynakta belirtilebilir (sonra derleyici bu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="d3b1f-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="d3b1f-118">Bu öznitelik nedeniyle yürütme için başvuru derlemeleri yüklemeye çalışma zamanları Reddet (ancak bunlar yine de salt yansıma bir bağlamda yüklenmiş olabilir).</span><span class="sxs-lookup"><span data-stu-id="d3b1f-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="d3b1f-119">Bunlar salt yansıma olarak başvuru derlemelerini yüklemek emin olmak derlemelerini yansıtan araçları gerekir; Aksi takdirde, çalışma zamanı oluşturur bir <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="d3b1f-120">`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3b1f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b1f-121">See also</span></span>
- [<span data-ttu-id="d3b1f-122">-refonly</span><span class="sxs-lookup"><span data-stu-id="d3b1f-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="d3b1f-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d3b1f-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d3b1f-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d3b1f-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

