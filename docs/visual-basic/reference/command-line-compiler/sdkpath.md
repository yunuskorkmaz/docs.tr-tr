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
ms.openlocfilehash: 85aba17b330af1b25b39f462844bc1a4856a448a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403115"
---
# <a name="-sdkpath"></a><span data-ttu-id="9c8bf-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="9c8bf-102">-sdkpath</span></span>
<span data-ttu-id="9c8bf-103">Mscorlib. dll ve Microsoft. VisualBasic. dll dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c8bf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9c8bf-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="9c8bf-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="9c8bf-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="9c8bf-106">Derleme için kullanılacak mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="9c8bf-107">Bu yol, yükleninceye kadar doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="9c8bf-108">Dizin adını bir boşluk içeriyorsa tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c8bf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c8bf-109">Remarks</span></span>  
 <span data-ttu-id="9c8bf-110">Bu seçenek, Visual Basic derleyicisine mscorlib. dll ve Microsoft. VisualBasic. dll dosyalarını varsayılan olmayan bir konumdan yüklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="9c8bf-111">`-sdkpath`Seçeneği [-netcf](netcf.md)ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-111">The `-sdkpath` option was designed to be used with [-netcf](netcf.md).</span></span> <span data-ttu-id="9c8bf-112">.NET Compact Framework, cihazlarda bulunmayan türlerin ve dil özelliklerinin kullanımını önlemek için bu destek kitaplıklarının farklı sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c8bf-113">`-sdkpath`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="9c8bf-114">`-sdkpath`Visual Basic bir cihaz projesi yüklendiğinde bu seçenek ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="9c8bf-115">Derleyicinin derleyici seçeneğini kullanarak Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlenmesi gerektiğini belirtebilirsiniz `-vbruntime` .</span><span class="sxs-lookup"><span data-stu-id="9c8bf-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="9c8bf-116">Daha fazla bilgi için bkz. [-vbruntime](vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="9c8bf-116">For more information, see [-vbruntime](vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c8bf-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c8bf-117">Example</span></span>  
 <span data-ttu-id="9c8bf-118">Aşağıdaki kod, `Myfile.vb` C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="9c8bf-119">Genellikle .NET Compact Framework en son sürümünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c8bf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c8bf-120">See also</span></span>

- [<span data-ttu-id="9c8bf-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9c8bf-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9c8bf-122">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="9c8bf-122">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="9c8bf-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="9c8bf-123">-netcf</span></span>](netcf.md)
- [<span data-ttu-id="9c8bf-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="9c8bf-124">-vbruntime</span></span>](vbruntime.md)
