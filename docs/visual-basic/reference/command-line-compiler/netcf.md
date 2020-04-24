---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 7f14ce07a2928f4dbffd3aa57f8cdd514b75694c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716711"
---
# <a name="-netcf"></a><span data-ttu-id="74397-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="74397-102">-netcf</span></span>

<span data-ttu-id="74397-103">.NET Compact Framework hedeflemek için derleyiciyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="74397-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="74397-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74397-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="74397-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74397-105">Remarks</span></span>

<span data-ttu-id="74397-106">Seçeneği `-netcf` , Visual Basic derleyicisinin tam .NET Framework yerine .NET Compact Framework hedeflemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="74397-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="74397-107">Yalnızca tam .NET Framework mevcut olan dil işlevselliği devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="74397-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="74397-108">`-netcf` Seçeneği [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="74397-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="74397-109">Tarafından `-netcf` devre dışı bırakılan dil özellikleri, ile `-sdkpath`hedeflenen dosyalarda mevcut olmayan dil özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="74397-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="74397-110">Bu `-netcf` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74397-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="74397-111">Visual Basic `-netcf` bir cihaz projesi yüklendiğinde bu seçenek ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="74397-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="74397-112">`-netcf` Seçeneği aşağıdaki dil özelliklerini değiştirir:</span><span class="sxs-lookup"><span data-stu-id="74397-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="74397-113">Bir programın yürütülmesini sonlandıran [End \<anahtar sözcüğü> deyimin](../../../visual-basic/language-reference/statements/end-keyword-statement.md) anahtar sözcüğü devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="74397-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="74397-114">Aşağıdaki program, ile `-netcf` `-netcf`derleme zamanında derleyip çalışır, ancak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="74397-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="74397-115">Tüm formlarda geç bağlama devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="74397-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="74397-116">Derleme zamanı hataları, tanınan geç bağlama senaryolarıyla karşılaşıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="74397-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="74397-117">Aşağıdaki program, ile `-netcf` `-netcf`derleme zamanında derleyip çalışır, ancak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="74397-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="74397-118">[Auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiricileri devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="74397-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="74397-119">[Declare ifadesinin](../../../visual-basic/language-reference/statements/declare-statement.md) sözdizimi de olarak `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="74397-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="74397-120">Aşağıdaki kod, derleme `-netcf` üzerinde etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="74397-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="74397-121">Visual Basic kaldırılmış Visual Basic 6,0 anahtar sözcüklerini kullanmak kullanıldığında farklı bir hata `-netcf` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74397-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="74397-122">Bu, aşağıdaki anahtar sözcüklerin hata iletilerini etkiler:</span><span class="sxs-lookup"><span data-stu-id="74397-122">This affects the error messages for the following keywords:</span></span>

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a><span data-ttu-id="74397-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="74397-123">Example</span></span>

<span data-ttu-id="74397-124">Aşağıdaki kod, C `Myfile.vb` sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="74397-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="74397-125">Genellikle .NET Compact Framework en son sürümünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="74397-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="74397-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74397-126">See also</span></span>

- [<span data-ttu-id="74397-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="74397-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="74397-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="74397-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="74397-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="74397-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
