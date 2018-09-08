---
title: 'Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: f86509b7257f25e8faaadfc107ad70ca794aeee0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129752"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="afa90-102">Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="afa90-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="afa90-103">Adlandırılmış bağımsız değişkenler ve sunulan isteğe bağlı bağımsız değişkenlere [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], kolaylık, esneklik ve C# programlama okunabilirliği geliştirmek.</span><span class="sxs-lookup"><span data-stu-id="afa90-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="afa90-104">Ayrıca, bu özellikler, Microsoft Office Otomasyon API'leri gibi COM arabirimlerine erişim büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="afa90-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="afa90-105">Aşağıdaki örnekte, yöntem [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) on altı gibi sütun ve biçimlendirme, satır sayısını sınırlayan bir tablonun özellikleri temsil eden parametreleri, yazı tiplerini ve renkleri vardır.</span><span class="sxs-lookup"><span data-stu-id="afa90-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="afa90-106">Çoğu zaman hepsi için belirli değerler belirtmek istemiyorsanız çünkü tüm on altı, isteğe bağlı parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="afa90-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="afa90-107">Ancak, adlandırılmış ve isteğe bağlı bağımsız değişkenler bir değer veya bir yer tutucu değerini her parametre için sağlanan gerekir.</span><span class="sxs-lookup"><span data-stu-id="afa90-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="afa90-108">Adlandırılmış ve isteğe bağlı bağımsız değişkenleri ile projeniz için gerekli olan parametreleri için değerler belirtin.</span><span class="sxs-lookup"><span data-stu-id="afa90-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="afa90-109">Bu yordamları tamamlamak için Microsoft Office Word bilgisayarınızda yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="afa90-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="afa90-110">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="afa90-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="afa90-111">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="afa90-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="afa90-112">Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="afa90-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="afa90-113">İçinde **şablon kategorileri** bölmesini genişletin **Visual C#** ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="afa90-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="afa90-114">Üst konum **şablonları** emin olmak için bölmesinde **.NET Framework 4** görünür **hedef Framework'ü** kutusu.</span><span class="sxs-lookup"><span data-stu-id="afa90-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="afa90-115">İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="afa90-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="afa90-116">Projeniz için bir ad yazın **adı** alan.</span><span class="sxs-lookup"><span data-stu-id="afa90-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="afa90-117">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="afa90-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="afa90-118">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="afa90-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="afa90-119">Başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="afa90-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="afa90-120">İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="afa90-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="afa90-121">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="afa90-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="afa90-122">Üzerinde **.NET** sayfasında **Microsoft.Office.Interop.Word** içinde **bileşen adı** listesi.</span><span class="sxs-lookup"><span data-stu-id="afa90-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="afa90-123">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="afa90-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="afa90-124">Eklemek için gerekli yönergeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="afa90-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="afa90-125">İçinde **Çözüm Gezgini**, sağ **Program.cs** dosya ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="afa90-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="afa90-126">Aşağıdaki `using` kod dosyasının en üstüne yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="afa90-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="afa90-127">Word belgesinde metni görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="afa90-127">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="afa90-128">İçinde `Program` sınıfı Program.cs içinde bir Word uygulaması ve bir Word belgesi oluşturmak için aşağıdaki yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afa90-128">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="afa90-129">[Ekle](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) yöntemi dört isteğe bağlı parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="afa90-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="afa90-130">Bu örnek, varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="afa90-130">This example uses their default values.</span></span> <span data-ttu-id="afa90-131">Bu nedenle, arama deyiminde hiçbir bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="afa90-131">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  <span data-ttu-id="afa90-132">Aşağıdaki kod, belgede metin görüntüleneceği yeri ve görüntülenecek metni tanımlamak için yöntem sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afa90-132">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a><span data-ttu-id="afa90-133">Uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="afa90-133">To run the application</span></span>  
  
1.  <span data-ttu-id="afa90-134">Aşağıdaki deyim, ana ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afa90-134">Add the following statement to Main.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  <span data-ttu-id="afa90-135">Projeyi çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="afa90-135">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="afa90-136">Belirtilen metni içeren bir Word belgesi görünür.</span><span class="sxs-lookup"><span data-stu-id="afa90-136">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="afa90-137">Metin bir tabloya dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="afa90-137">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="afa90-138">Kullanım `ConvertToTable` bir tabloda metin kapsamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afa90-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="afa90-139">Yöntemi, on altı isteğe bağlı parametre yok.</span><span class="sxs-lookup"><span data-stu-id="afa90-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="afa90-140">IntelliSense aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreler köşeli parantez içine alır.</span><span class="sxs-lookup"><span data-stu-id="afa90-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="afa90-141">![ConvertToTable yönteminin listesi. ](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="afa90-141">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="afa90-142">ConvertToTable parametreleri</span><span class="sxs-lookup"><span data-stu-id="afa90-142">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="afa90-143">Adlandırılmış ve isteğe bağlı bağımsız değişkenler yalnızca değiştirmek istediğiniz parametreleri için değerleri belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="afa90-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="afa90-144">Yönteminin sonuna aşağıdaki kodu ekleyin `DisplayInWord` basit bir tablo oluşturun.</span><span class="sxs-lookup"><span data-stu-id="afa90-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="afa90-145">Metinde virgüller de dize bağımsız değişkeni belirtir `range` tablo hücrelerini ayırın.</span><span class="sxs-lookup"><span data-stu-id="afa90-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     <span data-ttu-id="afa90-146">C#, çağrısı'nın önceki sürümlerinde `ConvertToTable` aşağıdaki kodda gösterildiği gibi her parametre için bir başvuru bağımsız değişkeni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="afa90-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  <span data-ttu-id="afa90-147">Projeyi çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="afa90-147">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="afa90-148">Diğer parametreler ile denemek için</span><span class="sxs-lookup"><span data-stu-id="afa90-148">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="afa90-149">Bir sütun ve üç satır sahip olacak şekilde değiştirmek için son satırında değiştirin `DisplayInWord` CTRL + F5'e yazın ve aşağıdaki deyimi.</span><span class="sxs-lookup"><span data-stu-id="afa90-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  <span data-ttu-id="afa90-150">Tablo için önceden tanımlanmış bir biçimi belirtmek için son satırında değiştirin `DisplayInWord` CTRL + F5'e yazın ve aşağıdaki deyimi.</span><span class="sxs-lookup"><span data-stu-id="afa90-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="afa90-151">Biçim herhangi biri olabilir [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) sabitler.</span><span class="sxs-lookup"><span data-stu-id="afa90-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a><span data-ttu-id="afa90-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="afa90-152">Example</span></span>  
 <span data-ttu-id="afa90-153">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="afa90-153">The following code includes the full example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="afa90-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afa90-154">See Also</span></span>

- [<span data-ttu-id="afa90-155">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="afa90-155">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
