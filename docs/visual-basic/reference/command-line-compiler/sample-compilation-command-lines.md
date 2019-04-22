---
title: Örnek Derleme Komut Satırları (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824317"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="a8be1-102">Örnek derleme komut satırları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8be1-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="a8be1-103">Visual Studio içinde Visual Basic programlarından derleme alternatif olarak, yürütülebilir (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyaları üretmek için komut satırından derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8be1-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="a8be1-104">Visual Basic komut satırı derleyicisi giriş denetleyen ve dosyaları, derlemeleri ve hata ayıklama ve önişlemci seçenekleri çıkış seçenekleri eksiksiz bir kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="a8be1-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="a8be1-105">Her seçenek birbirinin yerine iki biçimde kullanılabilir: `-option` ve `/option`.</span><span class="sxs-lookup"><span data-stu-id="a8be1-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="a8be1-106">Bu belgelerde yalnızca `-option` formu.</span><span class="sxs-lookup"><span data-stu-id="a8be1-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="a8be1-107">Aşağıdaki tabloda bazı örnek komut satırları, kendi kullanımınız için değiştirebileceğiniz listeler.</span><span class="sxs-lookup"><span data-stu-id="a8be1-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="a8be1-108">Bitiş</span><span class="sxs-lookup"><span data-stu-id="a8be1-108">To</span></span>|<span data-ttu-id="a8be1-109">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="a8be1-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="a8be1-110">File.vb derleyin ve File.exe oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8be1-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="a8be1-111">File.vb derleyin ve File.dll oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8be1-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="a8be1-112">File.vb derleyin ve My.exe oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8be1-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="a8be1-113">File.vb derlemek ve bir kitaplık hem File.dll adlı bir başvuru bütünleştirilmiş kodu oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8be1-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="a8be1-114">Geçerli dizindeki iyileştirmeler tüm Visual Basic dosyaları üzerinde derleyin ve `DEBUG` tanımlanmış sembol File2.exe üretme</span><span class="sxs-lookup"><span data-stu-id="a8be1-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="a8be1-115">Geçerli dizindeki logosu veya uyarıları görüntülemeden File2.dll hata ayıklama sürümü oluşturan tüm Visual Basic dosyaları derleme</span><span class="sxs-lookup"><span data-stu-id="a8be1-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="a8be1-116">Something.dll geçerli dizindeki tüm Visual Basic dosyaları derleme</span><span class="sxs-lookup"><span data-stu-id="a8be1-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="a8be1-117">Visual Studio IDE kullanarak bir proje oluşturduğunuzda, ilişkili bilgileri görüntüleyebilir **vbc** çıktı penceresinde, derleyici seçenekleri ile komutu.</span><span class="sxs-lookup"><span data-stu-id="a8be1-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="a8be1-118">Bu bilgileri görüntülemek için Aç [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)ve ardından **MSBuild proje oluşturması çıkış ayrıntısı** için **Normal** veya daha yüksek bir ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="a8be1-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="a8be1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8be1-119">See also</span></span>

- [<span data-ttu-id="a8be1-120">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a8be1-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a8be1-121">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="a8be1-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
