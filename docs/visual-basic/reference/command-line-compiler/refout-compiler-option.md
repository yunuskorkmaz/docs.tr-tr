---
title: -refout (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6075b92efd1eec9797fca248e97a325bd5df4bb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="fa6dc-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa6dc-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="fa6dc-103">**- Refout** seçeneği, bir dosya yolu burada referans derlemesini gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="fa6dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa6dc-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="fa6dc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fa6dc-105">Arguments</span></span>

 <span data-ttu-id="fa6dc-106">`filepath` Başvuru derlemenin dosya adı ve yolu.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="fa6dc-107">Genellikle bir alt birincil derlemesi klasörde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="fa6dc-108">(MSBuild tarafından kullanılır) önerilen kuralı başvuru bütünleştirilmiş kodunda yerleştirmektir bir "ref /" Birincil derleme göreli alt klasör.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="fa6dc-109">Tüm klasörleri `filepath` bulunmalıdır; derleyici bunları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="fa6dc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa6dc-110">Remarks</span></span>

<span data-ttu-id="fa6dc-111">Visual Basic destekler `-refout` 15.3 sürümünden başlayarak geçin.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="fa6dc-112">Başvuru derlemeleri meta verileri, ancak hiçbir uygulama kodu içeren yalnızca meta veri derlemeler ' dir.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="fa6dc-113">Bunlar, anonim türler dışında her şeyi için tür ve üye bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="fa6dc-114">Kullanıcıların yöntem gövdeleri tek bir tıklatmayla değiştirilir `throw null` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="fa6dc-115">Kullanmanın nedeni `throw null` yöntem gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="fa6dc-116">Başvuru derlemeleri içeren bir derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="fa6dc-117">Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="fa6dc-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="fa6dc-118">Bu öznitelik nedeniyle başvuru yürütme derlemelerde yüklemek çalışma zamanları Reddet (ancak bunlar hala bir salt yansıma bağlamında yüklenen olabilir).</span><span class="sxs-lookup"><span data-stu-id="fa6dc-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="fa6dc-119">Yalnızca yansıma olarak başvuru derlemeleri yükleme emin olmak için derlemelerini yansıtacak araçları gerekir; Aksi halde, çalışma zamanı oluşturur bir <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="fa6dc-120">`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa6dc-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa6dc-121">See Also</span></span>
<span data-ttu-id="fa6dc-122">[-refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="fa6dc-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="fa6dc-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="fa6dc-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="fa6dc-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="fa6dc-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  

