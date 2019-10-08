---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004660"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="af1c8-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af1c8-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="af1c8-103">UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="af1c8-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af1c8-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="af1c8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="af1c8-105">Arguments</span></span>  
 <span data-ttu-id="af1c8-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="af1c8-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="af1c8-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="af1c8-107">Optional.</span></span> <span data-ttu-id="af1c8-108">Bu seçenek için varsayılan değer `-utf8output-` ' dır. Bu, derleyici çıkışının UTF-8 kodlaması kullanmaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="af1c8-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="af1c8-109">@No__t-0 belirtildiğinde `-utf8output+` belirtilerek aynı olur.</span><span class="sxs-lookup"><span data-stu-id="af1c8-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af1c8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af1c8-110">Remarks</span></span>  
 <span data-ttu-id="af1c8-111">Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez.</span><span class="sxs-lookup"><span data-stu-id="af1c8-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="af1c8-112">Bu gibi durumlarda, `-utf8output` ' ı kullanın ve derleyici çıkışını bir dosyaya yeniden yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="af1c8-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af1c8-113">@No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af1c8-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af1c8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="af1c8-114">Example</span></span>  
 <span data-ttu-id="af1c8-115">Aşağıdaki kod `In.vb` derler ve derleyiciyi UTF-8 kodlaması kullanarak çıktıyı görüntüleyecek şekilde yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="af1c8-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="af1c8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af1c8-116">See also</span></span>

- [<span data-ttu-id="af1c8-117">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="af1c8-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="af1c8-118">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="af1c8-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
