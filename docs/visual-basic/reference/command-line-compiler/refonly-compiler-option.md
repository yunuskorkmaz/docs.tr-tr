---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653052"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="bc7f6-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc7f6-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="bc7f6-103">**- Refonly** seçeneği, derleme birincil çıkış uygulaması derleme yerine referans derlemesini olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="bc7f6-104">`-refonly` Parametre sessiz bir şekilde devre dışı bırakır pdb, kayıt çıkarma başvuru derlemeleri yürütülemez gibi.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="bc7f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc7f6-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="bc7f6-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc7f6-106">Remarks</span></span>

<span data-ttu-id="bc7f6-107">Visual Basic destekler `-refout` 15.3 sürümünden başlayarak geçin.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="bc7f6-108">Başvuru derlemeleri meta verileri, ancak hiçbir uygulama kodu içeren yalnızca meta veri derlemeler ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="bc7f6-109">Bunlar, anonim türler dışında her şeyi için tür ve üye bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="bc7f6-110">Kullanmanın nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="bc7f6-111">Başvuru derlemeleri içeren bir derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="bc7f6-112">Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="bc7f6-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="bc7f6-113">Bu öznitelik nedeniyle çalışma zamanları başvuru yürütme derlemelerde yük reddeder (ancak bunlar hala bir salt yansıma bağlamında yüklenen olabilir).</span><span class="sxs-lookup"><span data-stu-id="bc7f6-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="bc7f6-114">Yalnızca yansıma olarak başvuru derlemeleri yükleme emin olmak için derlemelerini yansıtacak araçları gerekir; Aksi halde, çalışma zamanı oluşturur bir <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="bc7f6-115">`-refonly` Ve [ `-refout` ](refout-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc7f6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc7f6-116">See also</span></span>
<span data-ttu-id="bc7f6-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="bc7f6-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="bc7f6-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bc7f6-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="bc7f6-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="bc7f6-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
