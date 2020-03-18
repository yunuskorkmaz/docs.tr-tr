---
title: Office interop nesnelerine nasıl erişilir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: b5d2da011ec6318c8b07f1eb4d383a4d56488239
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700841"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a><span data-ttu-id="ac72e-102">Office interop nesnelerine nasıl erişilir (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ac72e-102">How to access Office interop objects (C# Programming Guide)</span></span>

<span data-ttu-id="ac72e-103">C#, Office API nesnelerine erişimi kolaylaştıran özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-103">C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="ac72e-104">Yeni özellikler arasında adlandırılmış ve isteğe `dynamic`bağlı bağımsız değişkenler, adı verilen yeni bir tür ve değer parametreleri yatmaktadır gibi COM yöntemlerinde başvuru parametrelerine bağımsız değişkenler geçirebilme yeteneği yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="ac72e-105">Bu konuda, microsoft office excel çalışma sayfası oluşturan ve görüntüleyen kod yazmak için yeni özellikleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ac72e-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="ac72e-106">Daha sonra, Excel çalışma sayfasına bağlı bir simge içeren bir Office Word belgesi eklemek için kod yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="ac72e-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="ac72e-107">Bu izbiyi tamamlamak için, Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya daha sonraki sürümlerinin bilgisayarınızda yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="ac72e-108">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ac72e-108">To create a new console application</span></span>

1. <span data-ttu-id="ac72e-109">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="ac72e-110">**Dosya** menüsünde **Yeni'yi**işaret edin ve ardından **Project'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="ac72e-111">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="ac72e-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="ac72e-112">Yüklü **Şablonlar** bölmesinde Visual **C#** seçeneğini genişletin ve ardından **Windows'u**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="ac72e-113">**.NET Framework 4'ün** (veya sonraki sürümün) hedef çerçeve olarak seçildiğinden emin olmak için **Yeni Proje** iletişim kutusunun en üstüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="ac72e-114">**Şablonlar** bölmesinde Konsol **Uygulaması'nı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="ac72e-115">**Ad** alanına projeniz için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="ac72e-116">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-116">Click **OK**.</span></span>

     <span data-ttu-id="ac72e-117">Yeni proje Çözüm **Gezgini'nde**görünür.</span><span class="sxs-lookup"><span data-stu-id="ac72e-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="ac72e-118">Referans eklemek için</span><span class="sxs-lookup"><span data-stu-id="ac72e-118">To add references</span></span>

1. <span data-ttu-id="ac72e-119">**Çözüm Gezgini'nde,** projenizin adını sağ tıklatın ve ardından **Başvuru Ekle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="ac72e-120">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="ac72e-121">**Derlemeler** sayfasında, **Bileşen Adı** listesinde **Microsoft.Office.Interop.Word'u** seçin ve ardından CTRL tuşunu basılı tutun ve **Microsoft.Office.Interop.Excel'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="ac72e-122">Derlemeleri görmüyorsanız, bunların yüklendiğinden ve görüntülendiğinden emin olmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-122">If you do not see the assemblies, you may need to ensure they are installed and displayed.</span></span> <span data-ttu-id="ac72e-123">[Bkz. Nasıl: Office Birincil Interop Derlemelerini Yükleyin.](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)</span><span class="sxs-lookup"><span data-stu-id="ac72e-123">See [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span></span>

3. <span data-ttu-id="ac72e-124">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="ac72e-125">Yönergeleri kullanarak gerekli eklemek için</span><span class="sxs-lookup"><span data-stu-id="ac72e-125">To add necessary using directives</span></span>

1. <span data-ttu-id="ac72e-126">**Çözüm Gezgini'nde,** *Program.cs* dosyasını sağ tıklatın ve ardından **Kodu Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="ac72e-127">Kod dosyasının üst bölümüne aşağıdaki `using` yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac72e-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="ac72e-128">Banka hesaplarının listesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ac72e-128">To create a list of bank accounts</span></span>

1. <span data-ttu-id="ac72e-129">Aşağıdaki sınıf tanımını **Program.cs**yapıştırın. `Program`</span><span class="sxs-lookup"><span data-stu-id="ac72e-129">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="ac72e-130">İki hesap içeren `Main` bir `bankAccounts` liste oluşturmak için yönteme aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-130">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="ac72e-131">Hesap bilgilerini Excel'e dışa aktarma yöntemini bildirmek için</span><span class="sxs-lookup"><span data-stu-id="ac72e-131">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="ac72e-132">Excel çalışma sayfası `Program` ayarlamak için sınıfa aşağıdaki yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-132">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="ac72e-133">Yöntem, <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> belirli bir şablonu belirtmek için isteğe bağlı bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-133">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="ac72e-134">C# 4'te yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız, bu parametrenin bağımsız değişkenini atlayabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac72e-134">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="ac72e-135">Aşağıdaki kodda bağımsız değişken gönderilmediği için varsayılan `Add` şablonu kullanır ve yeni bir çalışma kitabı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac72e-135">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="ac72e-136">C# önceki sürümlerinde eşdeğer ifade bir yer `ExcelApp.Workbooks.Add(Type.Missing)`tutucu argüman gerektirir: .</span><span class="sxs-lookup"><span data-stu-id="ac72e-136">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="ac72e-137">'nin sonuna aşağıdaki kodu `DisplayInExcel`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-137">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="ac72e-138">Kod, çalışma sayfasının ilk satırının ilk iki sütununa değerler ekler.</span><span class="sxs-lookup"><span data-stu-id="ac72e-138">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="ac72e-139">'nin sonuna aşağıdaki kodu `DisplayInExcel`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="ac72e-140">Döngü, `foreach` hesap listesindeki bilgileri çalışma sayfasının ardışık satırlarının ilk iki sütununa koyar.</span><span class="sxs-lookup"><span data-stu-id="ac72e-140">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="ac72e-141">İçeriğe uyacak şekilde `DisplayInExcel` sütun gençlerini ayarlamak için sonuna şeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-141">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="ac72e-142">C# önceki `ExcelApp.Columns[1]` sürümleri, bir `Object`,, döndürür `AutoFit` ve <xref:Microsoft.Office.Interop.Excel.Range> bir Excel yöntemi olduğundan bu işlemler için açık döküm gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-142">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="ac72e-143">Aşağıdaki satırlarda döküm göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-143">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="ac72e-144">C# 4 ve sonraki sürümler, `Object` `dynamic` derleme [-link](../../language-reference/compiler-options/link-compiler-option.md) derleyicisi seçeneği tarafından başvurulsa veya excel **Gömme Interop Türleri** özelliği doğru ayarlanmışsa, döndürülen leri otomatik olarak dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ac72e-144">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [-link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="ac72e-145">True, bu özellik için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-145">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="ac72e-146">Projeyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ac72e-146">To run the project</span></span>

1. <span data-ttu-id="ac72e-147">'nin sonuna aşağıdaki satırı `Main`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-147">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="ac72e-148">CTRL+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-148">Press CTRL+F5.</span></span>

     <span data-ttu-id="ac72e-149">İki hesaptaki verileri içeren bir Excel çalışma sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-149">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="ac72e-150">Word belgesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="ac72e-150">To add a Word document</span></span>

1. <span data-ttu-id="ac72e-151">C# 4 ve sonraki sürümlerin Office programlamasını geliştirdiği ek yolları göstermek için, aşağıdaki kod bir Word uygulaması açar ve Excel çalışma sayfasına bağlanan bir simge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac72e-151">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="ac72e-152">Yapıştır metodu, `CreateIconInWordDoc`daha sonra bu `Program` adımda sınıfa verilir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-152">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="ac72e-153">`CreateIconInWordDoc`çağıran yöntemin karmaşıklığını azaltmak için <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> adlandırılmış ve <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>isteğe bağlı bağımsız değişkenler kullanır ve.</span><span class="sxs-lookup"><span data-stu-id="ac72e-153">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="ac72e-154">Bu çağrılar, c# 4'te tanıtılan ve başvuru parametreleri olan COM yöntemlerine yapılan çağrıları basitleştiren iki yeni özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-154">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="ac72e-155">İlk olarak, bağımsız değişkenleri referans parametrelerine değer parametreleri gibi gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-155">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="ac72e-156">Diğer bir diğer olarak, her başvuru parametresi için bir değişken oluşturmadan değerleri doğrudan gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-156">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="ac72e-157">Derleyici bağımsız değişken değerlerini tutmak için geçici değişkenler oluşturur ve çağrıdan döndüğünüzde değişkenleri atar.</span><span class="sxs-lookup"><span data-stu-id="ac72e-157">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="ac72e-158">İkinci olarak, bağımsız değişken `ref` listesindeki anahtar kelimeyi atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-158">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="ac72e-159">Yöntem, `Add` hepsi isteğe bağlı olan dört başvuru parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-159">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="ac72e-160">C# 4.0 ve sonraki sürümlerde, varsayılan değerlerini kullanmak istiyorsanız parametrelerin herhangi birini veya tümünün bağımsız değişkenlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-160">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="ac72e-161">C# 3.0 ve önceki sürümlerde, her parametre için bir bağımsız değişken sağlanmalıdır ve parametreler referans parametreleri olduğundan bağımsız değişken bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-161">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="ac72e-162">Yöntem, `PasteSpecial` Pano içeriğini ekler.</span><span class="sxs-lookup"><span data-stu-id="ac72e-162">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="ac72e-163">Yöntem, hepsi isteğe bağlı yedi başvuru parametrevardır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-163">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="ac72e-164">Aşağıdaki kod, iki tanesi için bağımsız `Link`değişkenler belirtir: , Pano içeriğinin kaynağına bir bağlantı oluşturmak ve `DisplayAsIcon`, bağlantıyı bir simge olarak görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="ac72e-164">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="ac72e-165">C# 4.0 ve sonraki sürümlerde, bu ikisi için adlandırılmış bağımsız değişkenleri kullanabilir ve diğerlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-165">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="ac72e-166">Bunlar başvuru parametreleri olsa da, anahtar `ref` kelimeyi kullanmanız veya bağımsız değişken olarak göndermek için değişkenler oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ac72e-166">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="ac72e-167">Değerleri doğrudan gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-167">You can send the values directly.</span></span> <span data-ttu-id="ac72e-168">C# 3.0 ve önceki sürümlerde, her başvuru parametresi için değişken bir bağımsız değişken sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-168">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="ac72e-169">C# 3.0 ve dilin önceki sürümlerinde aşağıdaki daha karmaşık kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-169">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="ac72e-170">'nin sonuna aşağıdaki ifadeyi `Main`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-170">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="ac72e-171">'nin sonuna aşağıdaki ifadeyi `DisplayInExcel`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-171">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="ac72e-172">Yöntem, `Copy` çalışma sayfasını Panoya ekler.</span><span class="sxs-lookup"><span data-stu-id="ac72e-172">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="ac72e-173">CTRL+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-173">Press CTRL+F5.</span></span>

     <span data-ttu-id="ac72e-174">Bir simge içeren bir Word belgesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-174">A Word document appears that contains an icon.</span></span> <span data-ttu-id="ac72e-175">Çalışma sayfasını ön plana çıkarmak için simgeyi çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-175">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="ac72e-176">Embed Interop Types özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ac72e-176">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="ac72e-177">Çalışma zamanında birincil interop derlemesi (PIA) gerektirmeyen bir COM türünü çağırdığınızda ek geliştirmeler mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ac72e-177">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="ac72e-178">PIAs bağımlılığını kaldırmak sürüm bağımsızlığı ve daha kolay dağıtım sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac72e-178">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="ac72e-179">PI'siz programlamanın avantajları hakkında daha fazla bilgi için [Bkz. Walkthrough: Yönetilen Derlemelerden Türleri Gömme.](../../../standard/assembly/embed-types-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="ac72e-179">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="ac72e-180">Buna ek olarak, com yöntemleri ile gerekli ve döndürülen türleri yerine türü `dynamic` kullanılarak temsil `Object`edilebilir, çünkü programlama daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-180">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="ac72e-181">Türü `dynamic` olan değişkenler çalışma süresine kadar değerlendirilmez, bu da açık döküm ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-181">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="ac72e-182">Daha fazla bilgi için [bkz.](../types/using-type-dynamic.md)</span><span class="sxs-lookup"><span data-stu-id="ac72e-182">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="ac72e-183">C# 4'te, PI'ler kullanmak yerine tür bilgilerini katıştırma varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-183">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="ac72e-184">Bu varsayılan nedenle, açık döküm gerekli olmadığından önceki örneklerden bazıları basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-184">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="ac72e-185">Örneğin, `worksheet` in `DisplayInExcel` bildirimi `Excel._Worksheet workSheet = excelApp.ActiveSheet` yerine `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`yazılır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-185">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="ac72e-186">`AutoFit` Aynı yöntemde yapılan aramalar da varsayılan olmadan açık `ExcelApp.Columns[1]` döküm `Object`gerektirir, `AutoFit` çünkü bir , bir Excel yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac72e-186">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="ac72e-187">Aşağıdaki kod döküm gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-187">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="ac72e-188">Varsayılanı değiştirmek ve tür bilgilerini katıştırmak yerine PI'leri kullanmak için **Solution Explorer'daki** **Başvuru** düğümünü genişletin ve ardından **Microsoft.Office.Interop.Excel** veya **Microsoft.Office.Interop.Word'ü**seçin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-188">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="ac72e-189">**Özellikler** penceresini göremiyorsanız **F4**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-189">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="ac72e-190">Özellikler listesinde **Embed Interop Türlerini** bulun ve değerini **False**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-190">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="ac72e-191">Buna benzer şekilde, komut isteminde [-link](../../language-reference/compiler-options/link-compiler-option.md) yerine [-referans](../../language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneğini kullanarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-191">Equivalently, you can compile by using the [-reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [-link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="ac72e-192">Tabloya ek biçimlendirme eklemek için</span><span class="sxs-lookup"><span data-stu-id="ac72e-192">To add additional formatting to the table</span></span>

1. <span data-ttu-id="ac72e-193">İki aramayı `AutoFit` aşağıdaki `DisplayInExcel` ifadeyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ac72e-193">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="ac72e-194">Yöntem, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> hepsi isteğe bağlı yedi değer parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="ac72e-194">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="ac72e-195">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, bunların hiçbiri, bazıları veya tümü için bağımsız değişkensağlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac72e-195">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="ac72e-196">Önceki deyimde, bir bağımsız değişken parametrelerden yalnızca `Format`biri için verilir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-196">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="ac72e-197">Parametre listesindeki ilk parametre `Format` olduğundan, parametre adını sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ac72e-197">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="ac72e-198">Ancak, aşağıdaki kodda gösterildiği gibi, parametre adı dahil edilip edilmediğini anlamak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-198">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="ac72e-199">Sonucu görmek için CTRL+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-199">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="ac72e-200">Diğer biçimler numaralandırmada <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> listelenir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-200">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="ac72e-201">1. adımdaki ifadeyi, C# 3.0 ve önceki sürümlerde gerekli olan bağımsız değişkenleri gösteren aşağıdaki kodla karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="ac72e-201">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="ac72e-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac72e-202">Example</span></span>

<span data-ttu-id="ac72e-203">Aşağıdaki kod tam örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac72e-203">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="ac72e-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac72e-204">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="ac72e-205">Dinamik</span><span class="sxs-lookup"><span data-stu-id="ac72e-205">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="ac72e-206">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="ac72e-206">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="ac72e-207">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ac72e-207">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="ac72e-208">Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="ac72e-208">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
