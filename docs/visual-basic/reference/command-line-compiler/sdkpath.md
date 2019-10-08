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
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004687"
---
# <a name="-sdkpath"></a><span data-ttu-id="4eafc-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="4eafc-102">-sdkpath</span></span>
<span data-ttu-id="4eafc-103">Mscorlib. dll ve Microsoft. VisualBasic. dll dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4eafc-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eafc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4eafc-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="4eafc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4eafc-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="4eafc-106">Derleme için kullanılacak mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="4eafc-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="4eafc-107">Bu yol, yükleninceye kadar doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="4eafc-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="4eafc-108">Dizin adını bir boşluk içeriyorsa tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="4eafc-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4eafc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4eafc-109">Remarks</span></span>  
 <span data-ttu-id="4eafc-110">Bu seçenek, Visual Basic derleyicisine mscorlib. dll ve Microsoft. VisualBasic. dll dosyalarını varsayılan olmayan bir konumdan yüklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="4eafc-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="4eafc-111">@No__t-0 seçeneği [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4eafc-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="4eafc-112">.NET Compact Framework, cihazlarda bulunmayan türlerin ve dil özelliklerinin kullanımını önlemek için bu destek kitaplıklarının farklı sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4eafc-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4eafc-113">@No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4eafc-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="4eafc-114">@No__t-0 seçeneği, bir Visual Basic cihaz projesi yüklendiğinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4eafc-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="4eafc-115">@No__t-0 derleyici seçeneğini kullanarak derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan derlenmesi gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4eafc-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="4eafc-116">Daha fazla bilgi için bkz. [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="4eafc-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4eafc-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4eafc-117">Example</span></span>  
 <span data-ttu-id="4eafc-118">Aşağıdaki kod, C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework `Myfile.vb` ' ı derler.</span><span class="sxs-lookup"><span data-stu-id="4eafc-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="4eafc-119">Genellikle .NET Compact Framework en son sürümünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4eafc-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4eafc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4eafc-120">See also</span></span>

- [<span data-ttu-id="4eafc-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4eafc-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4eafc-122">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4eafc-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="4eafc-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="4eafc-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="4eafc-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="4eafc-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
