---
title: 'Nasıl yapılır: görsel C# özellikler kullanarak Office birlikte çalışma nesnelerine erişme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 3399d1aad8a2118775f7779727d4d03ee2002547
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834206"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="fc2f0-102">Nasıl yapılır: görsel C# özellikler kullanarak Office birlikte çalışma nesnelerine erişim (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fc2f0-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>

<span data-ttu-id="fc2f0-103">Görselde C# Office API nesnelerine erişimi basitleştiren özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="fc2f0-104">Yeni özellikler adlandırılmış ve isteğe bağlı bağımsız değişkenler, `dynamic` adlı yeni bir tür ve bağımsız değişkenleri, değer parametreleri gibi COM yöntemlerinde başvuru parametrelerine geçirebilme özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="fc2f0-105">Bu konu başlığında, Microsoft Office bir Excel çalışma sayfası oluşturan ve görüntüleyen kod yazmak için yeni özellikleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="fc2f0-106">Daha sonra, Excel çalışma sayfasına bağlı bir simge içeren bir Office Word belgesi eklemek için kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="fc2f0-107">Bu yönergeyi tamamlamak için, bilgisayarınızda yüklü Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya sonraki sürümlerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="fc2f0-108">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-108">To create a new console application</span></span>

1. <span data-ttu-id="fc2f0-109">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="fc2f0-110">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="fc2f0-111">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="fc2f0-112">**Yüklü şablonlar** bölmesinde, **görsel C#** ' i genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="fc2f0-113">**.NET Framework 4** ' ün (veya sonraki bir sürüm) hedef çerçeve olarak seçildiğinden emin olmak Için **Yeni proje** iletişim kutusunun üst kısmına bakın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="fc2f0-114">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="fc2f0-115">**Ad** alanına projeniz için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="fc2f0-116">**Tamam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-116">Click **OK**.</span></span>

     <span data-ttu-id="fc2f0-117">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="fc2f0-118">Başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-118">To add references</span></span>

1. <span data-ttu-id="fc2f0-119">**Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="fc2f0-120">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="fc2f0-121">**Derlemeler** sayfasında, **bileşen adı** listesinde **Microsoft. Office. Interop. Word** ' ü seçin ve ardından CTRL tuşunu basılı tutarak **Microsoft. Office. Interop. Excel**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="fc2f0-122">Derlemeleri görmüyorsanız bunların yüklendiğinden ve görüntülendiğinden emin olmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-122">If you do not see the assemblies, you may need to ensure they are installed and displayed.</span></span> <span data-ttu-id="fc2f0-123">Bkz. [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span><span class="sxs-lookup"><span data-stu-id="fc2f0-123">See [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span></span>

3. <span data-ttu-id="fc2f0-124">**Tamam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="fc2f0-125">Gerekli yönergeleri kullanarak ekleme</span><span class="sxs-lookup"><span data-stu-id="fc2f0-125">To add necessary using directives</span></span>

1. <span data-ttu-id="fc2f0-126">**Çözüm Gezgini**, *program.cs* dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="fc2f0-127">Kod dosyasının en üstüne aşağıdaki `using` yönergelerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fc2f0-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="fc2f0-128">Banka hesaplarının bir listesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-128">To create a list of bank accounts</span></span>

1. <span data-ttu-id="fc2f0-129">Aşağıdaki sınıf tanımını `Program` sınıfı altında **program.cs**içine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-129">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="fc2f0-130">İki hesap içeren bir `bankAccounts` listesi oluşturmak için `Main` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-130">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="fc2f0-131">Excel 'e hesap bilgilerini veren bir yöntem bildirmek için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-131">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="fc2f0-132">Bir Excel çalışma sayfası ayarlamak için aşağıdaki yöntemi `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-132">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="fc2f0-133">@No__t-0 yönteminin belirli bir şablonu belirtmek için isteğe bağlı bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-133">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="fc2f0-134">4 ' te C# yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız bu parametreye ilişkin bağımsız değişkeni atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-134">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="fc2f0-135">Aşağıdaki kodda bir bağımsız değişken gönderilmediğinden, `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-135">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="fc2f0-136">Önceki sürümlerindeki denk ifade, bir yer C# tutucu bağımsız değişkeni gerektirir: `ExcelApp.Workbooks.Add(Type.Missing)`.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-136">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="fc2f0-137">@No__t-0 ' ın sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-137">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="fc2f0-138">Kod, çalışma sayfasının ilk satırının ilk iki sütununa değer ekler.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-138">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="fc2f0-139">@No__t-0 ' ın sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="fc2f0-140">@No__t-0 döngüsü, hesap listesindeki bilgileri, çalışma sayfasının Art arda gelen satırlarının ilk iki sütununa koyar.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-140">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="fc2f0-141">Sütun genişliğini içeriğe sığacak şekilde ayarlamak için `DisplayInExcel` ' ın sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-141">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="fc2f0-142">Önceki sürümleri, C# bu işlemler için açık atama gerektirir çünkü `ExcelApp.Columns[1]` `Object` ve `AutoFit` bir Excel <xref:Microsoft.Office.Interop.Excel.Range> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-142">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="fc2f0-143">Aşağıdaki satırlarda atama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-143">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="fc2f0-144">C#4 ve sonraki sürümlerde, derleme [/Link](../../language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği tarafından başvuruluyorsa ya da equivalently, Excel **birlikte çalışma türleri** özelliği true olarak ayarlandıysa, tarafından döndürülen `Object` ' i `dynamic` ' ye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-144">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="fc2f0-145">True, bu özellik için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-145">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="fc2f0-146">Projeyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-146">To run the project</span></span>

1. <span data-ttu-id="fc2f0-147">@No__t-0 ' ın sonuna aşağıdaki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-147">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="fc2f0-148">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-148">Press CTRL+F5.</span></span>

     <span data-ttu-id="fc2f0-149">İki hesaptan gelen verileri içeren bir Excel çalışma sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-149">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="fc2f0-150">Word belgesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-150">To add a Word document</span></span>

1. <span data-ttu-id="fc2f0-151">C# 4 ve sonraki sürümlerin, Office programlama 'yi geliştiren ek yollarını göstermek için aşağıdaki kod bir Word uygulaması açar ve Excel çalışma sayfasına bağlanan bir simge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-151">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="fc2f0-152">Bu adımda daha sonra sağlanmış olan `CreateIconInWordDoc` yöntemini `Program` sınıfına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-152">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="fc2f0-153">`CreateIconInWordDoc`, yöntem çağrılarının karmaşıklığını azaltmak için adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanır <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> ve <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-153">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="fc2f0-154">Bu çağrılar, başvuru parametrelerine sahip COM yöntemlerine yapılan C# çağrıları kolaylaştıran 4 ' te tanıtılan iki yeni özelliği dahil ediyor.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-154">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="fc2f0-155">İlk olarak, başvuru parametrelerine bağımsız değişkenleri değer parametreleriniz gibi gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-155">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="fc2f0-156">Diğer bir deyişle, her başvuru parametresi için bir değişken oluşturmadan doğrudan değerleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-156">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="fc2f0-157">Derleyici bağımsız değişken değerlerini tutacak geçici değişkenler oluşturur ve çağrıdan geri döndüğünüzde değişkenleri atar.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-157">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="fc2f0-158">İkinci olarak, bağımsız değişken listesindeki `ref` anahtar sözcüğünü atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-158">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="fc2f0-159">@No__t-0 yönteminde, tümü isteğe bağlı dört başvuru parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-159">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="fc2f0-160">C# 4,0 ve sonraki sürümlerde, varsayılan değerlerini kullanmak istiyorsanız parametrelerin herhangi biri veya tümü için bağımsız değişkenleri atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-160">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="fc2f0-161">C# 3,0 ve önceki sürümlerde, her bir parametre için bir bağımsız değişken sağlanmalı ve parametreler başvuru parametreleri olduğundan bağımsız değişken bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-161">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="fc2f0-162">@No__t-0 yöntemi panonun içeriğini ekler.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-162">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="fc2f0-163">Yönteminde, hepsi isteğe bağlı yedi başvuru parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-163">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="fc2f0-164">Aşağıdaki kod, iki öğenin bağımsız değişkenlerini belirtir: `Link`, pano içeriklerinin kaynağına bir bağlantı oluşturmak için ve bağlantıyı bir simge olarak göstermek için-1 @no__t.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-164">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="fc2f0-165">C# 4,0 ve sonraki sürümlerde, bu ikisi için adlandırılmış bağımsız değişkenleri kullanabilir ve diğerlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-165">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="fc2f0-166">Bunların başvuru parametreleri olmasına karşın, `ref` anahtar sözcüğünü kullanmanız veya bağımsız değişken olarak gönderilmek üzere değişkenler oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-166">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="fc2f0-167">Değerleri doğrudan gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-167">You can send the values directly.</span></span> <span data-ttu-id="fc2f0-168">C# 3,0 ve önceki sürümlerde, her başvuru parametresi için bir değişken bağımsız değişkeni sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-168">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="fc2f0-169">Dilin C# 3,0 ve önceki sürümlerinde, aşağıdaki daha karmaşık kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-169">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="fc2f0-170">@No__t-0 ' ın sonuna aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-170">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="fc2f0-171">@No__t-0 ' ın sonuna aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-171">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="fc2f0-172">@No__t-0 yöntemi, çalışma sayfasını panoya ekler.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-172">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="fc2f0-173">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-173">Press CTRL+F5.</span></span>

     <span data-ttu-id="fc2f0-174">Bir simge içeren bir Word belgesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-174">A Word document appears that contains an icon.</span></span> <span data-ttu-id="fc2f0-175">Çalışma sayfasını ön plana getirmek için simgeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-175">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="fc2f0-176">Birlikte çalışma türlerini katıştır özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-176">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="fc2f0-177">Çalışma zamanında birincil birlikte çalışma derlemesi (PIA) gerektirmeyen bir COM türünü çağırdığınızda ek geliştirmeler yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-177">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="fc2f0-178">PIA 'ların bağımlılığını kaldırmak sürüm bağımsızlık ve daha kolay dağıtıma neden olur.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-178">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="fc2f0-179">PIA olmadan programlamanın avantajları hakkında daha fazla bilgi için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="fc2f0-179">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="fc2f0-180">Ayrıca, gerekli ve COM yöntemleri tarafından döndürülen türler `Object` yerine `dynamic` türü kullanılarak gösterilebildiğinden programlama kolaylaşır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-180">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="fc2f0-181">@No__t-0 türüne sahip değişkenler, çalışma zamanına kadar değerlendirilmez ve bu da açık atama gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-181">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="fc2f0-182">Daha fazla bilgi için bkz. [dinamik tür kullanımı](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="fc2f0-182">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="fc2f0-183">4 C# ' te, PIA kullanımı yerine tür bilgilerini katıştırma varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-183">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="fc2f0-184">Bu varsayılan nedenle, açık atama gerekli olmadığından önceki örneklerden bazıları basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-184">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="fc2f0-185">Örneğin, `DisplayInExcel` ' deki `worksheet` bildirimi `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet` yerine `Excel._Worksheet workSheet = excelApp.ActiveSheet` olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-185">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="fc2f0-186">Aynı yöntemde `AutoFit` ' a yapılan çağrılar, varsayılan değer olmadan açık atama gerektirir, çünkü `ExcelApp.Columns[1]` bir `Object` döndürür ve `AutoFit` bir Excel yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-186">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="fc2f0-187">Aşağıdaki kod, atama gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-187">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="fc2f0-188">Tür bilgilerini gömmek yerine varsayılan değer değiştirmek ve PIA 'leri kullanmak için, **Çözüm Gezgini** ' deki **Başvurular** düğümünü genişletin ve ardından **Microsoft. Office. Interop. Excel** veya **Microsoft. Office. Interop. Word**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-188">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="fc2f0-189">**Özellikler** penceresini göremiyorsanız **F4**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-189">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="fc2f0-190">Özellik listesine **birlikte çalışma türlerini katıştır** ' ı bulun ve değerini **false**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-190">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="fc2f0-191">Equivalently, bir komut isteminde [/Link](../../language-reference/compiler-options/link-compiler-option.md) yerine [/Reference](../../language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneğini kullanarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-191">Equivalently, you can compile by using the [/reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="fc2f0-192">Tabloya ek biçimlendirme eklemek için</span><span class="sxs-lookup"><span data-stu-id="fc2f0-192">To add additional formatting to the table</span></span>

1. <span data-ttu-id="fc2f0-193">@No__t-1 ' deki `AutoFit` olan iki çağrısı aşağıdaki ifadeyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-193">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="fc2f0-194">@No__t-0 yönteminde, hepsi isteğe bağlı yedi değer parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-194">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="fc2f0-195">Adlandırılmış ve isteğe bağlı bağımsız değişkenler hiçbiri, bazıları veya tümü için bağımsız değişkenler sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-195">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="fc2f0-196">Önceki ifadede, `Format` parametrelerinden yalnızca biri için bir bağımsız değişken sağlandı.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-196">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="fc2f0-197">@No__t-0 parametre listesindeki ilk parametre olduğundan, parametre adını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-197">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="fc2f0-198">Ancak, aşağıdaki kodda gösterildiği gibi, deyimin parametre adının dahil edilip edilmediğini anlamak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-198">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="fc2f0-199">Sonucu görmek için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-199">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="fc2f0-200">Diğer biçimler <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> numaralandırmasında listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-200">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="fc2f0-201">Adım 1 ' deki ifadesini, C# 3,0 ve önceki sürümlerde gerekli olan bağımsız değişkenleri gösteren aşağıdaki kodla karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-201">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="fc2f0-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc2f0-202">Example</span></span>

<span data-ttu-id="fc2f0-203">Aşağıdaki kod, tüm örneği göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-203">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="fc2f0-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2f0-204">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="fc2f0-205">tir</span><span class="sxs-lookup"><span data-stu-id="fc2f0-205">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="fc2f0-206">Dinamik tür kullanma</span><span class="sxs-lookup"><span data-stu-id="fc2f0-206">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="fc2f0-207">Adlandırılmış ve Isteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="fc2f0-207">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="fc2f0-208">Nasıl yapılır: Office Programlamada adlandırılmış ve Isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="fc2f0-208">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
