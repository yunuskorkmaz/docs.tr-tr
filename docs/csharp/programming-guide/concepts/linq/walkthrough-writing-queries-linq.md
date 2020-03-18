---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: f2135c6c3649ba2fc87e3b49770439688a58269b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73418062"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="348df-102">İzlenecek yol: C#'de Sorgu Yazma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="348df-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="348df-103">Bu gözden geçirme, LINQ sorgu ifadeleri yazmak için kullanılan C# dil özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="348df-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="348df-104">Bir C# Projesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="348df-104">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="348df-105">Aşağıdaki talimatlar Visual Studio içindir.</span><span class="sxs-lookup"><span data-stu-id="348df-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="348df-106">Farklı bir geliştirme ortamı kullanıyorsanız, System.Core.dll'ye başvuru içeren `using` bir konsol <xref:System.Linq?displayProperty=nameWithType> projesi ve ad alanı için bir yönerge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="348df-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="348df-107">Visual Studio'da proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="348df-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="348df-108">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="348df-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="348df-109">Menü çubuğunda **Dosya**, **Yeni**, **Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="348df-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="348df-110">**Yeni Proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="348df-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="348df-111">**Yüklü**genişletin, **Şablonları**genişletin, **Visual C#** seçeneğini genişletin ve ardından **Konsol Uygulamasını**seçin.</span><span class="sxs-lookup"><span data-stu-id="348df-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="348df-112">**Ad** metin kutusuna farklı bir ad girin veya varsayılan adı kabul edin ve ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="348df-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="348df-113">Yeni proje Çözüm **Gezgini'nde**görünür.</span><span class="sxs-lookup"><span data-stu-id="348df-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="348df-114">Projenizin System.Core.dll'ye bir başvurusu `using` ve <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir yönergesi olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="348df-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="348df-115">Bellek İçi Veri Kaynağı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="348df-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="348df-116">Sorgular için veri kaynağı `Student` nesnelerin basit bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="348df-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="348df-117">Her `Student` kaydın bir adı, soyadı ve sınıftaki test puanlarını temsil eden bir tamsayı dizisi vardır.</span><span class="sxs-lookup"><span data-stu-id="348df-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="348df-118">Bu kodu projenize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="348df-118">Copy this code into your project.</span></span> <span data-ttu-id="348df-119">Aşağıdaki özelliklere dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="348df-119">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="348df-120">Sınıf `Student` otomatik olarak uygulanan özelliklerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="348df-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="348df-121">Listedeki her öğrenci bir nesne baş harfer ile başharfe işlenir.</span><span class="sxs-lookup"><span data-stu-id="348df-121">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="348df-122">Listenin kendisi bir koleksiyon baş harfer ile başharfe getirilir.</span><span class="sxs-lookup"><span data-stu-id="348df-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="348df-123">Tüm bu veri yapısı, herhangi bir oluşturucu ya da açık üye erişimine açık çağrılar yapılmadan başharflere alınacak ve anında elde edilecektir.</span><span class="sxs-lookup"><span data-stu-id="348df-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="348df-124">Bu yeni özellikler hakkında daha fazla bilgi için Otomatik [Uygulanan Özellikler](../../classes-and-structs/auto-implemented-properties.md) ve Nesne ve Koleksiyon [Başlangıç Layıcıları'na](../../classes-and-structs/object-and-collection-initializers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="348df-124">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="348df-125">Veri kaynağını eklemek için</span><span class="sxs-lookup"><span data-stu-id="348df-125">To add the data source</span></span>  
  
- <span data-ttu-id="348df-126">Projenizdeki `Student` sınıf ve öğrencilerin başlangıç listesini `Program` sınıfa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="348df-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="348df-127">Öğrenciler listesine yeni bir Öğrenci eklemek için</span><span class="sxs-lookup"><span data-stu-id="348df-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="348df-128">`Students` Listeye yeni `Student` bir yeni ekleyin ve seçtiğiniz bir ad ve test puanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="348df-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="348df-129">Nesne başharfini daha iyi öğrenmek için tüm yeni öğrenci bilgilerini yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="348df-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="348df-130">Sorgu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="348df-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="348df-131">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="348df-131">To create a simple query</span></span>  
  
- <span data-ttu-id="348df-132">Uygulamanın `Main` yönteminde, yürütüldüğünde ilk testteki puanı 90'dan büyük olan tüm öğrencilerin listesini oluşturacak basit bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="348df-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="348df-133">Tüm `Student` nesne seçildiğinden, sorgunun türü `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="348df-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="348df-134">Kod, [var](../../../language-reference/keywords/var.md) anahtar sözcüğü kullanılarak örtük yazıyazmakda da kullanılabilse de, sonuçları açıkça göstermek için açık yazı yazmak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="348df-134">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="348df-135">(Hakkında `var`daha fazla bilgi için bkz: [Örtülü Olarak Yazılan Yerel Değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="348df-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="348df-136">Ayrıca, sorgunun aralık değişkeni, `student`kaynaktaki her `Student` biri için bir başvuru görevi görehizmet ederek her nesne için üye erişimi sağladığını da unutmayın.</span><span class="sxs-lookup"><span data-stu-id="348df-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="348df-137">Sorguyu Yürütme</span><span class="sxs-lookup"><span data-stu-id="348df-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="348df-138">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="348df-138">To execute the query</span></span>  
  
1. <span data-ttu-id="348df-139">Şimdi sorguyürütmek için neden olacak `foreach` döngü yazın.</span><span class="sxs-lookup"><span data-stu-id="348df-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="348df-140">Kod hakkında aşağıdakileri not edin:</span><span class="sxs-lookup"><span data-stu-id="348df-140">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="348df-141">Döndürülen dizideki her elemana `foreach` döngüdeki yineleme değişkeninden erişilir.</span><span class="sxs-lookup"><span data-stu-id="348df-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="348df-142">Bu değişkenin türü `Student`ve sorgu değişkeninin türü `IEnumerable<Student>`uyumludur.</span><span class="sxs-lookup"><span data-stu-id="348df-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="348df-143">Bu kodu ekledikten sonra, **konsol** penceresinde sonuçları görmek için uygulamayı oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="348df-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="348df-144">Başka bir filtre koşulu eklemek için</span><span class="sxs-lookup"><span data-stu-id="348df-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="348df-145">Bir sorguyu `where` daha da hassaslaştırmak için yan tümcedeki birden çok Boolean koşullarını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="348df-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="348df-146">Aşağıdaki kod, ilk puanı 90'ın üzerinde olan ve son puanı 80'den az olan öğrencileri döndüren bir koşul ekler.</span><span class="sxs-lookup"><span data-stu-id="348df-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="348df-147">Yan `where` tümce aşağıdaki koda benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="348df-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="348df-148">Daha fazla bilgi için [bkz.](../../../language-reference/keywords/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="348df-148">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="348df-149">Sorguyu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="348df-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="348df-150">Sonuçları sıralamak için</span><span class="sxs-lookup"><span data-stu-id="348df-150">To order the results</span></span>  
  
1. <span data-ttu-id="348df-151">Bir tür sıradaysa, sonuçları taramayapmak daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="348df-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="348df-152">Döndürülen sırayı kaynak öğelerdeki erişilebilir herhangi bir alana göre sipariş edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="348df-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="348df-153">Örneğin, aşağıdaki `orderby` yan tümce, sonuçları her öğrencinin soyadına göre A'dan Z'ye alfabetik sırayla sıralar.</span><span class="sxs-lookup"><span data-stu-id="348df-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="348df-154">İfadeden `orderby` hemen sonra ve deyimden `select` önce, sorgunuza aşağıdaki yan tümceyi ekleyin: `where`</span><span class="sxs-lookup"><span data-stu-id="348df-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="348df-155">`orderby` Şimdi, sonuçları ilk testteki puana göre, en yüksek puandan en düşük puana göre ters sırayla sipariş edebilmesi için tümceyi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="348df-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="348df-156">Puanları `WriteLine` görebilmeniz için biçim dizesini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="348df-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="348df-157">Daha fazla bilgi için [orderby yan tümcesi'ne](../../../language-reference/keywords/orderby-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="348df-157">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="348df-158">Sonuçları gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="348df-158">To group the results</span></span>  
  
1. <span data-ttu-id="348df-159">Gruplandırma sorgu ifadelerinde güçlü bir yetenektir.</span><span class="sxs-lookup"><span data-stu-id="348df-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="348df-160">Grup yan tümcesi olan bir sorgu bir grup `Key` dizisi üretir ve her grubun kendisi, o grubun tüm üyelerinden oluşan bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="348df-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="348df-161">Aşağıdaki yeni sorgu, anahtar olarak soyadlarının ilk harfini kullanarak öğrencileri gruplandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="348df-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="348df-162">Sorgunun türünün artık değiştiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="348df-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="348df-163">Şimdi bir anahtar olarak türü `char` ve `Student` nesnelerin bir dizi grup bir dizi üretir.</span><span class="sxs-lookup"><span data-stu-id="348df-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="348df-164">Sorgunun türü değiştiğinden, aşağıdaki kod yürütme `foreach` döngüsünde de değişiklik gösterir:</span><span class="sxs-lookup"><span data-stu-id="348df-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="348df-165">Uygulamayı çalıştırın ve sonuçları **Konsol** penceresinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="348df-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="348df-166">Daha fazla bilgi için [grup yan tümcesi'ne](../../../language-reference/keywords/group-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="348df-166">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="348df-167">Değişkenlerin dolaylı olarak yazılmasını sağlamak için</span><span class="sxs-lookup"><span data-stu-id="348df-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="348df-168">Açıkça kodlama `IEnumerables` `IGroupings` hızla sıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="348df-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="348df-169">Aynı sorguyu yazabilir `foreach` ve döngüyü çok `var`daha rahat bir şekilde kullanarak.</span><span class="sxs-lookup"><span data-stu-id="348df-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="348df-170">Anahtar `var` kelime nesnelerinizin türlerini değiştirmez; sadece derleyici türleri çıkarmak için talimat verir.</span><span class="sxs-lookup"><span data-stu-id="348df-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="348df-171">Tür ve `studentQuery` yineleme değişkenini `group` değiştirin `var` ve sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="348df-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="348df-172">İç `foreach` döngüde yineleme değişkeninin hala "olarak" `Student`olarak yazılması gerektiğini ve sorgunun eskisi gibi çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="348df-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="348df-173">Yineleme `s` değişkenini değiştirin `var` ve sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="348df-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="348df-174">Aynı sonuçları aldığınızı görüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="348df-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="348df-175">[Var](../../../language-reference/keywords/var.md)hakkında daha fazla bilgi için [bkz.](../../classes-and-structs/implicitly-typed-local-variables.md)</span><span class="sxs-lookup"><span data-stu-id="348df-175">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="348df-176">Grupları anahtar değerlerine göre sıralamak için</span><span class="sxs-lookup"><span data-stu-id="348df-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="348df-177">Önceki sorguyu çalıştırdığınızda, grupların alfabetik sırada olmadığını fark esiniz.</span><span class="sxs-lookup"><span data-stu-id="348df-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="348df-178">Bunu değiştirmek için, yan `orderby` tümceden `group` sonra bir yan tümce sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="348df-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="348df-179">Ancak bir `orderby` yan tümce kullanmak için öncelikle yan tümcetarafından oluşturulan gruplara `group` başvuru görevi görebilen bir tanımlayıcıgerekir.</span><span class="sxs-lookup"><span data-stu-id="348df-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="348df-180">Anahtar kelimeyi kullanarak tanımlayıcıyı `into` aşağıdaki gibi sağlarsınız:</span><span class="sxs-lookup"><span data-stu-id="348df-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="348df-181">Bu sorguyu çalıştırdığınızda, grupların artık alfabetik sıraya göre sıralanmış olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="348df-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="348df-182">Bir tanımlayıcıyı let kullanarak tanıtmak için</span><span class="sxs-lookup"><span data-stu-id="348df-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="348df-183">`let` Sorgu ifadesinde herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak için anahtar kelimekullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="348df-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="348df-184">Bu tanımlayıcı, aşağıdaki örnekte olduğu gibi kolaylık sağlayabilir veya bir ifadenin sonuçlarını birden çok kez hesaplanması gerekmeyecek şekilde depolayarak performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="348df-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="348df-185">Daha fazla bilgi için [bkz.](../../../language-reference/keywords/let-clause.md)</span><span class="sxs-lookup"><span data-stu-id="348df-185">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="348df-186">Bir sorgu ifadesinde yöntem sözdizimini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="348df-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="348df-187">[Linq'te Sorgu Sözdizimi ve Yöntem Sözdizimi'nde](./query-syntax-and-method-syntax-in-linq.md)açıklandığı gibi, bazı sorgu işlemleri yalnızca yöntem sözdizimi kullanılarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="348df-187">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="348df-188">Aşağıdaki kod kaynak sıradaki her `Student` biri için toplam puanı `Average()` hesaplar ve sonra sınıfın ortalama puanını hesaplamak için bu sorgunun sonuçlarında yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="348df-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="348df-189">Select yan tümcesinde dönüştürmek ya da planlamak için</span><span class="sxs-lookup"><span data-stu-id="348df-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="348df-190">Bir sorgunun, öğeleri kaynak dizideki öğelerden farklı olan bir dizi oluşturması çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="348df-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="348df-191">Önceki sorgu ve yürütme döngünüzün silin veya yorumunuzu yapın ve aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="348df-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="348df-192">Sorgunun bir dize sırasını döndürtettiğini (değil) `Students`ve `foreach` bu gerçeğin döngüye yansıttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="348df-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="348df-193">Bu gözden geçirmede daha önceki kod, ortalama sınıf puanının yaklaşık 334 olduğunu belirtmiştir.</span><span class="sxs-lookup"><span data-stu-id="348df-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="348df-194">Toplam puanı sınıf `Students` ortalamasından büyük olan bir dizi oluşturmak `Student ID`için, onların , `select` deyiminde anonim bir tür kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="348df-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="348df-195">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="348df-195">Next Steps</span></span>  
 <span data-ttu-id="348df-196">C#'daki sorgularla çalışmanın temel yönlerini tanıdıktan sonra, ilgilendiğiniz belirli türde LINQ sağlayıcısına ait belgeleri ve örnekleri okumaya hazırsınız:</span><span class="sxs-lookup"><span data-stu-id="348df-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="348df-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="348df-197">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="348df-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="348df-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="348df-199">LinQ xml (C#) için</span><span class="sxs-lookup"><span data-stu-id="348df-199">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="348df-200">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="348df-200">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="348df-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="348df-201">See also</span></span>

- [<span data-ttu-id="348df-202">Dil-Tümleşik Sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="348df-202">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="348df-203">LINQ Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="348df-203">LINQ Query Expressions</span></span>](../../../linq/index.md)
