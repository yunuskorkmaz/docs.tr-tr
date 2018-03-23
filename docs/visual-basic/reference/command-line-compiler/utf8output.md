---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f90b39046aebe0cd15c7e033d8e588045491f7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="cb2f6-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb2f6-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="cb2f6-103">UTF-8 kodlaması kullanarak derleyici çıkışı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb2f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb2f6-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cb2f6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cb2f6-105">Arguments</span></span>  
 <span data-ttu-id="cb2f6-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="cb2f6-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="cb2f6-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-107">Optional.</span></span> <span data-ttu-id="cb2f6-108">Bu seçenek için varsayılan değer `-utf8output-`, yani Derleyici çıktısı UTF-8 kodlaması kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="cb2f6-109">Belirtme `-utf8output` belirtme aynı `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb2f6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb2f6-110">Remarks</span></span>  
 <span data-ttu-id="cb2f6-111">Uluslararası bazı yapılandırmalarda Derleyici çıktısı doğru konsolda görüntülenemiyor.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="cb2f6-112">Bu gibi durumlarda kullanmak `-utf8output` ve Derleyici çıktısı bir dosyaya yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb2f6-113">`-utf8output` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb2f6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb2f6-114">Example</span></span>  
 <span data-ttu-id="cb2f6-115">Aşağıdaki kod derlerken `In.vb` ve görüntülemek için derleyici yönlendirir UTF-8 kodlaması kullanarak çıktı.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb2f6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb2f6-116">See Also</span></span>  
 [<span data-ttu-id="cb2f6-117">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="cb2f6-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cb2f6-118">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="cb2f6-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
