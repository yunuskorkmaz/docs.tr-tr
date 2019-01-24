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
ms.openlocfilehash: 069514b4beed7f6fbc1d53e0b2fa5d9c6af8b1af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665961"
---
# <a name="-netcf"></a><span data-ttu-id="32007-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="32007-102">-netcf</span></span>
<span data-ttu-id="32007-103">Derleyicinin hedef ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32007-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32007-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32007-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="32007-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32007-105">Remarks</span></span>  
 <span data-ttu-id="32007-106">`-netcf` Seçeneği neden olur, Visual Basic Derleyicisi hedef [!INCLUDE[Compact](~/includes/compact-md.md)] tam yerine [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32007-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="32007-107">Yalnızca tam olarak mevcut olan dil işlevleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="32007-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="32007-108">`-netcf` Seçeneği ile kullanılmak üzere tasarlanmıştır [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="32007-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="32007-109">Devre dışı dil özellikleri `-netcf` aynı dil özellikleri ile hedeflenen dosyalarda mevcut olan `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="32007-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32007-110">`-netcf` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="32007-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="32007-111">`-netcf` Seçeneği, Visual Basic cihaz projesi yüklendiğinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="32007-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="32007-112">`-netcf` Seçeneği aşağıdaki dil özellikleri değiştirir:</span><span class="sxs-lookup"><span data-stu-id="32007-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="32007-113">[Son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) anahtar sözcüğü bir programın yürütülmesini sonlandıran, devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="32007-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="32007-114">Aşağıdaki programın olmadan çalışır ve `-netcf` ile derleme zamanında başarısız olduğunda `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="32007-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="32007-115">Geç bağlama, tüm formları içinde devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="32007-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="32007-116">Tanınan geç bağlama senaryoları karşılaştı, derleme zamanı hatalarına üretilir.</span><span class="sxs-lookup"><span data-stu-id="32007-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="32007-117">Aşağıdaki programın olmadan çalışır ve `-netcf` ile derleme zamanında başarısız olduğunda `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="32007-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="32007-118">[Otomatik](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md), ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiriciler devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="32007-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="32007-119">Söz dizimi [Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) deyimi için değişiklik de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="32007-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="32007-120">Aşağıdaki kod etkisini gösterir `-netcf` bir derleme üzerinde.</span><span class="sxs-lookup"><span data-stu-id="32007-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="32007-121">Visual Basic kaldırılan Visual Basic 6.0 anahtar sözcüklerini kullanarak, farklı bir hata oluşturur, `-netcf` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32007-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="32007-122">Bu, aşağıdaki anahtar sözcükler için hata iletileri etkiler:</span><span class="sxs-lookup"><span data-stu-id="32007-122">This affects the error messages for the following keywords:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="32007-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="32007-123">Example</span></span>  
 <span data-ttu-id="32007-124">Aşağıdaki kod derlenir `Myfile.vb` ile [!INCLUDE[Compact](~/includes/compact-md.md)], mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin sürümlerini kullanarak varsayılan yükleme dizininde bulunan [!INCLUDE[Compact](~/includes/compact-md.md)] C sürücüsünde.</span><span class="sxs-lookup"><span data-stu-id="32007-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="32007-125">Genellikle, en son sürümünü kullanın [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32007-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="32007-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32007-126">See also</span></span>
- [<span data-ttu-id="32007-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="32007-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="32007-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="32007-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="32007-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="32007-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
