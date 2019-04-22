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
ms.openlocfilehash: 2024ccadb06fdea0c24d9d304c2fe040f8cce1d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814334"
---
# <a name="-sdkpath"></a><span data-ttu-id="b8fe2-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="b8fe2-102">-sdkpath</span></span>
<span data-ttu-id="b8fe2-103">Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8fe2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8fe2-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="b8fe2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b8fe2-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="b8fe2-106">Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin derleme için kullanılacak sürümlerini içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="b8fe2-107">Bu yolu, yüklü olduğu kadar doğrulanmadı.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="b8fe2-108">Dizin adı tırnak içine alın ("") bir boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8fe2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8fe2-109">Remarks</span></span>  
 <span data-ttu-id="b8fe2-110">Bu seçenek, mscorlib.dll'nin ve Microsoft.VisualBasic.dll içinde dosyaları varsayılan olmayan bir konumdan yüklemek için Visual Basic Derleyicisi söyler.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="b8fe2-111">`-sdkpath` Seçeneği ile kullanılmak üzere tasarlanmış [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="b8fe2-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="b8fe2-112">[!INCLUDE[Compact](~/includes/compact-md.md)] Bunlardan farklı sürümlerini kullanan destek kitaplıklar türleri ve cihazlarda bulunamadı dil özellikleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8fe2-113">`-sdkpath` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="b8fe2-114">`-sdkpath` Seçeneği, Visual Basic cihaz projesi yüklendiğinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="b8fe2-115">Kullanarak derleyicinin Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlemelisiniz belirtebilirsiniz `-vbruntime` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="b8fe2-116">Daha fazla bilgi için [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="b8fe2-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8fe2-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8fe2-117">Example</span></span>  
 <span data-ttu-id="b8fe2-118">Aşağıdaki kod derlenir `Myfile.vb` ile [!INCLUDE[Compact](~/includes/compact-md.md)], mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin sürümlerini kullanarak varsayılan yükleme dizininde bulunan [!INCLUDE[Compact](~/includes/compact-md.md)] C sürücüsünde.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="b8fe2-119">Genellikle, en son sürümünü kullanın [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8fe2-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8fe2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8fe2-120">See also</span></span>

- [<span data-ttu-id="b8fe2-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b8fe2-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b8fe2-122">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b8fe2-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="b8fe2-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="b8fe2-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="b8fe2-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="b8fe2-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
