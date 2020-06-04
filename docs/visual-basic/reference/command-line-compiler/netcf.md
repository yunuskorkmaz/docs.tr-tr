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
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397481"
---
# <a name="-netcf"></a><span data-ttu-id="9b3a7-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="9b3a7-102">-netcf</span></span>

<span data-ttu-id="9b3a7-103">.NET Compact Framework hedeflemek için derleyiciyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b3a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b3a7-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="9b3a7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b3a7-105">Remarks</span></span>

<span data-ttu-id="9b3a7-106">`-netcf`Seçeneği, Visual Basic derleyicisinin tam .NET Framework yerine .NET Compact Framework hedeflemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="9b3a7-107">Yalnızca tam .NET Framework mevcut olan dil işlevselliği devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="9b3a7-108">`-netcf`Seçeneği [-SdkPath](sdkpath.md)ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-108">The `-netcf` option is designed to be used with [-sdkpath](sdkpath.md).</span></span> <span data-ttu-id="9b3a7-109">Tarafından devre dışı bırakılan dil özellikleri, `-netcf` ile hedeflenen dosyalarda mevcut olmayan dil özellikleridir `-sdkpath` .</span><span class="sxs-lookup"><span data-stu-id="9b3a7-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="9b3a7-110">`-netcf`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="9b3a7-111">`-netcf`Visual Basic bir cihaz projesi yüklendiğinde bu seçenek ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="9b3a7-112">`-netcf`Seçeneği aşağıdaki dil özelliklerini değiştirir:</span><span class="sxs-lookup"><span data-stu-id="9b3a7-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="9b3a7-113">Bir programın yürütülmesini sonlandıran [End \<keyword> deyimin](../../language-reference/statements/end-keyword-statement.md) anahtar sözcüğü devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-113">The [End \<keyword> Statement](../../language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="9b3a7-114">Aşağıdaki program, `-netcf` ile derleme zamanında derleyip çalışır, ancak başarısız olur `-netcf` .</span><span class="sxs-lookup"><span data-stu-id="9b3a7-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="9b3a7-115">Tüm formlarda geç bağlama devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="9b3a7-116">Derleme zamanı hataları, tanınan geç bağlama senaryolarıyla karşılaşıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="9b3a7-117">Aşağıdaki program, `-netcf` ile derleme zamanında derleyip çalışır, ancak başarısız olur `-netcf` .</span><span class="sxs-lookup"><span data-stu-id="9b3a7-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="9b3a7-118">[Auto](../../language-reference/modifiers/auto.md), [ANSI](../../language-reference/modifiers/ansi.md)ve [Unicode](../../language-reference/modifiers/unicode.md) değiştiricileri devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-118">The [Auto](../../language-reference/modifiers/auto.md), [Ansi](../../language-reference/modifiers/ansi.md), and [Unicode](../../language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="9b3a7-119">[Declare ifadesinin](../../language-reference/statements/declare-statement.md) sözdizimi de olarak değiştirilir `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` .</span><span class="sxs-lookup"><span data-stu-id="9b3a7-119">The syntax of the [Declare Statement](../../language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="9b3a7-120">Aşağıdaki kod, derleme üzerinde etkisini gösterir `-netcf` .</span><span class="sxs-lookup"><span data-stu-id="9b3a7-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="9b3a7-121">Visual Basic kaldırılmış Visual Basic 6,0 anahtar sözcüklerini kullanmak kullanıldığında farklı bir hata oluşturur `-netcf` .</span><span class="sxs-lookup"><span data-stu-id="9b3a7-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="9b3a7-122">Bu, aşağıdaki anahtar sözcüklerin hata iletilerini etkiler:</span><span class="sxs-lookup"><span data-stu-id="9b3a7-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="9b3a7-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b3a7-123">Example</span></span>

<span data-ttu-id="9b3a7-124">Aşağıdaki kod, `Myfile.vb` C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="9b3a7-125">Genellikle .NET Compact Framework en son sürümünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="9b3a7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b3a7-126">See also</span></span>

- [<span data-ttu-id="9b3a7-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9b3a7-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9b3a7-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="9b3a7-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="9b3a7-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="9b3a7-129">-sdkpath</span></span>](sdkpath.md)
