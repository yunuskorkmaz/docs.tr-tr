---
title: 'Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişin- C# Programlama Kılavuzu'
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
ms.openlocfilehash: 19fff39969933baa2510458400cabf9646e0c48d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589130"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="05d6a-102">Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişin (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="05d6a-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>

<span data-ttu-id="05d6a-103">Görselde C# Office API nesnelerine erişimi basitleştiren özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="05d6a-104">Yeni özellikler adlandırılmış ve isteğe bağlı bağımsız değişkenler, yeni bir tür adı `dynamic`ve com yöntemlerindeki başvuru parametrelerine bağımsız değişkenleri değer parametreleri gibi geçirme özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="05d6a-105">Bu konu başlığında, Microsoft Office bir Excel çalışma sayfası oluşturan ve görüntüleyen kod yazmak için yeni özellikleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="05d6a-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="05d6a-106">Daha sonra, Excel çalışma sayfasına bağlı bir simge içeren bir Office Word belgesi eklemek için kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="05d6a-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="05d6a-107">Bu yönergeyi tamamlamak için, bilgisayarınızda yüklü Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya sonraki sürümlerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="05d6a-108">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="05d6a-108">To create a new console application</span></span>

1. <span data-ttu-id="05d6a-109">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="05d6a-110">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="05d6a-111">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="05d6a-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="05d6a-112">**Yüklü şablonlar** bölmesinde, **görsel C#** ' i genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="05d6a-113">**.NET Framework 4** ' ün (veya sonraki bir sürüm) hedef çerçeve olarak seçildiğinden emin olmak Için **Yeni proje** iletişim kutusunun üst kısmına bakın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="05d6a-114">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="05d6a-115">**Ad** alanına projeniz için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="05d6a-116">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-116">Click **OK**.</span></span>

     <span data-ttu-id="05d6a-117">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="05d6a-118">Başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="05d6a-118">To add references</span></span>

1. <span data-ttu-id="05d6a-119">**Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="05d6a-120">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="05d6a-121">**Derlemeler** sayfasında, **bileşen adı** listesinde **Microsoft. Office. Interop. Word** ' ü seçin ve ardından CTRL tuşunu basılı tutarak **Microsoft. Office. Interop. Excel**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="05d6a-122">Derlemeleri görmüyorsanız, bunların yüklendiğinden ve görüntülendiklerinden emin olmanız gerekebilir (bkz [. nasıl yapılır: Office birincil birlikte çalışma derlemelerini](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)yükler)</span><span class="sxs-lookup"><span data-stu-id="05d6a-122">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>

3. <span data-ttu-id="05d6a-123">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="05d6a-124">Gerekli yönergeleri kullanarak ekleme</span><span class="sxs-lookup"><span data-stu-id="05d6a-124">To add necessary using directives</span></span>

1. <span data-ttu-id="05d6a-125">**Çözüm Gezgini**, **program.cs** dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>

2. <span data-ttu-id="05d6a-126">Aşağıdaki `using` yönergeleri kod dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-126">Add the following `using` directives to the top of the code file.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="05d6a-127">Banka hesaplarının bir listesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="05d6a-127">To create a list of bank accounts</span></span>

1. <span data-ttu-id="05d6a-128">Aşağıdaki sınıf tanımını `Program` sınıfının altına **program.cs**yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-128">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="05d6a-129">İki hesap içeren bir `Main` `bankAccounts` liste oluşturmak için yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-129">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="05d6a-130">Excel 'e hesap bilgilerini veren bir yöntem bildirmek için</span><span class="sxs-lookup"><span data-stu-id="05d6a-130">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="05d6a-131">Bir Excel çalışma sayfası ayarlamak için `Program` aşağıdaki yöntemi sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-131">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="05d6a-132">Yöntemin <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> belirli bir şablonu belirtmek için isteğe bağlı bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-132">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="05d6a-133">4 ' te C# yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız bu parametreye ilişkin bağımsız değişkeni atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="05d6a-133">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="05d6a-134">Aşağıdaki kodda bir bağımsız değişken gönderilmediğinden, `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05d6a-134">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="05d6a-135">Önceki sürümlerindeki eşdeğer ifade, bir yer C# tutucu bağımsız değişkeni gerektirir: `ExcelApp.Workbooks.Add(Type.Missing)`.</span><span class="sxs-lookup"><span data-stu-id="05d6a-135">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="05d6a-136">Aşağıdaki kodu sonuna `DisplayInExcel`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-136">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="05d6a-137">Kod, çalışma sayfasının ilk satırının ilk iki sütununa değer ekler.</span><span class="sxs-lookup"><span data-stu-id="05d6a-137">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="05d6a-138">Aşağıdaki kodu sonuna `DisplayInExcel`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-138">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="05d6a-139">`foreach` Döngü, hesap listesindeki bilgileri, çalışma sayfasının Art arda gelen satırlarının ilk iki sütununa yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-139">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="05d6a-140">Sütunun genişliğini içeriğe sığacak şekilde ayarlamak `DisplayInExcel` için aşağıdaki kodu sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-140">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="05d6a-141">Önceki sürümleri bu C# işlemler için açık atama gerektirir, çünkü `ExcelApp.Columns[1]` bir `Object`, ve `AutoFit` bir Excel <xref:Microsoft.Office.Interop.Excel.Range> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-141">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="05d6a-142">Aşağıdaki satırlarda atama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-142">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="05d6a-143">C#4 ve sonraki sürümlerde, derleme [/Link](../../language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği `Object` tarafından `dynamic` başvuruluyorsa veya equivalently, Excel **birlikte çalışma türleri** özelliği true olarak ayarlandıysa, geri döndürülen öğesini otomatik olarak dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="05d6a-143">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="05d6a-144">True, bu özellik için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-144">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="05d6a-145">Projeyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="05d6a-145">To run the project</span></span>

1. <span data-ttu-id="05d6a-146">Aşağıdaki satırı sonuna `Main`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-146">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="05d6a-147">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-147">Press CTRL+F5.</span></span>

     <span data-ttu-id="05d6a-148">İki hesaptan gelen verileri içeren bir Excel çalışma sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-148">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="05d6a-149">Word belgesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="05d6a-149">To add a Word document</span></span>

1. <span data-ttu-id="05d6a-150">C# 4 ve sonraki sürümlerin, Office programlama 'yi geliştiren ek yollarını göstermek için aşağıdaki kod bir Word uygulaması açar ve Excel çalışma sayfasına bağlanan bir simge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05d6a-150">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="05d6a-151">Daha sonra `CreateIconInWordDoc`Bu adımda `Program` sunulan yöntemi sınıfına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-151">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="05d6a-152">`CreateIconInWordDoc`, ve <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>için metot çağrılarının karmaşıklığını azaltmak için adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-152">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="05d6a-153">Bu çağrılar, başvuru parametrelerine sahip COM yöntemlerine yapılan C# çağrıları kolaylaştıran 4 ' te tanıtılan iki yeni özelliği dahil ediyor.</span><span class="sxs-lookup"><span data-stu-id="05d6a-153">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="05d6a-154">İlk olarak, başvuru parametrelerine bağımsız değişkenleri değer parametreleriniz gibi gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-154">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="05d6a-155">Diğer bir deyişle, her başvuru parametresi için bir değişken oluşturmadan doğrudan değerleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-155">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="05d6a-156">Derleyici bağımsız değişken değerlerini tutacak geçici değişkenler oluşturur ve çağrıdan geri döndüğünüzde değişkenleri atar.</span><span class="sxs-lookup"><span data-stu-id="05d6a-156">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="05d6a-157">İkinci olarak, bağımsız değişken listesindeki `ref` anahtar sözcüğü atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-157">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="05d6a-158">`Add` Yönteminin tümü isteğe bağlı dört başvuru parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-158">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="05d6a-159">C# 4,0 ve sonraki sürümlerde, varsayılan değerlerini kullanmak istiyorsanız parametrelerin herhangi biri veya tümü için bağımsız değişkenleri atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-159">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="05d6a-160">C# 3,0 ve önceki sürümlerde, her bir parametre için bir bağımsız değişken sağlanmalı ve parametreler başvuru parametreleri olduğundan bağımsız değişken bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-160">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="05d6a-161">`PasteSpecial` Yöntemi panonun içeriğini ekler.</span><span class="sxs-lookup"><span data-stu-id="05d6a-161">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="05d6a-162">Yönteminde, hepsi isteğe bağlı yedi başvuru parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-162">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="05d6a-163">Aşağıdaki kod, bu iki öğenin bağımsız değişkenlerini belirtir: `Link`, pano içeriklerinin kaynağına bir bağlantı oluşturmak ve `DisplayAsIcon`bağlantıyı bir simge olarak göstermek için.</span><span class="sxs-lookup"><span data-stu-id="05d6a-163">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="05d6a-164">C# 4,0 ve sonraki sürümlerde, bu ikisi için adlandırılmış bağımsız değişkenleri kullanabilir ve diğerlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-164">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="05d6a-165">Bunların başvuru parametreleri olmasına karşın, `ref` anahtar sözcüğünü kullanmanız veya bağımsız değişken olarak gönderilmek üzere değişkenler oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="05d6a-165">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="05d6a-166">Değerleri doğrudan gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-166">You can send the values directly.</span></span> <span data-ttu-id="05d6a-167">C# 3,0 ve önceki sürümlerde, her başvuru parametresi için bir değişken bağımsız değişkeni sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-167">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="05d6a-168">Dilin C# 3,0 ve önceki sürümlerinde, aşağıdaki daha karmaşık kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-168">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="05d6a-169">Aşağıdaki ifadesini sonuna `Main`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-169">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="05d6a-170">Aşağıdaki ifadesini sonuna `DisplayInExcel`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-170">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="05d6a-171">`Copy` Yöntemi, çalışma sayfasını panoya ekler.</span><span class="sxs-lookup"><span data-stu-id="05d6a-171">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="05d6a-172">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-172">Press CTRL+F5.</span></span>

     <span data-ttu-id="05d6a-173">Bir simge içeren bir Word belgesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-173">A Word document appears that contains an icon.</span></span> <span data-ttu-id="05d6a-174">Çalışma sayfasını ön plana getirmek için simgeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-174">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="05d6a-175">Birlikte çalışma türlerini katıştır özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="05d6a-175">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="05d6a-176">Çalışma zamanında birincil birlikte çalışma derlemesi (PIA) gerektirmeyen bir COM türünü çağırdığınızda ek geliştirmeler yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-176">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="05d6a-177">PIA 'ların bağımlılığını kaldırmak sürüm bağımsızlık ve daha kolay dağıtıma neden olur.</span><span class="sxs-lookup"><span data-stu-id="05d6a-177">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="05d6a-178">PIA olmadan programlamanın avantajları hakkında daha fazla bilgi için bkz [. İzlenecek yol: Yönetilen derlemelerden](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)türler ekleme.</span><span class="sxs-lookup"><span data-stu-id="05d6a-178">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>

     <span data-ttu-id="05d6a-179">Ayrıca, gerekli ve com yöntemleri tarafından döndürülen türler `dynamic` `Object`yerine türü kullanılarak gösterilebildiğinden programlama daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="05d6a-179">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="05d6a-180">Türü `dynamic` olan değişkenler çalışma zamanına kadar değerlendirilmez ve bu da açık atama gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-180">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="05d6a-181">Daha fazla bilgi için bkz. [dinamik tür kullanımı](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="05d6a-181">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="05d6a-182">4 C# ' te, PIA kullanımı yerine tür bilgilerini katıştırma varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-182">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="05d6a-183">Bu varsayılan nedenle, açık atama gerekli olmadığından önceki örneklerden bazıları basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-183">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="05d6a-184">Örneğin, `worksheet` içindeki `DisplayInExcel` bildirimi yerine `Excel._Worksheet workSheet = excelApp.ActiveSheet` olarak`Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`yazılır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-184">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="05d6a-185">Aynı yöntemde yapılan `AutoFit` çağrılar, varsayılan değer olmadan açık atama gerektirir, çünkü `ExcelApp.Columns[1]` bir `Object`, döndürür ve `AutoFit` bir Excel yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-185">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="05d6a-186">Aşağıdaki kod, atama gösterir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-186">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="05d6a-187">Tür bilgilerini gömmek yerine varsayılan değer değiştirmek ve PIA 'leri kullanmak için, **Çözüm Gezgini** ' deki **Başvurular** düğümünü genişletin ve ardından **Microsoft. Office. Interop. Excel** veya **Microsoft. Office. Interop. Word**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-187">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="05d6a-188">**Özellikler** penceresini göremiyorsanız **F4**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-188">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="05d6a-189">Özellik listesine **birlikte çalışma türlerini katıştır** ' ı bulun ve değerini **false**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-189">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="05d6a-190">Equivalently, bir komut isteminde [/Link](../../language-reference/compiler-options/link-compiler-option.md) yerine [/Reference](../../language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneğini kullanarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-190">Equivalently, you can compile by using the [/reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="05d6a-191">Tabloya ek biçimlendirme eklemek için</span><span class="sxs-lookup"><span data-stu-id="05d6a-191">To add additional formatting to the table</span></span>

1. <span data-ttu-id="05d6a-192">`AutoFit` İçindeki`DisplayInExcel` iki çağrısı aşağıdaki ifadesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="05d6a-192">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="05d6a-193"><xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Yöntemi, hepsi isteğe bağlı yedi değer parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-193">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="05d6a-194">Adlandırılmış ve isteğe bağlı bağımsız değişkenler hiçbiri, bazıları veya tümü için bağımsız değişkenler sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-194">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="05d6a-195">Önceki ifadede, parametrelerden `Format`yalnızca biri için bir bağımsız değişken sağlanır.</span><span class="sxs-lookup"><span data-stu-id="05d6a-195">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="05d6a-196">, `Format` Parametre listesindeki ilk parametre olduğundan, parametre adını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="05d6a-196">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="05d6a-197">Ancak, aşağıdaki kodda gösterildiği gibi, deyimin parametre adının dahil edilip edilmediğini anlamak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-197">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="05d6a-198">Sonucu görmek için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-198">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="05d6a-199">Diğer biçimler, <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> numaralandırmada listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-199">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="05d6a-200">Adım 1 ' deki ifadesini, C# 3,0 ve önceki sürümlerde gerekli olan bağımsız değişkenleri gösteren aşağıdaki kodla karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="05d6a-200">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="05d6a-201">Örnek</span><span class="sxs-lookup"><span data-stu-id="05d6a-201">Example</span></span>

<span data-ttu-id="05d6a-202">Aşağıdaki kod, tüm örneği göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="05d6a-202">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="05d6a-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05d6a-203">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="05d6a-204">dynamic</span><span class="sxs-lookup"><span data-stu-id="05d6a-204">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="05d6a-205">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="05d6a-205">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="05d6a-206">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="05d6a-206">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="05d6a-207">Nasıl yapılır: Office Programlamada adlandırılmış ve Isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="05d6a-207">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
