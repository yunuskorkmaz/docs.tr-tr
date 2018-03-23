---
title: Örnek Derleme Komut Satırları (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf20e2916efd2eb10065be22c319e34ddb2bda9a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="66db9-102">Örnek derleme komut satırları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66db9-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="66db9-103">Visual Basic programları içinden derleme alternatif olarak [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], yürütülebilir dosyanın (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyaları üretmek için komut satırından derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66db9-103">As an alternative to compiling Visual Basic programs from within [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="66db9-104">Visual Basic komut satırı derleyicisi giriş denetleyen ve dosyaları, derlemeler ve hata ayıklama ve önişlemci seçenekleri çıkış seçenekleri eksiksiz bir kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="66db9-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="66db9-105">Her seçenek birbirinin yerine iki biçimde sağlanır: `-option` ve `/option`.</span><span class="sxs-lookup"><span data-stu-id="66db9-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="66db9-106">Bu belge yalnızca gösterir `-option` formu.</span><span class="sxs-lookup"><span data-stu-id="66db9-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="66db9-107">Aşağıdaki tabloda bazı örnek komut satırları kendi kullanımınız için değiştirebileceğiniz listeler.</span><span class="sxs-lookup"><span data-stu-id="66db9-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="66db9-108">Bitiş</span><span class="sxs-lookup"><span data-stu-id="66db9-108">To</span></span>|<span data-ttu-id="66db9-109">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="66db9-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="66db9-110">File.vb derlemek ve File.exe oluşturma</span><span class="sxs-lookup"><span data-stu-id="66db9-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="66db9-111">File.vb derlemek ve File.dll oluşturma</span><span class="sxs-lookup"><span data-stu-id="66db9-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="66db9-112">File.vb derlemek ve My.exe oluşturma</span><span class="sxs-lookup"><span data-stu-id="66db9-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="66db9-113">File.vb derlemek ve kitaplığa ve File.dll adlı bir başvuru derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="66db9-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="66db9-114">Üzerinde en iyi duruma getirme ile geçerli dizinin tüm Visual Basic dosyalarını derlemek ve `DEBUG` tanımlanmış sembol File2.exe üretme</span><span class="sxs-lookup"><span data-stu-id="66db9-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="66db9-115">Geçerli dizindeki logo veya uyarıları görüntülemeden File2.dll hata sürümü oluşturan tüm Visual Basic dosyaları derleme</span><span class="sxs-lookup"><span data-stu-id="66db9-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="66db9-116">Something.dll geçerli dizindeki tüm Visual Basic dosyaları derleme</span><span class="sxs-lookup"><span data-stu-id="66db9-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="66db9-117">Visual Studio IDE kullanarak bir proje oluşturduğunuzda ilişkili ilgili bilgileri görüntüleyebilirsiniz **vbc** kendi derleyici seçenekleri çıktı penceresinde ile komutu.</span><span class="sxs-lookup"><span data-stu-id="66db9-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="66db9-118">Bu bilgileri görüntülemek için açık [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)ve ardından **MSBuild Proje yapı çıktı ayrıntı** için **Normal** veya daha yüksek bir ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="66db9-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="66db9-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66db9-119">See Also</span></span>  
 [<span data-ttu-id="66db9-120">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="66db9-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="66db9-121">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="66db9-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
