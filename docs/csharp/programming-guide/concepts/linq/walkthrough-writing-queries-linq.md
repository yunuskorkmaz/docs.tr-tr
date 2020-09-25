---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
description: Bu izlenecek yol, C# dil özelliklerinin LINQ sorgu ifadelerinde nasıl kullanıldığını gösterir. Bu makalede, Visual Studio 'Yu bir geliştirme ortamı olarak kullanılmaktadır.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: bdf91f6f52a68309cfcd276b222083c8cb67a0cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176246"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="ab3c3-104">İzlenecek yol: C#'de Sorgu Yazma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ab3c3-104">Walkthrough: Writing Queries in C# (LINQ)</span></span>

<span data-ttu-id="ab3c3-105">Bu izlenecek yol, LINQ sorgu ifadeleri yazmak için kullanılan C# dil özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-105">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="ab3c3-106">Bir C# Projesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab3c3-106">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab3c3-107">Aşağıdaki yönergeler Visual Studio içindir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-107">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="ab3c3-108">Farklı bir geliştirme ortamı kullanıyorsanız, System.Core.dll bir başvuruya ve `using` ad alanına yönelik bir yönergeyle bir konsol projesi oluşturun <xref:System.Linq?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-108">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="ab3c3-109">Visual Studio 'da bir proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-109">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="ab3c3-110">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-110">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="ab3c3-111">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-111">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="ab3c3-112">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-112">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="ab3c3-113">**Yüklü**' i genişletin, **Şablonlar**' ı genişletin, **Visual C#** öğesini genişletin ve **konsol uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-113">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="ab3c3-114">**Ad** metin kutusuna, farklı bir ad girin veya varsayılan adı kabul edin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-114">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="ab3c3-115">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-115">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="ab3c3-116">Projenizin System.Core.dll bir başvurusu olduğunu ve `using` ad alanı için bir yönergeyi olduğunu unutmayın <xref:System.Linq?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-116">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="ab3c3-117">Bellek İçi Veri Kaynağı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab3c3-117">Create an in-Memory Data Source</span></span>  

 <span data-ttu-id="ab3c3-118">Sorgular için veri kaynağı basit bir `Student` nesne listesidir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-118">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="ab3c3-119">Her `Student` kaydın adı, soyadı ve, sınıftaki test puanlarını temsil eden bir tamsayılar dizisi vardır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-119">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="ab3c3-120">Bu kodu projenize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-120">Copy this code into your project.</span></span> <span data-ttu-id="ab3c3-121">Aşağıdaki özelliklere göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="ab3c3-121">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="ab3c3-122">`Student`Sınıfı otomatik uygulanan özelliklerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-122">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="ab3c3-123">Listedeki her öğrenci bir nesne başlatıcısı ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-123">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="ab3c3-124">Listenin kendisi bir koleksiyon başlatıcısı ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-124">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="ab3c3-125">Bu bütün veri yapısı, herhangi bir oluşturucuya veya açık üye erişimine açık çağrılar olmadan başlatılır ve oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-125">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="ab3c3-126">Bu yeni özellikler hakkında daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../classes-and-structs/auto-implemented-properties.md) ve [nesne ve koleksiyon başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="ab3c3-126">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="ab3c3-127">Veri kaynağını eklemek için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-127">To add the data source</span></span>  
  
- <span data-ttu-id="ab3c3-128">`Student`Kuruluşunuzdaki sınıfa sınıfını ve başlatılan öğrenci listesini ekleyin `Program` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-128">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="ab3c3-129">Öğrenciler listesine yeni bir Öğrenci eklemek için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-129">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="ab3c3-130">Listeye yeni bir `Student` ad ekleyin `Students` ve seçtiğiniz bir adı ve test puanlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-130">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="ab3c3-131">Nesne başlatıcısının sözdizimini daha iyi öğrenmek için tüm yeni öğrenci bilgilerini yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-131">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="ab3c3-132">Sorgu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab3c3-132">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="ab3c3-133">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-133">To create a simple query</span></span>  
  
- <span data-ttu-id="ab3c3-134">Uygulamanın `Main` yönteminde, yürütüldüğü bir basit sorgu oluşturun, bu, ilk testteki puanı 90 ' den büyük olan tüm öğrencilerin bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-134">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="ab3c3-135">Tüm `Student` nesnenin seçildiği, sorgunun türünün olduğunu unutmayın `IEnumerable<Student>` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-135">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="ab3c3-136">Kod aynı zamanda [var](../../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak örtük yazma da kullanabilir, ancak sonuçları açıkça göstermek için açık yazma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-136">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="ab3c3-137">(Hakkında daha fazla bilgi için `var` bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="ab3c3-137">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="ab3c3-138">Ayrıca sorgunun Aralık değişkeni, `student` `Student` her bir nesne için üye erişimi sağlayan, kaynakta her birine bir başvuru olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-138">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="ab3c3-139">Sorguyu Yürütme</span><span class="sxs-lookup"><span data-stu-id="ab3c3-139">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="ab3c3-140">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-140">To execute the query</span></span>  
  
1. <span data-ttu-id="ab3c3-141">Şimdi `foreach` sorgunun yürütülmesine neden olacak döngüyü yazın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-141">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="ab3c3-142">Kod hakkında aşağıdakilere göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="ab3c3-142">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="ab3c3-143">Döndürülen dizideki her öğeye, döngüdeki yineleme değişkeni üzerinden erişilir `foreach` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-143">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="ab3c3-144">Bu değişkenin türü `Student` ve sorgu değişkeninin türü uyumludur `IEnumerable<Student>` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-144">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="ab3c3-145">Bu kodu ekledikten sonra, sonuçları **konsol** penceresinde görmek için uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-145">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="ab3c3-146">Başka bir filtre koşulu eklemek için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-146">To add another filter condition</span></span>  
  
1. <span data-ttu-id="ab3c3-147">`where`Bir sorguyu daha iyi daraltmak için yan tümcesinde birden çok Boolean koşulu birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-147">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="ab3c3-148">Aşağıdaki kod, sorgunun ilk puanı 90 üzerinde olan ve son puanı 80 ' den az olan bu öğrencileri döndüren bir koşul ekler.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-148">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="ab3c3-149">`where`Yan tümce aşağıdaki koda benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-149">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="ab3c3-150">Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ab3c3-150">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="ab3c3-151">Sorguyu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ab3c3-151">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="ab3c3-152">Sonuçları sıralamak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-152">To order the results</span></span>  
  
1. <span data-ttu-id="ab3c3-153">Belirli bir sıra türünde olmaları durumunda sonuçların taranması daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-153">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="ab3c3-154">Döndürülen sırayı, kaynak öğelerde erişilebilir olan herhangi bir alana göre sıraya alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-154">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="ab3c3-155">Örneğin, aşağıdaki `orderby` yan tümce sonuçları her öğrencinin son adına göre a 'Dan Z 'ye alfabetik sırada sıralar.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-155">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="ab3c3-156">Aşağıdaki `orderby` yan tümceyi, `where` deyiminize ve deyimden önceye ekleyin `select` :</span><span class="sxs-lookup"><span data-stu-id="ab3c3-156">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="ab3c3-157">Şimdi, `orderby` yan tümceyi, en yüksek puanın en düşük puanına kadar, ilk testteki puana göre ters sırada sipariş verecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-157">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="ab3c3-158">`WriteLine`Puanları görebilmeniz için biçim dizesini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ab3c3-158">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="ab3c3-159">Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ab3c3-159">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="ab3c3-160">Sonuçları gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-160">To group the results</span></span>  
  
1. <span data-ttu-id="ab3c3-161">Gruplandırma, sorgu ifadelerinde güçlü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-161">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="ab3c3-162">Group yan tümcesi içeren bir sorgu bir grup sırası üretir ve her bir grubun kendisi `Key` ve bu grubun tüm üyelerinden oluşan bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-162">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="ab3c3-163">Aşağıdaki yeni sorgu, en son adının ilk harfini anahtar olarak kullanarak öğrencileri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-163">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="ab3c3-164">Sorgu türünün artık değiştiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-164">Note that the type of the query has now changed.</span></span> <span data-ttu-id="ab3c3-165">Artık `char` anahtar olarak bir türe ve bir nesne dizisine sahip olan bir grup sırası oluşturur `Student` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-165">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="ab3c3-166">Sorgunun türü değiştiği için aşağıdaki kod `foreach` yürütme döngüsünü de değiştirir:</span><span class="sxs-lookup"><span data-stu-id="ab3c3-166">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="ab3c3-167">Uygulamayı çalıştırın ve sonuçları **konsol** penceresinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-167">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="ab3c3-168">Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ab3c3-168">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="ab3c3-169">Değişkenlerin dolaylı olarak yazılmasını sağlamak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-169">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="ab3c3-170">Açıkça kodlama `IEnumerables` , `IGroupings` hızlı bir şekilde sıkıcı hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-170">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="ab3c3-171">Kullanarak aynı sorguyu ve döngüyü çok daha kolay bir şekilde yazabilirsiniz `foreach` `var` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-171">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="ab3c3-172">`var`Anahtar sözcüğü nesnelerinizin türlerini değiştirmez; yalnızca derleyiciye tür çıkarması talimatını verir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-172">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="ab3c3-173">Türünü `studentQuery` ve yineleme değişkenini değiştirin `group` `var` ve sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-173">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="ab3c3-174">İç `foreach` döngüde yineleme değişkeninin hala olarak yazılmış olduğunu `Student` ve sorgunun daha önce olduğu gibi çalışıp çalışmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-174">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="ab3c3-175">`s`Yineleme değişkenini olarak değiştirin `var` ve sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-175">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="ab3c3-176">Tam olarak aynı sonuçları elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-176">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="ab3c3-177">[Var](../../../language-reference/keywords/var.md)hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="ab3c3-177">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="ab3c3-178">Grupları anahtar değerlerine göre sıralamak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-178">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="ab3c3-179">Önceki sorguyu çalıştırdığınızda grupların alfabetik sırada olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-179">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="ab3c3-180">Bunu değiştirmek için, `orderby` yan tümcesinden sonra bir yan tümce sağlamanız gerekir `group` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-180">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="ab3c3-181">Ancak `orderby` yan tümce kullanmak için önce yan tümce tarafından oluşturulan gruplara başvuru olarak hizmet veren bir tanımlayıcıya ihtiyacınız vardır `group` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-181">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="ab3c3-182">`into`Aşağıdaki gibi anahtar sözcüğünü kullanarak tanımlayıcıyı sağlarsınız:</span><span class="sxs-lookup"><span data-stu-id="ab3c3-182">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="ab3c3-183">Bu sorguyu çalıştırdığınızda, grupların artık alfabetik sırada sıralanacağını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-183">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="ab3c3-184">Bir tanımlayıcıyı let kullanarak tanıtmak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-184">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="ab3c3-185">`let`Sorgu ifadesinde herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak üzere anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-185">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="ab3c3-186">Bu tanımlayıcı, aşağıdaki örnekte olduğu gibi kolaylık olabilir veya bir ifadenin sonuçlarını birden çok kez hesaplanmak zorunda kalmayacak şekilde depolayarak performansı geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-186">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="ab3c3-187">Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ab3c3-187">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="ab3c3-188">Bir sorgu ifadesinde yöntem sözdizimini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-188">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="ab3c3-189">[Sorgu söz dizimi ve LINQ 'Teki yöntem sözdiziminde](./query-syntax-and-method-syntax-in-linq.md)açıklandığı gibi, bazı sorgu işlemleri yalnızca Yöntem sözdizimi kullanılarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-189">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="ab3c3-190">Aşağıdaki kod, kaynak dizideki her biri için toplam puanı hesaplar `Student` ve ardından `Average()` sınıfın ortalama Puanını hesaplamak için bu sorgunun sonuçlarında yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-190">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="ab3c3-191">Select yan tümcesinde dönüştürmek ya da planlamak için</span><span class="sxs-lookup"><span data-stu-id="ab3c3-191">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="ab3c3-192">Bir sorgu için, öğeleri kaynak dizideki öğelerden farklı olan bir sıra üretmek çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-192">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="ab3c3-193">Önceki sorgunuzu ve yürütme döngünüzü silin veya bir yorum yapın ve aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-193">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="ab3c3-194">Sorgunun bir dizi dizeyi (değil) döndürdüğünü `Students` ve bu olgunun döngüde yansıtıldığını unutmayın `foreach` .</span><span class="sxs-lookup"><span data-stu-id="ab3c3-194">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="ab3c3-195">Bu kılavuzda daha önce bahsedilen kod, Ortalama sınıf puanının yaklaşık 334 olduğunu gösterdi.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-195">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="ab3c3-196">`Students`Toplam puanı, ortalamasının, ile birlikte ortalamasının daha büyük olduğu bir dizi oluşturmak için `Student ID` , bildiriminde anonim bir tür kullanabilirsiniz `select` :</span><span class="sxs-lookup"><span data-stu-id="ab3c3-196">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="ab3c3-197">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="ab3c3-197">Next Steps</span></span>  

 <span data-ttu-id="ab3c3-198">C# ' deki sorgularla çalışmanın temel yönleri hakkında bilgi sahibi olduktan sonra, ilgilendiğiniz LINQ sağlayıcısı türü için belge ve örnekleri okumaya hazırlanın:</span><span class="sxs-lookup"><span data-stu-id="ab3c3-198">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="ab3c3-199">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ab3c3-199">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="ab3c3-200">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="ab3c3-200">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="ab3c3-201">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ab3c3-201">LINQ to XML (C#)</span></span>](../../../../standard/linq/linq-xml-overview.md)  
  
 [<span data-ttu-id="ab3c3-202">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ab3c3-202">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab3c3-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab3c3-203">See also</span></span>

- [<span data-ttu-id="ab3c3-204">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ab3c3-204">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="ab3c3-205">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ab3c3-205">LINQ Query Expressions</span></span>](../../../linq/index.md)
