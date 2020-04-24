---
title: 'Nasıl yapılır: Komut Satırı Derleyicisini Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344254"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="51559-102">Nasıl yapılır: Komut Satırı Derleyicisini Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51559-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="51559-103">Komut satırı derleyicisini, yürütülebilir dosyasının adını MS-DOS istemi olarak da bilinen komut satırına yazarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51559-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="51559-104">Varsayılan Windows komut Isteminden derleme yaparsanız, yürütülebilir dosyanın tam yolunu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51559-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="51559-105">Bu varsayılan davranışı geçersiz kılmak için, Visual Studio Geliştirici Komut İstemi kullanabilir ya da PATH ortam değişkenini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51559-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="51559-106">Her ikisi de yalnızca derleyici adını yazarak herhangi bir dizinden derlemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="51559-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="51559-107">Visual Studio için Geliştirici Komut İstemi kullanarak derleyiciyi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="51559-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="51559-108">Microsoft Visual Studio program grubu içinde Visual Studio Araçları program klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="51559-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="51559-109">Visual Studio 'nun yüklüyse, makinenizde herhangi bir dizinden derleyiciye erişmek için Visual Studio Geliştirici Komut İstemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51559-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="51559-110">Visual Studio için Geliştirici Komut İstemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="51559-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="51559-111">Komut satırında `vbc.exe` *sourceFileName* yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="51559-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="51559-112">Örneğin, kaynak kodunuzu adlı `SourceFiles`bir dizinde depoladıysanız, komut istemi ' ni açıp bu dizine geçmek için yazın. `cd SourceFiles`</span><span class="sxs-lookup"><span data-stu-id="51559-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="51559-113">Dizinde adlı `Source.vb`bir kaynak dosyası varsa, yazarak `vbc.exe Source.vb`derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51559-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="51559-114">Windows komut Istemi için PATH ortam değişkenini derleyiciye ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="51559-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="51559-115">Yerel diskinizde Vbc. exe ' yi bulmak için Windows Search özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="51559-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="51559-116">Derleyicinin bulunduğu dizinin tam adı Windows dizininin konumuna ve ".NET Framework" sürümünün yüklü olmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="51559-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="51559-117">".NET Framework" öğesinin birden fazla sürümü yüklüyse, hangi sürümün kullanılacağını (genellikle en son sürüm) belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="51559-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="51559-118">**Başlangıç** menüsünde **, Bilgisayarım ' a sağ tıklayın ve**ardından kısayol menüsünde **Özellikler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51559-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="51559-119">**Gelişmiş** sekmesine tıklayın ve ardından **ortam değişkenleri**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51559-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="51559-120">**Sistem** değişkenleri bölmesinde listeden **yol** ' ı seçin ve **Düzenle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51559-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="51559-121">Sistem değişkenini **Düzenle** iletişim kutusunda, ekleme noktasını **değişken değer** alanındaki dizenin sonuna taşıyın ve noktalı virgül (;) yazın ardından adım 1 ' de bulunan tam dizin adı.</span><span class="sxs-lookup"><span data-stu-id="51559-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="51559-122">Düzenlemelerinizi onaylamak ve iletişim kutularını kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="51559-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="51559-123">PATH ortam değişkenini değiştirdikten sonra, Visual Basic derleyicisini bilgisayardaki herhangi bir dizinden Windows komut Isteminde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51559-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="51559-124">Windows komut Istemi kullanarak derleyiciyi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="51559-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="51559-125">**Başlat** menüsünde, **Donatılar** klasörüne tıklayın ve ardından **Windows komut istemi**' ni açın.</span><span class="sxs-lookup"><span data-stu-id="51559-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="51559-126">Komut satırında `vbc.exe` *sourceFileName* yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="51559-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="51559-127">Örneğin, kaynak kodunuzu adlı `SourceFiles`bir dizinde depoladıysanız, komut istemi ' ni açıp bu dizine geçmek için yazın. `cd SourceFiles`</span><span class="sxs-lookup"><span data-stu-id="51559-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="51559-128">Dizinde adlı `Source.vb`bir kaynak dosyası varsa, yazarak `vbc.exe Source.vb`derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51559-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="51559-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51559-129">See also</span></span>

- [<span data-ttu-id="51559-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="51559-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="51559-131">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="51559-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
