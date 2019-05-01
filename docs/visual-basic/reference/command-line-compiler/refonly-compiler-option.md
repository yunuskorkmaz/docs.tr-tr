---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 4093e98738cf6e41cd450229d82e3672fe9687ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788875"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="78905-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78905-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="78905-103">**- Refonly** seçeneği gösteren derlemenin birincil çıkışının yerine bir uygulama derlemeye bir başvuru bütünleştirilmiş kodu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78905-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="78905-104">`-refonly` Parametre sessiz bir şekilde devre dışı bırakır pdb, çıktısı olarak başvuru bütünleştirilmiş kodları yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="78905-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="78905-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78905-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="78905-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78905-106">Remarks</span></span>

<span data-ttu-id="78905-107">Visual Basic destekler `-refout` 15.3 sürümünden başlayarak geçin.</span><span class="sxs-lookup"><span data-stu-id="78905-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="78905-108">Başvuru bütünleştirilmiş kodları meta verileri ancak hiçbir uygulama kodu içeren yalnızca meta veri derlemelerdir.</span><span class="sxs-lookup"><span data-stu-id="78905-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="78905-109">Bunlar, anonim türler dışında her şeyi için tür ve üye bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="78905-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="78905-110">Kullanılmasının nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğünü doğrulama) geçirin.</span><span class="sxs-lookup"><span data-stu-id="78905-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="78905-111">Başvuru derlemelerini içeren bir derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="78905-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="78905-112">Bu özniteliği, kaynakta belirtilebilir (sonra derleyici bu sentezlemek gerekmez).</span><span class="sxs-lookup"><span data-stu-id="78905-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="78905-113">Bu öznitelik nedeniyle yürütme için başvuru derlemeleri yüklemeye çalışma zamanları reddeder (ancak bunlar yine de salt yansıma bir bağlamda yüklenmiş olabilir).</span><span class="sxs-lookup"><span data-stu-id="78905-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="78905-114">Bunlar salt yansıma olarak başvuru derlemelerini yüklemek emin olmak derlemelerini yansıtan araçları gerekir; Aksi takdirde, çalışma zamanı oluşturur bir <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="78905-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="78905-115">`-refonly` Ve [ `-refout` ](refout-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="78905-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="78905-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78905-116">See also</span></span>

- [<span data-ttu-id="78905-117">-refout</span><span class="sxs-lookup"><span data-stu-id="78905-117">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="78905-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="78905-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="78905-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="78905-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
