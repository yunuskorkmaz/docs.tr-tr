---
title: "Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a453699591397224435fba1e602c305f18e84a11
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="539ca-102">Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="539ca-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="539ca-103">Adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler de kullanıma sunulan [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], kolaylık, esneklik ve C# programlama okunabilirliğini artırmak.</span><span class="sxs-lookup"><span data-stu-id="539ca-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="539ca-104">Ayrıca, bu özellikler, Microsoft Office Otomasyonu API'leri gibi COM arabirimlerine erişim büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="539ca-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="539ca-105">Aşağıdaki örnekte, yöntem [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) altı gibi biçimlendirme, satırları ve sütunları sayısını sınırlayan bir tablo özelliklerini temsil eden parametreleri, yazı tiplerini ve renkleri vardır.</span><span class="sxs-lookup"><span data-stu-id="539ca-105">In the following example, method [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="539ca-106">Çoğu zaman, bunların tümünün için özel değerler belirtmek istemediğiniz tüm altı parametreler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="539ca-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="539ca-107">Ancak, adlandırılmış ve isteğe bağlı bağımsız değişkenler bir değer veya bir yer tutucu değerini her parametre için sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="539ca-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="539ca-108">Adlandırılmış ve isteğe bağlı bağımsız değişkenlerle projeniz için gerekli olan parametreleri için değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="539ca-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="539ca-109">Bu yordamları tamamlamak için Microsoft Office Word, bilgisayarınızda yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="539ca-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="539ca-110">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="539ca-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="539ca-111">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="539ca-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="539ca-112">Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="539ca-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="539ca-113">İçinde **şablon kategorileri** bölmesini genişletin **Visual C#**ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="539ca-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="539ca-114">Üst kısmındaki Ara **şablonları** emin olmak için bölmesinde **.NET Framework 4** görünür **hedef Framework** kutusu.</span><span class="sxs-lookup"><span data-stu-id="539ca-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="539ca-115">İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="539ca-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="539ca-116">Projenizde için bir ad yazın **adı** alan.</span><span class="sxs-lookup"><span data-stu-id="539ca-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="539ca-117">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="539ca-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="539ca-118">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="539ca-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="539ca-119">Başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="539ca-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="539ca-120">İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="539ca-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="539ca-121">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="539ca-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="539ca-122">Üzerinde **.NET** sayfasında, **Microsoft.Office.Interop.Word** içinde **bileşen adı** listesi.</span><span class="sxs-lookup"><span data-stu-id="539ca-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="539ca-123">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="539ca-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="539ca-124">Eklemek için gerekli yönergeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="539ca-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="539ca-125">İçinde **Çözüm Gezgini**, sağ **Program.cs** dosya ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="539ca-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="539ca-126">Aşağıdakileri ekleyin `using` yönergelerini kod dosyasının en üstüne.</span><span class="sxs-lookup"><span data-stu-id="539ca-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="539ca-127">Bir Word belgesinde metni görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="539ca-127">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="539ca-128">İçinde `Program` sınıf Program.cs içinde bir Word uygulaması ve bir Word belgesi oluşturmak için aşağıdaki yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="539ca-128">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="539ca-129">[Ekle](http://go.microsoft.com/fwlink/?LinkId=145381) yöntemi dört isteğe bağlı parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="539ca-129">The [Add](http://go.microsoft.com/fwlink/?LinkId=145381) method has four optional parameters.</span></span> <span data-ttu-id="539ca-130">Bu örnek, varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="539ca-130">This example uses their default values.</span></span> <span data-ttu-id="539ca-131">Bu nedenle, bağımsız değişkenler arama deyiminde gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="539ca-131">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  <span data-ttu-id="539ca-132">Aşağıdaki kodu nereye belgedeki metin görüntülemek ve görüntülenecek metni tanımlamak için yöntemi sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="539ca-132">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a><span data-ttu-id="539ca-133">Uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="539ca-133">To run the application</span></span>  
  
1.  <span data-ttu-id="539ca-134">Aşağıdaki deyim ana ekleyin.</span><span class="sxs-lookup"><span data-stu-id="539ca-134">Add the following statement to Main.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  <span data-ttu-id="539ca-135">Projeyi çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="539ca-135">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="539ca-136">Belirtilen metni içeren bir Word belgesi görünür.</span><span class="sxs-lookup"><span data-stu-id="539ca-136">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="539ca-137">Bir tabloya metni değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="539ca-137">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="539ca-138">Kullanım `ConvertToTable` yöntemi bir tablodaki metni alın.</span><span class="sxs-lookup"><span data-stu-id="539ca-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="539ca-139">Yöntemi, altı isteğe bağlı parametre yok.</span><span class="sxs-lookup"><span data-stu-id="539ca-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="539ca-140">IntelliSense aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreler köşeli parantez içine alır.</span><span class="sxs-lookup"><span data-stu-id="539ca-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="539ca-141">![ConvertToTable yönteminin listesi. ] (../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="539ca-141">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="539ca-142">ConvertToTable parametreleri</span><span class="sxs-lookup"><span data-stu-id="539ca-142">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="539ca-143">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, değiştirmek istediğiniz parametre değerlerini belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="539ca-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="539ca-144">Yönteminin sonuna aşağıdaki kodu ekleyin `DisplayInWord` basit bir tablo oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="539ca-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="539ca-145">Metinde virgüller içinde dize bağımsız değişkeni belirtir `range` tablo hücrelerinin ayırın.</span><span class="sxs-lookup"><span data-stu-id="539ca-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     <span data-ttu-id="539ca-146">Önceki sürümlerinde, C#, çağrısı `ConvertToTable` aşağıdaki kodda gösterildiği gibi her parametre için bir başvuru bağımsız değişken gerektirir.</span><span class="sxs-lookup"><span data-stu-id="539ca-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  <span data-ttu-id="539ca-147">Projeyi çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="539ca-147">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="539ca-148">Diğer parametrelerle denemek için</span><span class="sxs-lookup"><span data-stu-id="539ca-148">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="539ca-149">Bir sütun ve üç satır sahip olması tabloyu değiştirmek için son satırında yerini `DisplayInWord` aşağıdaki ifadeyi ve CTRL + F5'e yazın.</span><span class="sxs-lookup"><span data-stu-id="539ca-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  <span data-ttu-id="539ca-150">Tablosu için önceden tanımlanmış bir biçim belirtmek için son satırında Değiştir `DisplayInWord` aşağıdaki ifadeyi ve CTRL + F5'e yazın.</span><span class="sxs-lookup"><span data-stu-id="539ca-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="539ca-151">Biçim herhangi biri olabilir [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) sabitleri.</span><span class="sxs-lookup"><span data-stu-id="539ca-151">The format can be any of the [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) constants.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a><span data-ttu-id="539ca-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="539ca-152">Example</span></span>  
 <span data-ttu-id="539ca-153">Aşağıdaki kod, tam örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="539ca-153">The following code includes the full example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="539ca-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="539ca-154">See Also</span></span>  
 [<span data-ttu-id="539ca-155">Adlandırılmış ve isteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="539ca-155">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
