---
title: 'Nasıl yapılır: Komut Satırı Derleyicisini Çağırma (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1ccf08ba58fa6af60bd8ffd7cba79b205dc0f3d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="1156c-102">Nasıl yapılır: Komut Satırı Derleyicisini Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1156c-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="1156c-103">Komut satırına olarak da bilinen MS-DOS İstemi yürütülebilir dosyanın adını yazarak komut satırı derleyicisini çağırma.</span><span class="sxs-lookup"><span data-stu-id="1156c-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="1156c-104">Varsayılan Windows komut istemi derleme yaparsanız, yürütülebilir dosyanın tam yolunu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1156c-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="1156c-105">Bu varsayılan davranışı geçersiz kılmak için kullanabilir [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] komut istemi veya PATH ortam değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1156c-105">To override this default behavior, you can either use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt, or modify the PATH environment variable.</span></span> <span data-ttu-id="1156c-106">Her ikisi de, herhangi bir dizinden derleyici adını yazarak derlemek izin verir.</span><span class="sxs-lookup"><span data-stu-id="1156c-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a><span data-ttu-id="1156c-107">Visual Studio komut istemi kullanarak derleyici çağırmak için</span><span class="sxs-lookup"><span data-stu-id="1156c-107">To invoke the compiler using the Visual Studio Command Prompt</span></span>  
  
1.  <span data-ttu-id="1156c-108">Microsoft Visual Studio program grubunu Visual Studio Araçları program klasördeki açın.</span><span class="sxs-lookup"><span data-stu-id="1156c-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="1156c-109">Kullanabileceğiniz [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Visual Studio yüklüyse, makinenizde herhangi bir dizinden derleyici erişmek için komut isteminden.</span><span class="sxs-lookup"><span data-stu-id="1156c-109">You can use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="1156c-110">Çağırma [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="1156c-110">Invoke the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
4.  <span data-ttu-id="1156c-111">Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1156c-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="1156c-112">Örneğin, kaynak kodunuzu adlı bir dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="1156c-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="1156c-113">Dizin adlı bir kaynak dosya içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="1156c-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="1156c-114">Windows komut satırından derleyiciye PATH ortam değişkeni ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1156c-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="1156c-115">Yerel diskinize Vbc.exe bulmak için Windows Arama özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1156c-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="1156c-116">Derleyici bulunduğu dizinin tam adı, Windows dizininin konumu ve sürümünü ".NET Framework'ün yüklü" bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1156c-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="1156c-117">".NET Framework'ün yüklü" birden çok sürüm varsa, hangi sürümün (genellikle en son sürüm) kullanılacağını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1156c-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="1156c-118">Öğesinden, **Başlat** menüsünde sağ **Bilgisayarım**ve ardından **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="1156c-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="1156c-119">Tıklatın **Gelişmiş** sekmesini ve ardından **ortam değişkenleri**.</span><span class="sxs-lookup"><span data-stu-id="1156c-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="1156c-120">İçinde **sistem** değişkenleri bölmesinde, **yolu** tıklatın ve liste **Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="1156c-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="1156c-121">İçinde **Düzenle sistem** değişken iletişim kutusunda, dizenin sonuna ekleme noktasını Taşı **değişken değeri** alan ve noktalı virgül (;) yazın adım 1'de bulunan tam dizin adı ve ardından.</span><span class="sxs-lookup"><span data-stu-id="1156c-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="1156c-122">Tıklatın **Tamam** yaptığınız düzenlemeleri onaylamak ve iletişim kutularını kapatın.</span><span class="sxs-lookup"><span data-stu-id="1156c-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="1156c-123">PATH ortam değişkeni değiştirdikten sonra Visual Basic derleyici Windows komut isteminde herhangi bir dizinden bilgisayarda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1156c-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="1156c-124">Windows komut istemi kullanarak derleyici çağırmak için</span><span class="sxs-lookup"><span data-stu-id="1156c-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="1156c-125">Gelen **Başlat** menüsünde tıklatın **Donatılar** klasörünü ve ardından açın **Windows Komut İstemi**.</span><span class="sxs-lookup"><span data-stu-id="1156c-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="1156c-126">Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1156c-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="1156c-127">Örneğin, kaynak kodunuzu adlı bir dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="1156c-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="1156c-128">Dizin adlı bir kaynak dosya içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="1156c-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1156c-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1156c-129">See Also</span></span>  
 [<span data-ttu-id="1156c-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1156c-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1156c-131">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="1156c-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
