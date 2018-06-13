---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654771"
---
# <a name="-sdkpath"></a><span data-ttu-id="60543-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="60543-102">-sdkpath</span></span>
<span data-ttu-id="60543-103">Mscorlib.dll ve Microsoft.VisualBasic.dll içinde konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="60543-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60543-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60543-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="60543-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="60543-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="60543-106">Mscorlib.dll ve derleme için kullanılacak Microsoft.VisualBasic.dll içinde sürümleri içeren dizini.</span><span class="sxs-lookup"><span data-stu-id="60543-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="60543-107">Bunu yüklenene kadar bu yolu doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="60543-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="60543-108">Dizin adı tırnak işaretleri içine alın ("") boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="60543-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60543-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60543-109">Remarks</span></span>  
 <span data-ttu-id="60543-110">Bu seçenek varsayılan olmayan konumdan mscorlib.dll ve Microsoft.VisualBasic.dll içinde dosyaları yüklemek için Visual Basic derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="60543-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="60543-111">`-sdkpath` Seçeneği ile kullanılmak üzere tasarlanmış [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="60543-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="60543-112">[!INCLUDE[Compact](~/includes/compact-md.md)] Bunlardan farklı sürümlerini kullanan destek kitaplıkları türleri ve farklı dil özelliklerini cihazlarda bulunamadı kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="60543-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60543-113">`-sdkpath` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60543-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="60543-114">`-sdkpath` Seçeneği, bir Visual Basic cihaz projesi yüklendiğinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="60543-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="60543-115">Derleyici Visual Basic çalışma zamanı kitaplığı başvurusu olmadan kullanarak derleme belirtebilirsiniz `-vbruntime` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="60543-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="60543-116">Daha fazla bilgi için bkz: [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="60543-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60543-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="60543-117">Example</span></span>  
 <span data-ttu-id="60543-118">Aşağıdaki kod derlerken `Myfile.vb` ile [!INCLUDE[Compact](~/includes/compact-md.md)], Mscorlib.dll ve Microsoft.VisualBasic.dll içinde sürümleri kullanılarak varsayılan yükleme dizininde bulunan [!INCLUDE[Compact](~/includes/compact-md.md)] C sürücüsünde.</span><span class="sxs-lookup"><span data-stu-id="60543-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="60543-119">Genellikle, en son sürümünü kullanmak [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60543-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="60543-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60543-120">See Also</span></span>  
 [<span data-ttu-id="60543-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="60543-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="60543-122">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="60543-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="60543-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="60543-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="60543-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="60543-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
