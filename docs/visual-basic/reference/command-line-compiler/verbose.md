---
title: -verbose
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0523409e53a8c7ea34de7dcc24b1bce2885a183
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-verbose"></a><span data-ttu-id="a5ca8-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="a5ca8-102">-verbose</span></span>
<span data-ttu-id="a5ca8-103">Ayrıntılı durum ve hata iletilerine neden derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ca8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5ca8-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5ca8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5ca8-105">Arguments</span></span>  
 <span data-ttu-id="a5ca8-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a5ca8-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a5ca8-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-107">Optional.</span></span> <span data-ttu-id="a5ca8-108">Belirtme `-verbose` belirtme aynı `-verbose+`, ayrıntılı iletiler yaymak üzere derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="a5ca8-109">Bu seçenek için varsayılan değer `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5ca8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5ca8-110">Remarks</span></span>  
 <span data-ttu-id="a5ca8-111">`-verbose` Seçeneği derleyici tarafından verilen hatalarının toplam sayısını hakkında bilgi, bir modül tarafından hangi derlemelerin yüklenen raporları ve hangi dosyaların şu anda derlenmiş görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5ca8-112">`-verbose` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ca8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5ca8-113">Example</span></span>  
 <span data-ttu-id="a5ca8-114">Aşağıdaki kod derlerken `In.vb` ve ayrıntılı durum bilgilerini görüntülemek için derleyici yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5ca8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5ca8-115">See Also</span></span>  
 [<span data-ttu-id="a5ca8-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a5ca8-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a5ca8-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a5ca8-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
