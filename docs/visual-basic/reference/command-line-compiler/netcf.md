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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36b2cba14f15cebdcc7f371f53f46b657ab12758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655778"
---
# <a name="-netcf"></a><span data-ttu-id="ab46c-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="ab46c-102">-netcf</span></span>
<span data-ttu-id="ab46c-103">Hedefe derleyici ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab46c-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab46c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab46c-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="ab46c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab46c-105">Remarks</span></span>  
 <span data-ttu-id="ab46c-106">`-netcf` Seçeneği neden hedef için Visual Basic derleyici [!INCLUDE[Compact](~/includes/compact-md.md)] tam yerine [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab46c-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="ab46c-107">Yalnızca tam olarak mevcut dil işlevleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="ab46c-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="ab46c-108">`-netcf` Seçeneği ile kullanılmak üzere tasarlanmıştır [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="ab46c-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="ab46c-109">Devre dışı dil özellikleri `-netcf` aynı dil özellikleri ile hedeflenen dosyalarında yok `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="ab46c-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab46c-110">`-netcf` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab46c-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="ab46c-111">`-netcf` Seçeneği, bir Visual Basic cihaz projesi yüklendiğinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ab46c-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="ab46c-112">`-netcf` Seçenek aşağıdaki dil özellikleri değiştirir:</span><span class="sxs-lookup"><span data-stu-id="ab46c-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="ab46c-113">[Son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) bir programın yürütülmesini sonlandırır, anahtar sözcüğü devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="ab46c-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="ab46c-114">Aşağıdaki programı derlenir ve olmadan çalışır `-netcf` ancak derleme zamanında başarısız `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="ab46c-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="ab46c-115">Geç bağlama, tüm formlarında devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="ab46c-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="ab46c-116">Tanınan geç bağlama senaryoları karşılaşılırsa, derleme zamanı hataları üretilir.</span><span class="sxs-lookup"><span data-stu-id="ab46c-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="ab46c-117">Aşağıdaki programı derlenir ve olmadan çalışır `-netcf` ancak derleme zamanında başarısız `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="ab46c-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="ab46c-118">[Otomatik](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md), ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiricileri devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="ab46c-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="ab46c-119">Söz dizimi [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) deyimi için değişiklik de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="ab46c-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="ab46c-120">Aşağıdaki kod etkisini gösterir `-netcf` bir derleme üzerinde.</span><span class="sxs-lookup"><span data-stu-id="ab46c-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="ab46c-121">Visual Basic'ten kaldırıldı Visual Basic 6.0 anahtar sözcükleri kullanarak farklı bir hata oluşturur, `-netcf` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab46c-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="ab46c-122">Bu, aşağıdaki anahtar sözcükler için hata iletileri etkiler:</span><span class="sxs-lookup"><span data-stu-id="ab46c-122">This affects the error messages for the following keywords:</span></span>  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a><span data-ttu-id="ab46c-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab46c-123">Example</span></span>  
 <span data-ttu-id="ab46c-124">Aşağıdaki kod derlerken `Myfile.vb` ile [!INCLUDE[Compact](~/includes/compact-md.md)], mscorlib.dll ve Microsoft.VisualBasic.dll içinde sürümleri kullanılarak varsayılan yükleme dizininde bulunan [!INCLUDE[Compact](~/includes/compact-md.md)] C sürücüsünde.</span><span class="sxs-lookup"><span data-stu-id="ab46c-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="ab46c-125">Genellikle, en son sürümünü kullanmak [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab46c-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab46c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab46c-126">See Also</span></span>  
 [<span data-ttu-id="ab46c-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ab46c-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ab46c-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ab46c-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="ab46c-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="ab46c-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
