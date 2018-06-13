---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: e67fe05507c8cb3edd7f46cad19211ba11e3b054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652402"
---
# <a name="-quiet"></a><span data-ttu-id="aeb2c-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="aeb2c-102">-quiet</span></span>
<span data-ttu-id="aeb2c-103">Derleyici sözdizimi ile ilgili hatalar ve Uyarılar için kod görüntülenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="aeb2c-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeb2c-104">Syntax</span></span>  
  
```  
-quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="aeb2c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeb2c-105">Remarks</span></span>  
 <span data-ttu-id="aeb2c-106">Varsayılan olarak, `-quiet` etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="aeb2c-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="aeb2c-107">Derleyici bir sözdizimi ile ilgili hata veya uyarı bildirdiğinde, ayrıca kaynak kod satırından çıkarır.</span><span class="sxs-lookup"><span data-stu-id="aeb2c-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="aeb2c-108">Derleyici çıktı ayrıştırma uygulamalar için yalnızca Tanı metin çıktısı derleyici için daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb2c-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="aeb2c-109">Aşağıdaki örnekte, `Module1` olmadan derlendiğinde kaynak kodu içeren hata çıkarır `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="aeb2c-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="aeb2c-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="aeb2c-110">Output:</span></span>  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 <span data-ttu-id="aeb2c-111">Derlenmiş ile `-quiet`, yalnızca aşağıdaki derleyici çıkarır:</span><span class="sxs-lookup"><span data-stu-id="aeb2c-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="aeb2c-112">`-quiet` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb2c-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb2c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeb2c-113">Example</span></span>  
 <span data-ttu-id="aeb2c-114">Aşağıdaki kod derlerken `T2.vb` ve derleyici sözdizimi ile ilgili tanılama kodunu görüntülemez:</span><span class="sxs-lookup"><span data-stu-id="aeb2c-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="aeb2c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb2c-115">See Also</span></span>  
 [<span data-ttu-id="aeb2c-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="aeb2c-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="aeb2c-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="aeb2c-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
