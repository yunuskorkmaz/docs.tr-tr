---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582867"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="649de-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="649de-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="649de-103">**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="649de-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="649de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="649de-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="649de-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="649de-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="649de-106">Başvuru derlemesinin yolu ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="649de-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="649de-107">Genellikle birincil derlemenin alt klasöründe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="649de-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="649de-108">Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="649de-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="649de-109">@No__t_0 tüm klasörler var olmalıdır; derleyici bunları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="649de-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="649de-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="649de-110">Remarks</span></span>

<span data-ttu-id="649de-111">Visual Basic, sürüm 15,3 ' den başlayarak `-refout` anahtarını destekler.</span><span class="sxs-lookup"><span data-stu-id="649de-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="649de-112">Başvuru derlemeleri yalnızca meta veri içeren derlemelerdir, ancak uygulama kodu yoktur.</span><span class="sxs-lookup"><span data-stu-id="649de-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="649de-113">Anonim türler hariç her şey için tür ve üye bilgilerini içerirler.</span><span class="sxs-lookup"><span data-stu-id="649de-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="649de-114">Yöntem gövdeleri tek bir `throw null` ifadesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="649de-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="649de-115">@No__t_0 yöntemi gövdelerini kullanmanın nedeni (gövdeden farklı olarak), PEVerify 'ın çalıştırılabilmesi ve geçebilmesi (Bu nedenle meta verilerin tamamlanmasının doğrulanması).</span><span class="sxs-lookup"><span data-stu-id="649de-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="649de-116">Başvuru derlemeleri derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="649de-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="649de-117">Bu öznitelik kaynakta belirtilebilir (derleyicinin onu birleştirmesini gerektirmez).</span><span class="sxs-lookup"><span data-stu-id="649de-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="649de-118">Bu öznitelik nedeniyle, çalışma zamanları yürütme için başvuru derlemelerini yüklemeyi reddeder (ancak yine de yalnızca bir yansıma bağlamına yüklenebilirler).</span><span class="sxs-lookup"><span data-stu-id="649de-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="649de-119">Derlemeler üzerinde yansıtan araçların başvuru derlemelerini yalnızca yansıma olarak yüklediklerinden emin olunması gerekir; Aksi takdirde, çalışma zamanı bir <xref:System.BadImageFormatException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649de-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="649de-120">@No__t_0 ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="649de-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="649de-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="649de-121">See also</span></span>

- [<span data-ttu-id="649de-122">-refonly</span><span class="sxs-lookup"><span data-stu-id="649de-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="649de-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="649de-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="649de-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="649de-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
