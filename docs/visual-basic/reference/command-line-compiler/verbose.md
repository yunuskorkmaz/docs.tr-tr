---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: f6d896fb0d41a8fa3ed613d29bc3fca2bd14cc5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832800"
---
# <a name="-verbose"></a><span data-ttu-id="88cae-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="88cae-102">-verbose</span></span>
<span data-ttu-id="88cae-103">Ayrıntılı durum ve hata iletileri oluşturmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="88cae-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88cae-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="88cae-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="88cae-105">Arguments</span></span>  
 <span data-ttu-id="88cae-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="88cae-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="88cae-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="88cae-107">Optional.</span></span> <span data-ttu-id="88cae-108">Belirtme `-verbose` belirtmekle aynı `-verbose+`, ayrıntılı iletiler dönüştüğünde derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="88cae-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="88cae-109">Bu seçenek için varsayılan değer `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="88cae-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88cae-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88cae-110">Remarks</span></span>  
 <span data-ttu-id="88cae-111">`-verbose` Seçeneği derleyici tarafından verilen hatalarının toplam sayısını hakkında bilgi, hangi derlemelerin modülü tarafından yüklenen raporları ve hangi dosyaların şu anda derlenen görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cae-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88cae-112">`-verbose` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88cae-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88cae-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="88cae-113">Example</span></span>  
 <span data-ttu-id="88cae-114">Aşağıdaki kod derlenir `In.vb` ve ayrıntılı durum bilgilerini görüntülemek için derleyicinin yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="88cae-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="88cae-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88cae-115">See also</span></span>

- [<span data-ttu-id="88cae-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="88cae-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="88cae-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="88cae-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
