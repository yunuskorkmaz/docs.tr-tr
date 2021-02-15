---
description: Hakkında daha fazla bilgi edinin:-verbose
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: ea222d4f284bcaf163b142269fe250a081b0ee4f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470142"
---
# <a name="-verbose"></a><span data-ttu-id="824a0-103">-verbose</span><span class="sxs-lookup"><span data-stu-id="824a0-103">-verbose</span></span>

<span data-ttu-id="824a0-104">Derleyicinin ayrıntılı durum ve hata iletileri oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="824a0-104">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="824a0-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="824a0-105">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="824a0-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="824a0-106">Arguments</span></span>  

 <span data-ttu-id="824a0-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="824a0-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="824a0-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="824a0-108">Optional.</span></span> <span data-ttu-id="824a0-109">Belirtme, `-verbose` `-verbose+` derleyicinin ayrıntılı iletiler yaymasına neden olan, belirtilerek aynı şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="824a0-109">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="824a0-110">Bu seçenek için varsayılan değer `-verbose-` .</span><span class="sxs-lookup"><span data-stu-id="824a0-110">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="824a0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="824a0-111">Remarks</span></span>  

 <span data-ttu-id="824a0-112">`-verbose`Seçeneği derleyici tarafından verilen toplam hata sayısı, bir modül tarafından hangi derlemelerin yüklendiğini raporlar ve şu anda derlenen dosyaları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="824a0-112">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="824a0-113">`-verbose`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="824a0-113">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="824a0-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="824a0-114">Example</span></span>  

 <span data-ttu-id="824a0-115">Aşağıdaki kod derlenir `In.vb` ve derleyicinin ayrıntılı durum bilgilerini görüntülemesi için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="824a0-115">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="824a0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="824a0-116">See also</span></span>

- [<span data-ttu-id="824a0-117">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="824a0-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="824a0-118">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="824a0-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
