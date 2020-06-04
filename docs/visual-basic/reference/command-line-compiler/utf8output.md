---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403063"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="2974c-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2974c-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="2974c-103">UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2974c-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2974c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2974c-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2974c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2974c-105">Arguments</span></span>  
 <span data-ttu-id="2974c-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="2974c-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2974c-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2974c-107">Optional.</span></span> <span data-ttu-id="2974c-108">Bu seçenek için varsayılan değer, `-utf8output-` derleyici ÇıKıŞıNıN UTF-8 kodlamasını kullanmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2974c-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="2974c-109">Belirtmek, `-utf8output` belirtilerek aynı olur `-utf8output+` .</span><span class="sxs-lookup"><span data-stu-id="2974c-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2974c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2974c-110">Remarks</span></span>  
 <span data-ttu-id="2974c-111">Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez.</span><span class="sxs-lookup"><span data-stu-id="2974c-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="2974c-112">Bu gibi durumlarda, `-utf8output` derleyici çıkışını kullanın ve bir dosyaya yeniden yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="2974c-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2974c-113">`-utf8output`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2974c-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2974c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="2974c-114">Example</span></span>  
 <span data-ttu-id="2974c-115">Aşağıdaki kod derlenir `In.vb` ve DERLEYICININ UTF-8 kodlamasını kullanarak çıktıyı görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2974c-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2974c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2974c-116">See also</span></span>

- [<span data-ttu-id="2974c-117">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2974c-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2974c-118">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2974c-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
