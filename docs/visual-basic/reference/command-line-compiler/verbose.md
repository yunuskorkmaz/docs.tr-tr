---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004981"
---
# <a name="-verbose"></a><span data-ttu-id="819ba-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="819ba-102">-verbose</span></span>
<span data-ttu-id="819ba-103">Derleyicinin ayrıntılı durum ve hata iletileri oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="819ba-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="819ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="819ba-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="819ba-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="819ba-105">Arguments</span></span>  
 <span data-ttu-id="819ba-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="819ba-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="819ba-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="819ba-107">Optional.</span></span> <span data-ttu-id="819ba-108">Belirtme `-verbose` , derleyicinin ayrıntılı iletiler yaymasına neden olan, belirtilerek `-verbose+`aynı şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="819ba-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="819ba-109">Bu seçenek için varsayılan değer `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="819ba-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="819ba-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="819ba-110">Remarks</span></span>  
 <span data-ttu-id="819ba-111">`-verbose` Seçeneği derleyici tarafından verilen toplam hata sayısı, bir modül tarafından hangi derlemelerin yüklendiğini raporlar ve şu anda derlenen dosyaları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="819ba-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="819ba-112">Bu `-verbose` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="819ba-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="819ba-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="819ba-113">Example</span></span>  
 <span data-ttu-id="819ba-114">Aşağıdaki kod derlenir `In.vb` ve derleyicinin ayrıntılı durum bilgilerini görüntülemesi için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="819ba-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="819ba-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="819ba-115">See also</span></span>

- [<span data-ttu-id="819ba-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="819ba-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="819ba-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="819ba-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
