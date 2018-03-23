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
ms.openlocfilehash: a7c3fac318e05c5e3d6fb9dd7117cac70ead03dc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="9e7d3-102">Örnek derleme komut satırları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e7d3-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="9e7d3-103">Derleme alternatif olarak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programların içinden [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], yürütülebilir dosyanın (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyaları üretmek için komut satırından derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-103">As an alternative to compiling [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs from within [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="9e7d3-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Komut satırı derleyicisi girdi ve çıktı dosyaları, derlemeler ve hata ayıklama denetleyen ve önişlemci seçeneklerini eksiksiz bir kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="9e7d3-105">Her seçenek birbirinin yerine iki biçimde sağlanır: `-option` ve `/option`.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="9e7d3-106">Bu belge yalnızca gösterir `-option` formu.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="9e7d3-107">Aşağıdaki tabloda bazı örnek komut satırları kendi kullanımınız için değiştirebileceğiniz listeler.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="9e7d3-108">Bitiş</span><span class="sxs-lookup"><span data-stu-id="9e7d3-108">To</span></span>|<span data-ttu-id="9e7d3-109">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="9e7d3-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="9e7d3-110">File.vb derlemek ve File.exe oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e7d3-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="9e7d3-111">File.vb derlemek ve File.dll oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e7d3-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="9e7d3-112">File.vb derlemek ve My.exe oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e7d3-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="9e7d3-113">Tüm derleme [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dosyaları en iyi duruma getirme ile geçerli dizinin üzerindeki ve `DEBUG` tanımlanmış sembol File2.exe üretme</span><span class="sxs-lookup"><span data-stu-id="9e7d3-113">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="9e7d3-114">Tüm derleme [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] logo veya uyarıları görüntülemeden File2.dll hata sürümü oluşturan geçerli dizindeki dosyaları</span><span class="sxs-lookup"><span data-stu-id="9e7d3-114">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="9e7d3-115">Tüm derleme [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Something.dll için geçerli dizindeki dosyaları</span><span class="sxs-lookup"><span data-stu-id="9e7d3-115">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
 <span data-ttu-id="9e7d3-116">Komut satırından derlerken Microsoft açıkça başvurmalıdır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] çalışma zamanı kitaplığı aracılığıyla `-reference` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] run-time library through the `-reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="9e7d3-117">Visual Studio IDE kullanarak bir proje oluşturduğunuzda ilişkili ilgili bilgileri görüntüleyebilirsiniz **vbc** kendi derleyici seçenekleri çıktı penceresinde ile komutu.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="9e7d3-118">Bu bilgileri görüntülemek için açık [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)ve ardından **MSBuild Proje yapı çıktı ayrıntı** için **Normal** veya daha yüksek bir ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="9e7d3-119">Daha fazla bilgi için bkz: [nasıl yapılır: görünümü, kaydetme ve yapı günlük dosyalarını Yapılandır](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="9e7d3-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7d3-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e7d3-120">See Also</span></span>  
 [<span data-ttu-id="9e7d3-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9e7d3-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9e7d3-122">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="9e7d3-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
