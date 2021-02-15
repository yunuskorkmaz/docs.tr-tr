---
description: 'Daha fazla bilgi edinin: örnek derleme komut satırları (Visual Basic)'
title: Örnek Derleme Komut Satırları
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: fbd35b7f12b3bee9690698a24dcb70d850081f95
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474011"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="95361-103">Örnek derleme komut satırları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95361-103">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="95361-104">Visual Studio içinden Visual Basic programları derlemeye alternatif olarak, çalıştırılabilir (. exe) dosyalar veya dinamik bağlantı kitaplığı (. dll) dosyaları oluşturmak için komut satırından derleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95361-104">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="95361-105">Visual Basic komut satırı derleyicisi, giriş ve çıkış dosyalarını, derlemeleri ve hata ayıklama ve Önişlemci seçeneklerini denetleyen tam bir seçenek kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="95361-105">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="95361-106">Her seçenek, iki değiştirilebilir formda mevcuttur: `-option` ve `/option` .</span><span class="sxs-lookup"><span data-stu-id="95361-106">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="95361-107">Bu belgede yalnızca form gösterilmektedir `-option` .</span><span class="sxs-lookup"><span data-stu-id="95361-107">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="95361-108">Aşağıdaki tabloda, kendi kullanımı için değiştirebileceğiniz bazı örnek komut satırları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="95361-108">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="95361-109">Amaç</span><span class="sxs-lookup"><span data-stu-id="95361-109">To</span></span>|<span data-ttu-id="95361-110">Kullanın</span><span class="sxs-lookup"><span data-stu-id="95361-110">Use</span></span>|
|--------|---------|
|<span data-ttu-id="95361-111">Dosya. vb dosyasını derleyin ve File.exe oluşturun</span><span class="sxs-lookup"><span data-stu-id="95361-111">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="95361-112">Dosya. vb dosyasını derleyin ve File.dll oluşturun</span><span class="sxs-lookup"><span data-stu-id="95361-112">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="95361-113">Dosya. vb dosyasını derleyin ve My.exe oluşturun</span><span class="sxs-lookup"><span data-stu-id="95361-113">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="95361-114">File. vb derleyin ve hem bir kitaplık hem de File.dll adlı bir başvuru bütünleştirilmiş kodu oluşturun</span><span class="sxs-lookup"><span data-stu-id="95361-114">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="95361-115">Geçerli dizindeki tüm Visual Basic dosyalarını, iyileştirmelere ve `DEBUG` tanımlanan simgeye göre derleyin, File2.exe üretme</span><span class="sxs-lookup"><span data-stu-id="95361-115">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="95361-116">Logo veya uyarıları görüntülemeden bir File2.dll hata ayıklama sürümü üreten geçerli dizindeki tüm Visual Basic dosyalarını derleyin</span><span class="sxs-lookup"><span data-stu-id="95361-116">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="95361-117">Geçerli dizindeki tüm Visual Basic dosyalarını Something.dll olarak derle</span><span class="sxs-lookup"><span data-stu-id="95361-117">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="95361-118">Visual Studio IDE kullanarak bir proje oluşturduğunuzda, ilişkili **vbc** komutuyla ilgili bilgileri çıkış penceresinde derleyici seçenekleriyle birlikte görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95361-118">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="95361-119">Bu bilgileri göstermek için, [Seçenekler Iletişim kutusu, projeler ve çözümler ' i açın ve çalıştırın](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), sonra **MSBuild proje yapı çıkış ayrıntı** düzeyini **normal** veya daha yüksek ayrıntı düzeyi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="95361-119">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="95361-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95361-120">See also</span></span>

- [<span data-ttu-id="95361-121">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="95361-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="95361-122">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="95361-122">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
