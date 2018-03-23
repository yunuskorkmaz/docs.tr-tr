---
title: -quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0ed08e013f088f512ae915daa9aeb2fa6b249b0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-quiet"></a><span data-ttu-id="4dd04-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="4dd04-102">-quiet</span></span>
<span data-ttu-id="4dd04-103">Derleyici sözdizimi ile ilgili hatalar ve Uyarılar için kod görüntülenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="4dd04-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4dd04-104">Syntax</span></span>  
  
```  
-quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="4dd04-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4dd04-105">Remarks</span></span>  
 <span data-ttu-id="4dd04-106">Varsayılan olarak, `-quiet` etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="4dd04-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="4dd04-107">Derleyici bir sözdizimi ile ilgili hata veya uyarı bildirdiğinde, ayrıca kaynak kod satırından çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4dd04-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="4dd04-108">Derleyici çıktı ayrıştırma uygulamalar için yalnızca Tanı metin çıktısı derleyici için daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4dd04-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="4dd04-109">Aşağıdaki örnekte, `Module1` olmadan derlendiğinde kaynak kodu içeren hata çıkarır `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="4dd04-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="4dd04-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="4dd04-110">Output:</span></span>  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 <span data-ttu-id="4dd04-111">Derlenmiş ile `-quiet`, yalnızca aşağıdaki derleyici çıkarır:</span><span class="sxs-lookup"><span data-stu-id="4dd04-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="4dd04-112">`-quiet` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4dd04-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dd04-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dd04-113">Example</span></span>  
 <span data-ttu-id="4dd04-114">Aşağıdaki kod derlerken `T2.vb` ve derleyici sözdizimi ile ilgili tanılama kodunu görüntülemez:</span><span class="sxs-lookup"><span data-stu-id="4dd04-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dd04-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4dd04-115">See Also</span></span>  
 [<span data-ttu-id="4dd04-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4dd04-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4dd04-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4dd04-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
