---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Command-Line derleyicisini çağırma (Visual Basic)'
title: 'Nasıl yapılır: Komut Satırı Derleyicisini Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: aca8fe70e252ae9e7fb06f740ce5b7f3c8ca3d5d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470219"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="31df2-103">Nasıl yapılır: Komut Satırı Derleyicisini Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31df2-103">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="31df2-104">Komut satırı derleyicisini, yürütülebilir dosyasının adını MS-DOS istemi olarak da bilinen komut satırına yazarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31df2-104">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="31df2-105">Varsayılan Windows komut Isteminden derleme yaparsanız, yürütülebilir dosyanın tam yolunu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31df2-105">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="31df2-106">Bu varsayılan davranışı geçersiz kılmak için, Visual Studio Geliştirici Komut İstemi kullanabilir ya da PATH ortam değişkenini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31df2-106">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="31df2-107">Her ikisi de yalnızca derleyici adını yazarak herhangi bir dizinden derlemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="31df2-107">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="31df2-108">Visual Studio için Geliştirici Komut İstemi kullanarak derleyiciyi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="31df2-108">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="31df2-109">Microsoft Visual Studio program grubu içinde Visual Studio Araçları program klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="31df2-109">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="31df2-110">Visual Studio 'nun yüklüyse, makinenizde herhangi bir dizinden derleyiciye erişmek için Visual Studio Geliştirici Komut İstemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31df2-110">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="31df2-111">Visual Studio için Geliştirici Komut İstemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="31df2-111">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="31df2-112">Komut satırında `vbc.exe` *sourceFileName* yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="31df2-112">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="31df2-113">Örneğin, kaynak kodunuzu adlı bir dizinde depoladıysanız `SourceFiles` , komut istemi ' ni açıp `cd SourceFiles` Bu dizine geçmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="31df2-113">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="31df2-114">Dizinde adlı bir kaynak dosyası varsa `Source.vb` , yazarak derleyebilirsiniz `vbc.exe Source.vb` .</span><span class="sxs-lookup"><span data-stu-id="31df2-114">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="31df2-115">Windows komut Istemi için PATH ortam değişkenini derleyiciye ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="31df2-115">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="31df2-116">Yerel diskinizde Vbc.exe bulmak için Windows Search özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="31df2-116">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="31df2-117">Derleyicinin bulunduğu dizinin tam adı Windows dizininin konumuna ve ".NET Framework" sürümünün yüklü olmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="31df2-117">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="31df2-118">".NET Framework" öğesinin birden fazla sürümü yüklüyse, hangi sürümün kullanılacağını (genellikle en son sürüm) belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="31df2-118">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="31df2-119">**Başlangıç** menüsünde **, Bilgisayarım ' a sağ tıklayın ve** ardından kısayol menüsünde **Özellikler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="31df2-119">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="31df2-120">**Gelişmiş** sekmesine tıklayın ve ardından **ortam değişkenleri**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="31df2-120">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="31df2-121">**Sistem** değişkenleri bölmesinde listeden **yol** ' ı seçin ve **Düzenle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="31df2-121">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="31df2-122">Sistem değişkenini **Düzenle** iletişim kutusunda, ekleme noktasını **değişken değer** alanındaki dizenin sonuna taşıyın ve noktalı virgül (;) yazın ardından adım 1 ' de bulunan tam dizin adı.</span><span class="sxs-lookup"><span data-stu-id="31df2-122">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="31df2-123">Düzenlemelerinizi onaylamak ve iletişim kutularını kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="31df2-123">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="31df2-124">PATH ortam değişkenini değiştirdikten sonra, Visual Basic derleyicisini bilgisayardaki herhangi bir dizinden Windows komut Isteminde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31df2-124">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="31df2-125">Windows komut Istemi kullanarak derleyiciyi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="31df2-125">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="31df2-126">**Başlat** menüsünde, **Donatılar** klasörüne tıklayın ve ardından **Windows komut istemi**' ni açın.</span><span class="sxs-lookup"><span data-stu-id="31df2-126">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="31df2-127">Komut satırında `vbc.exe` *sourceFileName* yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="31df2-127">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="31df2-128">Örneğin, kaynak kodunuzu adlı bir dizinde depoladıysanız `SourceFiles` , komut istemi ' ni açıp `cd SourceFiles` Bu dizine geçmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="31df2-128">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="31df2-129">Dizinde adlı bir kaynak dosyası varsa `Source.vb` , yazarak derleyebilirsiniz `vbc.exe Source.vb` .</span><span class="sxs-lookup"><span data-stu-id="31df2-129">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="31df2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31df2-130">See also</span></span>

- [<span data-ttu-id="31df2-131">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="31df2-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="31df2-132">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="31df2-132">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
