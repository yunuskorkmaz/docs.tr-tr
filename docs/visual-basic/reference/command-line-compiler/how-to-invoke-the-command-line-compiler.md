---
title: 'Nasıl yapılır: (Visual Basic) komut satırı derleyicisini çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 78bf5b1f19db3a4f39e263cfd71283f0f7718631
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817194"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="b26f2-102">Nasıl yapılır: (Visual Basic) komut satırı derleyicisini çağırma</span><span class="sxs-lookup"><span data-stu-id="b26f2-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="b26f2-103">Komut satırına, MS-DOS İstemi olarak da bilinen yürütülebilir dosyasının adını yazarak komut satırı derleyicisini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b26f2-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="b26f2-104">Windows komut istemi varsayılan derleme yaparsanız, yürütülebilir dosyanın tam yolunu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b26f2-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="b26f2-105">Bu varsayılan davranışı geçersiz kılmak için Visual Studio için geliştirici komut istemi kullanın veya yol ortam değişkenine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b26f2-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="b26f2-106">Her ikisi de, derleme adını yazarak herhangi bir dizinden derleme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b26f2-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="b26f2-107">Visual Studio için geliştirici komut istemi kullanarak derleyici çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b26f2-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>  
  
1.  <span data-ttu-id="b26f2-108">Microsoft Visual Studio program grubu içinde Visual Studio Araçları program klasörü açın.</span><span class="sxs-lookup"><span data-stu-id="b26f2-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="b26f2-109">Visual Studio yüklüyse derleyici makinenizde, herhangi bir dizinden erişmek için Visual Studio için geliştirici Komut İstemi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b26f2-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="b26f2-110">Visual Studio için geliştirici komut istemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="b26f2-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>  
  
4.  <span data-ttu-id="b26f2-111">Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b26f2-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="b26f2-112">Örneğin, kaynak kodunuzu adlı dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="b26f2-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="b26f2-113">Dizin adlı bir kaynak dosyası içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="b26f2-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="b26f2-114">PATH ortam değişkenine derleyicisi için Windows komut istemi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b26f2-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="b26f2-115">Yerel diskinizde Vbc.exe bulmak için Windows Search özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b26f2-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="b26f2-116">Derleyici bulunduğu dizinin tam adı, Windows dizin konumunu ve ".NET Framework'ün" sürüm bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b26f2-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="b26f2-117">".NET Framework'ün" birden fazla sürümü varsa, hangi sürümün (genellikle en son sürüm) kullanılacağını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b26f2-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="b26f2-118">Öğesinden, **Başlat** menüsünde sağ **Bilgisayarım**ve ardından **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="b26f2-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="b26f2-119">Tıklayın **Gelişmiş** sekmesine ve ardından **ortam değişkenlerini**.</span><span class="sxs-lookup"><span data-stu-id="b26f2-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="b26f2-120">İçinde **sistem** değişkenleri bölmesinde **yolu** listesi ve **Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="b26f2-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="b26f2-121">İçinde **düzenleme sistemi** değişken iletişim kutusunda, dizenin sonuna ekleme noktasını Taşı **değişken değeri** alan ve noktalı virgül (;) yazın ardından adım 1'de bulunan tam dizin adı.</span><span class="sxs-lookup"><span data-stu-id="b26f2-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="b26f2-122">Tıklayın **Tamam** yaptığınız düzenlemeleri onaylamak ve iletişim kutularını kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="b26f2-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="b26f2-123">PATH ortam değişkenine değiştirdikten sonra Visual Basic Derleyicisi Windows komut isteminde herhangi bir dizinden bilgisayarda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b26f2-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="b26f2-124">Windows komut istemi kullanarak derleyici çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b26f2-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="b26f2-125">Gelen **Başlat** menüsünde tıklatın **Donatılar** klasörünü açın ve ardından açık **Windows Komut İstemi**.</span><span class="sxs-lookup"><span data-stu-id="b26f2-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="b26f2-126">Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b26f2-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="b26f2-127">Örneğin, kaynak kodunuzu adlı dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="b26f2-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="b26f2-128">Dizin adlı bir kaynak dosyası içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="b26f2-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b26f2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b26f2-129">See also</span></span>

- [<span data-ttu-id="b26f2-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b26f2-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b26f2-131">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="b26f2-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
