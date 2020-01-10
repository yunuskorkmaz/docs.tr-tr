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
# <a name="-netcf"></a><span data-ttu-id="c0c19-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="c0c19-102">-netcf</span></span>

<span data-ttu-id="c0c19-103">.NET Compact Framework hedeflemek için derleyiciyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c0c19-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0c19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0c19-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="c0c19-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0c19-105">Remarks</span></span>

<span data-ttu-id="c0c19-106">`-netcf` seçeneği, Visual Basic derleyicinin tam .NET Framework yerine .NET Compact Framework hedeflemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0c19-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="c0c19-107">Yalnızca tam .NET Framework mevcut olan dil işlevselliği devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c0c19-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="c0c19-108">`-netcf` seçeneği [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c0c19-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="c0c19-109">`-netcf` tarafından devre dışı bırakılan dil özellikleri, `-sdkpath`hedeflenen dosyalarda bulunmayan dil özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="c0c19-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="c0c19-110">`-netcf` seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0c19-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="c0c19-111">`-netcf` seçeneği, bir Visual Basic cihaz projesi yüklendiğinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c0c19-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="c0c19-112">`-netcf` seçeneği aşağıdaki dil özelliklerini değiştirir:</span><span class="sxs-lookup"><span data-stu-id="c0c19-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="c0c19-113">Bir programın yürütülmesini sonlandıran [End \<anahtar sözcüğü > deyimin](../../../visual-basic/language-reference/statements/end-keyword-statement.md) anahtar sözcüğü devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c0c19-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="c0c19-114">Aşağıdaki program `-netcf` olmadan derlenir ve çalışır, ancak `-netcf`ile derleme zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c0c19-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="c0c19-115">Tüm formlarda geç bağlama devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c0c19-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="c0c19-116">Derleme zamanı hataları, tanınan geç bağlama senaryolarıyla karşılaşıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c0c19-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="c0c19-117">Aşağıdaki program `-netcf` olmadan derlenir ve çalışır, ancak `-netcf`ile derleme zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c0c19-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="c0c19-118">[Auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiricileri devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c0c19-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="c0c19-119">[Declare ifadesinin](../../../visual-basic/language-reference/statements/declare-statement.md) sözdizimi de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c0c19-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="c0c19-120">Aşağıdaki kod bir derlemede `-netcf` etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0c19-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="c0c19-121">Visual Basic kaldırılmış Visual Basic 6,0 anahtar sözcüklerini kullanmak `-netcf` kullanıldığında farklı bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="c0c19-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="c0c19-122">Bu, aşağıdaki anahtar sözcüklerin hata iletilerini etkiler:</span><span class="sxs-lookup"><span data-stu-id="c0c19-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="c0c19-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0c19-123">Example</span></span>

<span data-ttu-id="c0c19-124">Aşağıdaki kod, C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework `Myfile.vb` derler.</span><span class="sxs-lookup"><span data-stu-id="c0c19-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="c0c19-125">Genellikle .NET Compact Framework en son sürümünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c0c19-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="c0c19-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0c19-126">See also</span></span>

- [<span data-ttu-id="c0c19-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c0c19-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c0c19-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c0c19-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="c0c19-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="c0c19-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
