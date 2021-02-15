---
description: Hakkında daha fazla bilgi edinin:-utf8output (Visual Basic)
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 317c1be3f18150ae88bb8e95927d9f5faf0e4f3c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461898"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="d45a2-103">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d45a2-103">-utf8output (Visual Basic)</span></span>

<span data-ttu-id="d45a2-104">UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d45a2-104">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d45a2-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d45a2-105">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d45a2-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="d45a2-106">Arguments</span></span>  

 <span data-ttu-id="d45a2-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d45a2-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d45a2-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d45a2-108">Optional.</span></span> <span data-ttu-id="d45a2-109">Bu seçenek için varsayılan değer, `-utf8output-` derleyici ÇıKıŞıNıN UTF-8 kodlamasını kullanmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d45a2-109">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="d45a2-110">Belirtmek, `-utf8output` belirtilerek aynı olur `-utf8output+` .</span><span class="sxs-lookup"><span data-stu-id="d45a2-110">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d45a2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d45a2-111">Remarks</span></span>  

 <span data-ttu-id="d45a2-112">Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez.</span><span class="sxs-lookup"><span data-stu-id="d45a2-112">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="d45a2-113">Bu gibi durumlarda, `-utf8output` derleyici çıkışını kullanın ve bir dosyaya yeniden yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="d45a2-113">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d45a2-114">`-utf8output`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d45a2-114">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d45a2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d45a2-115">Example</span></span>  

 <span data-ttu-id="d45a2-116">Aşağıdaki kod derlenir `In.vb` ve DERLEYICININ UTF-8 kodlamasını kullanarak çıktıyı görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d45a2-116">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d45a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d45a2-117">See also</span></span>

- [<span data-ttu-id="d45a2-118">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d45a2-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d45a2-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d45a2-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
