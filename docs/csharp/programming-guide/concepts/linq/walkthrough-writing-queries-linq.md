---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: 29c24d9920bff38beced8f5995ec328571e6b5d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309231"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="69eed-102">İzlenecek yol: C#'de Sorgu Yazma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="69eed-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="69eed-103">Bu yönerge, LINQ Sorgu ifadeleri yazmak için kullanılan C# dili özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="69eed-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="69eed-104">Bir C# Projesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="69eed-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69eed-105">Visual Studio için aşağıdaki yönergeleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="69eed-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="69eed-106">Farklı bir geliştirme ortamı kullanıyorsanız, bir System.Core.dll başvurusu olan bir konsol projesi oluşturun ve bir `using` yönergesi <xref:System.Linq?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="69eed-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="69eed-107">Visual Studio'da bir proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69eed-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="69eed-108">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69eed-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="69eed-109">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="69eed-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="69eed-110">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="69eed-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="69eed-111">Genişletin **yüklü**, genişletme **şablonları**, genişletme **Visual C#** ve ardından **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="69eed-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="69eed-112">İçinde **adı** metin kutusunda, farklı bir ad girin veya varsayılan adı kabul edin ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69eed-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="69eed-113">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="69eed-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="69eed-114">Projenize bir System.Core.dll başvurusu dikkat edin ve bir `using` yönergesi <xref:System.Linq?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="69eed-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="69eed-115">Bellek İçi Veri Kaynağı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="69eed-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="69eed-116">Veri kaynağını sorgular için basit bir listesidir `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="69eed-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="69eed-117">Her `Student` kaydına sahip bir ad, Soyadı ve test puanlarını sınıfında temsil eden tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="69eed-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="69eed-118">Bu kod projenize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="69eed-118">Copy this code into your project.</span></span> <span data-ttu-id="69eed-119">Aşağıdaki özelliklere dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="69eed-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="69eed-120">`Student` Sınıfı otomatik olarak uygulanan özellikler oluşur.</span><span class="sxs-lookup"><span data-stu-id="69eed-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="69eed-121">Listedeki her Öğrenci, bir nesne Başlatıcısı ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="69eed-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="69eed-122">Liste koleksiyon Başlatıcısı ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="69eed-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="69eed-123">Bu tüm veri yapısı başlatılamadı ve herhangi bir oluşturucu veya açık üye erişimi yapılan açık çağrıları olmadan örneği.</span><span class="sxs-lookup"><span data-stu-id="69eed-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="69eed-124">Bu yeni özellikler hakkında daha fazla bilgi için bkz. [Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) ve [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="69eed-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="69eed-125">Veri kaynağı eklemek için</span><span class="sxs-lookup"><span data-stu-id="69eed-125">To add the data source</span></span>  
  
-   <span data-ttu-id="69eed-126">Ekleme `Student` sınıfı ve öğrenciler için başlatılmış listesini `Program` projenizdeki sınıfı.</span><span class="sxs-lookup"><span data-stu-id="69eed-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="69eed-127">Öğrenciler listesine yeni bir Öğrenci eklemek için</span><span class="sxs-lookup"><span data-stu-id="69eed-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="69eed-128">Yeni bir `Student` için `Students` listesi ve test puanlarının tercih ettiğiniz bir ad kullanın.</span><span class="sxs-lookup"><span data-stu-id="69eed-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="69eed-129">Daha iyi nesne Başlatıcısı sözdizimi öğrenmek için tüm yeni Öğrenci bilgi yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="69eed-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="69eed-130">Sorgu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="69eed-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="69eed-131">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69eed-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="69eed-132">İçinde uygulamanın `Main` yöntemi yürütüldüğünde, tüm Öğrenciler ilk test üzerindeki, puanı 90'dan büyük bir listesini oluşturur ve basit bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69eed-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="69eed-133">Dikkat edin çünkü bütün `Student` nesne seçildiğinde, sorgu türü `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="69eed-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="69eed-134">Kod kullanarak dolaylı yazma da kullanabilirsiniz, ancak [var](../../../../csharp/language-reference/keywords/var.md) anahtar sözcüğü, açık yazım açıkça sonuçları göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69eed-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="69eed-135">(Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="69eed-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="69eed-136">Ayrıca sorgunun unutmayın aralık değişkeni `student`, her bir başvuru olarak hizmet veren `Student` kaynakta, her nesne için üye erişimi sağlama.</span><span class="sxs-lookup"><span data-stu-id="69eed-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="69eed-137">Sorguyu Yürütme</span><span class="sxs-lookup"><span data-stu-id="69eed-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="69eed-138">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="69eed-138">To execute the query</span></span>  
  
1. <span data-ttu-id="69eed-139">Artık yazma `foreach` sorgu yürütmek neden olacak bir döngü.</span><span class="sxs-lookup"><span data-stu-id="69eed-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="69eed-140">Kod hakkında aşağıdakileri unutmayın:</span><span class="sxs-lookup"><span data-stu-id="69eed-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="69eed-141">Döndürülen dizinin her öğesinde, yineleme değişkeni aracılığıyla erişilir `foreach` döngü.</span><span class="sxs-lookup"><span data-stu-id="69eed-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="69eed-142">Bu değişken türü `Student`, ve sorgu değişkeninin türü uyumlu `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="69eed-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="69eed-143">Bu kodu ekledikten sonra derleme ve sonuçlarını görmek için uygulamayı çalıştırma **konsol** penceresi.</span><span class="sxs-lookup"><span data-stu-id="69eed-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="69eed-144">Başka bir filtre koşulu eklemek için</span><span class="sxs-lookup"><span data-stu-id="69eed-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="69eed-145">Birden çok Boole koşulu birleştirebilirsiniz `where` sorgu iyice daraltmak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69eed-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="69eed-146">Aşağıdaki kod, böylece sorgu bu Öğrenciler, ilk puanı döndürür. bir koşul üzerinde 90 ve son, puan 80 şeklindeydi ekler.</span><span class="sxs-lookup"><span data-stu-id="69eed-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="69eed-147">`where` Yan tümcesi, aşağıdaki kod benzemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="69eed-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="69eed-148">Daha fazla bilgi için [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69eed-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="69eed-149">Sorguyu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="69eed-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="69eed-150">Sonuçları sıralamak için</span><span class="sxs-lookup"><span data-stu-id="69eed-150">To order the results</span></span>  
  
1. <span data-ttu-id="69eed-151">Sipariş çeşit olmaları durumunda tarama sonuçlarını daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="69eed-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="69eed-152">Döndürülen dizi kaynak öğeleri erişilebilen herhangi bir alana göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69eed-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="69eed-153">Örneğin, aşağıdaki `orderby` yan tümcesi siparişleri sonuçları alfabetik sırada A'dan Z'ye son her öğrencinin adına göre.</span><span class="sxs-lookup"><span data-stu-id="69eed-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="69eed-154">Aşağıdaki `orderby` sorgunuzu, sonra sağ yan tümcesini `where` deyimi ve önce `select` deyimi:</span><span class="sxs-lookup"><span data-stu-id="69eed-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="69eed-155">Şimdi değiştir `orderby` BT'nin sonuçlarını ters sırada puanına göre ilk testten en yüksek puanı düşük puana göre sıralar için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69eed-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="69eed-156">Değişiklik `WriteLine` puanları görebilmeniz için biçimlendirme dizesi:</span><span class="sxs-lookup"><span data-stu-id="69eed-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="69eed-157">Daha fazla bilgi için [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69eed-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="69eed-158">Sonuçları gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="69eed-158">To group the results</span></span>  
  
1. <span data-ttu-id="69eed-159">Gruplandırma sorgu ifadeleri güçlü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="69eed-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="69eed-160">Group yan tümcesi içeren sorgu grupları bir dizi oluşturur ve her grubu içeren bir `Key` ve bu grubun tüm üyelerinin oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="69eed-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="69eed-161">Aşağıdaki yeni sorgu anahtarı olarak son adlarının ilk harflerini kullanarak Öğrenciler gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="69eed-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="69eed-162">Sorgu türü artık değiştirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="69eed-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="69eed-163">Artık bir dizi olan grupları üretir bir `char` bir anahtarı ve bir dizi türü `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="69eed-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="69eed-164">Sorgu türü değiştiğinden, aşağıdaki değişiklikleri kod `foreach` yürütme döngüsü ayrıca:</span><span class="sxs-lookup"><span data-stu-id="69eed-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="69eed-165">Uygulamayı çalıştırmak ve sonuçları görüntülemek **konsol** penceresi.</span><span class="sxs-lookup"><span data-stu-id="69eed-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="69eed-166">Daha fazla bilgi için [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69eed-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="69eed-167">Değişkenlerin dolaylı olarak yazılmasını sağlamak için</span><span class="sxs-lookup"><span data-stu-id="69eed-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="69eed-168">Açıkça kodlama `IEnumerables` , `IGroupings` hızla zahmetli hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="69eed-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="69eed-169">Aynı sorgu yazabilirsiniz ve `foreach` daha rahat kullanarak döngü `var`.</span><span class="sxs-lookup"><span data-stu-id="69eed-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="69eed-170">`var` Anahtar sözcüğü, nesne türlerini değiştirmez; yalnızca derleyicinin türlerini çıkarması bildirir.</span><span class="sxs-lookup"><span data-stu-id="69eed-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="69eed-171">Türünü değiştirme `studentQuery` ve yineleme değişkeni `group` için `var` ve sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69eed-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="69eed-172">İçinde iç unutmayın `foreach` döngüsünün yineleme değişkeni hala türü olarak `Student`, ve sorgu yalnızca gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="69eed-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="69eed-173">Değişiklik `s` yineleme değişkeni `var` ve sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69eed-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="69eed-174">Tam olarak aynı sonuçları elde ettiğimizi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="69eed-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="69eed-175">Hakkında daha fazla bilgi için [var](../../../../csharp/language-reference/keywords/var.md), bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="69eed-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="69eed-176">Grupları anahtar değerlerine göre sıralamak için</span><span class="sxs-lookup"><span data-stu-id="69eed-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="69eed-177">Önceki sorguya çalıştırdığınızda, grupları alfabetik sırada olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="69eed-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="69eed-178">Bunu değiştirmek için sağlamalısınız bir `orderby` yan tümcesinden sonra `group` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69eed-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="69eed-179">Ancak kullanmak için bir `orderby` yan tümcesi, ilk gerekir tarafından oluşturulan grupları başvuru olarak hizmet veren bir tanımlayıcı `group` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69eed-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="69eed-180">Tanımlayıcısını kullanarak sağlama `into` anahtar sözcüğü, aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="69eed-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="69eed-181">Bu sorgu çalıştırdığınızda, grupları, artık alfabetik olarak sıralanır görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="69eed-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="69eed-182">Bir tanımlayıcıyı let kullanarak tanıtmak için</span><span class="sxs-lookup"><span data-stu-id="69eed-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="69eed-183">Kullanabileceğiniz `let` sorgu ifadesinde herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="69eed-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="69eed-184">Bu tanımlayıcı aşağıdaki örnekte olduğu gibi bir kullanışlı olabilir veya birden çok kez hesaplanacak yok, bir ifadenin sonuçlarını depolayarak performansı geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69eed-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="69eed-185">Daha fazla bilgi için [let yan tümcesi](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69eed-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="69eed-186">Bir sorgu ifadesinde yöntem sözdizimini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="69eed-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="69eed-187">Bölümünde anlatıldığı gibi [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), bazı sorgu işlemlerinin yalnızca yöntemi söz dizimi kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="69eed-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="69eed-188">Toplam puanı her biri için aşağıdaki kodu hesaplar `Student` kaynak dizisi, ve ardından aramaları `Average()` sınıfının ortalama puanını hesaplamak için bu sorgunun sonuçlarının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="69eed-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="69eed-189">Select yan tümcesinde dönüştürmek ya da planlamak için</span><span class="sxs-lookup"><span data-stu-id="69eed-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="69eed-190">Öğeleri kaynak dizileri öğeleri farklı bir dizi oluşturmak için bir sorgu çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="69eed-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="69eed-191">Silin veya önceki sorgu ve yürütme döngüsü açıklama ve aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="69eed-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="69eed-192">Sorgu dizeleri bir dizi döndürmediğine dikkat edin (değil `Students`), ve bu olgu yansıtılır `foreach` döngü.</span><span class="sxs-lookup"><span data-stu-id="69eed-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="69eed-193">Bu kılavuzda daha önce açıklanan kod ortalama sınıfı puanı yaklaşık 334 belirtilir.</span><span class="sxs-lookup"><span data-stu-id="69eed-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="69eed-194">Bir dizi oluşturmak için `Students` birlikte sınıfı ortalama'den büyük olan toplam puanı, `Student ID`, anonim bir tür içinde kullanabileceğiniz `select` deyimi:</span><span class="sxs-lookup"><span data-stu-id="69eed-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="69eed-195">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="69eed-195">Next Steps</span></span>  
 <span data-ttu-id="69eed-196">Sorgular, C# ile çalışmanın temel özellikleri hakkında bilgi sahibi olduktan sonra belgelere ve örneklere LINQ sağlayıcısı, ilgilendiğiniz belirli türünün okumaya hazırsınız:</span><span class="sxs-lookup"><span data-stu-id="69eed-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="69eed-197">LINQ - SQL</span><span class="sxs-lookup"><span data-stu-id="69eed-197">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="69eed-198">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="69eed-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="69eed-199">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="69eed-199">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="69eed-200">LINQ to Objects'in (C#)</span><span class="sxs-lookup"><span data-stu-id="69eed-200">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="69eed-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69eed-201">See also</span></span>

- [<span data-ttu-id="69eed-202">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="69eed-202">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="69eed-203">C#'de LINQ'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="69eed-203">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="69eed-204">LINQ Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="69eed-204">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
