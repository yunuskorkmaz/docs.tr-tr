---
title: Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenler nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 36b5c8b49404606c8240d24953c3677d5612d30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714869"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="f439d-102">Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenler nasıl kullanılır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f439d-102">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="f439d-103">C# 4'te tanıtılan adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler, C# programlamada kolaylığı, esnekliği ve okunabilirliği artırır.</span><span class="sxs-lookup"><span data-stu-id="f439d-103">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="f439d-104">Ayrıca, bu özellikler Microsoft Office otomasyon API'leri gibi COM arabirimlerine erişimi büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f439d-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="f439d-105">Aşağıdaki örnekte, [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) yöntemi, sütun ve satır sayısı, biçimlendirme, kenarlıklar, yazı tipleri ve renkler gibi bir tablonun özelliklerini temsil eden on altı parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f439d-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="f439d-106">Çoğu zaman hepsi için belirli değerleri belirtmek istemediğiniz için on altı parametrenin tümü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f439d-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="f439d-107">Ancak, adlandırılmış ve isteğe bağlı bağımsız değişkenler olmadan, her parametre için bir değer veya yer tutucu değeri sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f439d-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="f439d-108">Adlandırılmış ve isteğe bağlı bağımsız değişkenlerle, yalnızca projeniz için gerekli parametreler için değerleri belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f439d-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="f439d-109">Bu yordamları tamamlamak için bilgisayarınızda Microsoft Office Word yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f439d-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="f439d-110">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f439d-110">To create a new console application</span></span>

1. <span data-ttu-id="f439d-111">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f439d-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="f439d-112">**Dosya** menüsünde **Yeni'yi**işaret edin ve ardından **Project'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f439d-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="f439d-113">**Şablonlar Kategorileri** bölmesinde **Visual C#** seçeneğini genişletin ve **ardından Windows'u**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f439d-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="f439d-114">**.NET Framework 4'ün** **Hedef Çerçeve** kutusunda göründüğünden emin olmak için **Şablonlar** bölmesinin üst bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f439d-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="f439d-115">**Şablonlar** bölmesinde Konsol **Uygulaması'nı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f439d-115">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="f439d-116">**Ad** alanına projeniz için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="f439d-116">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="f439d-117">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f439d-117">Click **OK**.</span></span>

     <span data-ttu-id="f439d-118">Yeni proje Çözüm **Gezgini'nde**görünür.</span><span class="sxs-lookup"><span data-stu-id="f439d-118">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="f439d-119">Başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="f439d-119">To add a reference</span></span>

1. <span data-ttu-id="f439d-120">**Çözüm Gezgini'nde,** projenizin adını sağ tıklatın ve ardından **Başvuru Ekle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f439d-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="f439d-121">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f439d-121">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="f439d-122">**.NET** sayfasında, **Bileşen Adı** listesinde **Microsoft.Office.Interop.Word'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="f439d-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="f439d-123">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f439d-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="f439d-124">Yönergeleri kullanarak gerekli eklemek için</span><span class="sxs-lookup"><span data-stu-id="f439d-124">To add necessary using directives</span></span>

1. <span data-ttu-id="f439d-125">**Çözüm Gezgini'nde,** *Program.cs* dosyasını sağ tıklatın ve ardından **Kodu Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f439d-125">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="f439d-126">Kod dosyasının üst bölümüne aşağıdaki `using` yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f439d-126">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="f439d-127">Word belgesinde metni görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="f439d-127">To display text in a Word document</span></span>

1. <span data-ttu-id="f439d-128">`Program` *Program.cs'daki*sınıfta, Word uygulaması ve Word belgesi oluşturmak için aşağıdaki yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f439d-128">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="f439d-129">[Ekle](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) yönteminin dört isteğe bağlı parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="f439d-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="f439d-130">Bu örnekte varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f439d-130">This example uses their default values.</span></span> <span data-ttu-id="f439d-131">Bu nedenle, arama deyiminde bağımsız değişken gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f439d-131">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="f439d-132">Belgede metnin nerede görüntüleneği ve hangi metnin görüntüleneleyeceğini tanımlamak için yöntemin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f439d-132">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="f439d-133">Uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f439d-133">To run the application</span></span>

1. <span data-ttu-id="f439d-134">Main'e aşağıdaki ifadeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f439d-134">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="f439d-135">Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f439d-135">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="f439d-136">Belirtilen metni içeren bir Word belgesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f439d-136">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="f439d-137">Metni tabloya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f439d-137">To change the text to a table</span></span>
  
1. <span data-ttu-id="f439d-138">Metni `ConvertToTable` bir tabloya bünyesine katmayı yapmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f439d-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="f439d-139">Yöntemon on altı isteğe bağlı parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="f439d-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="f439d-140">IntelliSense, aşağıdaki resimde gösterildiği gibi isteğe bağlı parametreleri parantez içine içine alar.</span><span class="sxs-lookup"><span data-stu-id="f439d-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![ConvertToTable yöntemi için parametrelerlistesi](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="f439d-142">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, yalnızca değiştirmek istediğiniz parametreler için değerleri belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f439d-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="f439d-143">Basit bir tablo oluşturmak için `DisplayInWord` yöntemin sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f439d-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="f439d-144">Bağımsız değişken, metin dizesindeki virgüllerin tablonun hücrelerini `range` birbirinden ayırdığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f439d-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="f439d-145">C#'ın önceki sürümlerinde, `ConvertToTable` çağrı, aşağıdaki kodda gösterildiği gibi, her parametre için bir başvuru bağımsız değişkeni gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f439d-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="f439d-146">Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f439d-146">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="f439d-147">Diğer parametrelerle denemeler yapmak için</span><span class="sxs-lookup"><span data-stu-id="f439d-147">To experiment with other parameters</span></span>

1. <span data-ttu-id="f439d-148">Tabloyu bir sütun ve üç satır olacak şekilde değiştirmek için, son satırı `DisplayInWord` aşağıdaki deyimle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın.</span><span class="sxs-lookup"><span data-stu-id="f439d-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="f439d-149">Tablo için önceden tanımlanmış bir biçim belirtmek için, son satırı `DisplayInWord` aşağıdaki ifadeyle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın.</span><span class="sxs-lookup"><span data-stu-id="f439d-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="f439d-150">Biçim, [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) sabitlerinden herhangi biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="f439d-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="f439d-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="f439d-151">Example</span></span>

<span data-ttu-id="f439d-152">Aşağıdaki kod tam örneği içerir:</span><span class="sxs-lookup"><span data-stu-id="f439d-152">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="f439d-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f439d-153">See also</span></span>

- [<span data-ttu-id="f439d-154">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f439d-154">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
