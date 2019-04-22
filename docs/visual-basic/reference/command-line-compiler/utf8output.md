---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 75369c3bcb19afbf98bfb80bc3e439f996d2a9d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833654"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="42707-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42707-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="42707-103">UTF-8 kodlaması kullanarak derleyici çıkışı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42707-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42707-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42707-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="42707-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="42707-105">Arguments</span></span>  
 <span data-ttu-id="42707-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="42707-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="42707-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="42707-107">Optional.</span></span> <span data-ttu-id="42707-108">Bu seçenek için varsayılan değer `-utf8output-`, derleyici çıkışını UTF-8 kodlamasını kullanmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="42707-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="42707-109">Belirtme `-utf8output` belirtmekle aynı `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="42707-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42707-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42707-110">Remarks</span></span>  
 <span data-ttu-id="42707-111">Bazı uluslararası yapılandırmalarında, derleyici çıkışını konsolunda doğru şekilde görüntülenemiyor.</span><span class="sxs-lookup"><span data-stu-id="42707-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="42707-112">Böyle durumlarda `-utf8output` ve derleyici çıkışı bir dosyaya yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="42707-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42707-113">`-utf8output` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="42707-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42707-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="42707-114">Example</span></span>  
 <span data-ttu-id="42707-115">Aşağıdaki kod derlenir `In.vb` ve görüntülemek için derleyicinin yönlendirir UTF-8 kodlaması kullanarak çıktı.</span><span class="sxs-lookup"><span data-stu-id="42707-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="42707-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42707-116">See also</span></span>

- [<span data-ttu-id="42707-117">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="42707-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="42707-118">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="42707-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
