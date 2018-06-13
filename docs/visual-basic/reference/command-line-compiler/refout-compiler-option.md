---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21cea76f31bdf2ac5fcf434ee759f874f917617b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653539"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="d9539-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9539-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="d9539-103">**- Refout** seçeneği, bir dosya yolu burada referans derlemesini gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9539-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="d9539-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9539-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="d9539-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d9539-105">Arguments</span></span>

 <span data-ttu-id="d9539-106">`filepath` Başvuru derlemenin dosya adı ve yolu.</span><span class="sxs-lookup"><span data-stu-id="d9539-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="d9539-107">Genellikle bir alt birincil derlemesi klasörde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9539-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="d9539-108">(MSBuild tarafından kullanılır) önerilen kuralı başvuru bütünleştirilmiş kodunda yerleştirmektir bir "ref /" Birincil derleme göreli alt klasör.</span><span class="sxs-lookup"><span data-stu-id="d9539-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="d9539-109">Tüm klasörleri `filepath` bulunmalıdır; derleyici bunları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d9539-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="d9539-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9539-110">Remarks</span></span>

<span data-ttu-id="d9539-111">Visual Basic destekler `-refout` 15.3 sürümünden başlayarak geçin.</span><span class="sxs-lookup"><span data-stu-id="d9539-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="d9539-112">Başvuru derlemeleri meta verileri, ancak hiçbir uygulama kodu içeren yalnızca meta veri derlemeler ' dir.</span><span class="sxs-lookup"><span data-stu-id="d9539-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="d9539-113">Bunlar, anonim türler dışında her şeyi için tür ve üye bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d9539-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="d9539-114">Kullanıcıların yöntem gövdeleri tek bir tıklatmayla değiştirilir `throw null` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d9539-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="d9539-115">Kullanmanın nedeni `throw null` yöntem gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="d9539-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="d9539-116">Başvuru derlemeleri içeren bir derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d9539-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="d9539-117">Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="d9539-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="d9539-118">Bu öznitelik nedeniyle başvuru yürütme derlemelerde yüklemek çalışma zamanları Reddet (ancak bunlar hala bir salt yansıma bağlamında yüklenen olabilir).</span><span class="sxs-lookup"><span data-stu-id="d9539-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="d9539-119">Yalnızca yansıma olarak başvuru derlemeleri yükleme emin olmak için derlemelerini yansıtacak araçları gerekir; Aksi halde, çalışma zamanı oluşturur bir <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="d9539-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="d9539-120">`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="d9539-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9539-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9539-121">See Also</span></span>
<span data-ttu-id="d9539-122">[-refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="d9539-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="d9539-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d9539-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="d9539-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d9539-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  

