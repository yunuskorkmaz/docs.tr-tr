---
title: Komut Satırından Derleme (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a9dee47f06e4f7d9fc8d237376df7707130921d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="2589e-102">Komut Satırından Derleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2589e-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="2589e-103">Visual Basic projesinde, bir veya daha fazla ayrı kaynak dosyalarını yapılır.</span><span class="sxs-lookup"><span data-stu-id="2589e-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="2589e-104">Derleme bilinen işlem sırasında bu dosyaları birlikte bir pakete yapılmadan — bir uygulama olarak çalıştırılabilir tek bir yürütülebilir dosya.</span><span class="sxs-lookup"><span data-stu-id="2589e-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="2589e-105">Visual Basic, Visual Studio tümleşik geliştirme ortamı (IDE) içinde programları derleme alternatif olarak komut satırı derleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2589e-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="2589e-106">Komut satırı derleyicisi içinde gerektirmeyen IDE özelliklerinde, tamamını durumlar için tasarlanmış — Örneğin, ne zaman, kullanarak veya sınırlı sayıda sistem bellek veya depolama alanı sahip bilgisayarlar için yazma.</span><span class="sxs-lookup"><span data-stu-id="2589e-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="2589e-107">Visual Studio IDE içinde kaynak dosyalarını derlemek için seçin **yapı** komutunu **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2589e-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="2589e-108">Visual Studio IDE kullanarak proje dosyalarını derlerken ilişkili ilgili bilgileri görüntüleyebilirsiniz **vbc** komut ve çıktı penceresinde alt anahtarlar.</span><span class="sxs-lookup"><span data-stu-id="2589e-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="2589e-109">Bu bilgileri görüntülemek için açık [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)ve ardından **MSBuild Proje yapı çıktı ayrıntı** için **Normal** veya daha yüksek bir ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="2589e-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="2589e-110">Daha fazla bilgi için bkz: [nasıl yapılır: görünümü, kaydetme ve yapı günlük dosyalarını Yapılandır](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="2589e-110">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="2589e-111">MSBuild kullanarak bir komut isteminde proje (.vbproj) dosyalarını derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2589e-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="2589e-112">Daha fazla bilgi için bkz: [komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference) ve [izlenecek yol: MSBuild kullanma](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="2589e-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2589e-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2589e-113">In This Section</span></span>  
 [<span data-ttu-id="2589e-114">Nasıl yapılır: Komut Satırı Derleyicisini Çağırma</span><span class="sxs-lookup"><span data-stu-id="2589e-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="2589e-115">MS-DOS komut isteminde veya belirli bir alt dizinden komut satırı derleyicisini çağırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="2589e-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="2589e-116">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2589e-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="2589e-117">Kendi kullanımınız için değiştirebileceğiniz örnek komut satırları listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2589e-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2589e-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2589e-118">Related Sections</span></span>  
 [<span data-ttu-id="2589e-119">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2589e-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="2589e-120">Alfabetik olarak veya amacına göre düzenlenmiş derleyici seçenekleri listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2589e-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="2589e-121">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="2589e-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="2589e-122">Kodun belirli bölümlerini derlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="2589e-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="2589e-123">Visual Studio'da Projeler ve Çözümler Oluşturma ve Temizleme</span><span class="sxs-lookup"><span data-stu-id="2589e-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="2589e-124">Ne farklı derlemelerde dahil edilecek proje özellikleri'ni seçin ve doğru sırada derleme projeleri olun düzenlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="2589e-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
