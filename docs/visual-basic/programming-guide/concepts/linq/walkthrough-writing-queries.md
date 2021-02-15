---
description: 'Daha fazla bilgi edinin: Izlenecek yol: Visual Basic sorguları yazma'
title: Sorgu Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 55a1b3382d587b7982b79448334c4688895fa6e6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466815"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="9c60d-103">İzlenecek Yol: Visual Basic'de Sorgu Yazma</span><span class="sxs-lookup"><span data-stu-id="9c60d-103">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="9c60d-104">Bu izlenecek yol, Language-Integrated sorgu (LINQ) sorgu ifadeleri yazmak için Visual Basic dil özelliklerini nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-104">This walkthrough demonstrates how you can use Visual Basic language features to write Language-Integrated Query (LINQ) query expressions.</span></span> <span data-ttu-id="9c60d-105">İzlenecek yol, öğrenci nesneleri listesinde sorgu oluşturmayı, sorguların nasıl çalıştırılacağını ve bunların nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-105">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="9c60d-106">Sorgular, nesne başlatıcıları, yerel tür çıkarımı ve anonim türler dahil olmak üzere çeşitli özellikler birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-106">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="9c60d-107">Bu yönergeyi tamamladıktan sonra, ilgilendiğiniz belirli bir LINQ sağlayıcısı için örneklere ve belgelere geçiş yapmaya hazırlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-107">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific LINQ provider you are interested in.</span></span> <span data-ttu-id="9c60d-108">LINQ sağlayıcıları [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , LINQ to DataSet ve içerir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9c60d-108">LINQ providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="9c60d-109">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c60d-109">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="9c60d-110">Konsol uygulama projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9c60d-110">To create a console application project</span></span>

1. <span data-ttu-id="9c60d-111">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="9c60d-112">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="9c60d-113">**Yüklü şablonlar** listesinde **Visual Basic**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-113">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="9c60d-114">Proje türleri listesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-114">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="9c60d-115">**Ad** kutusuna proje için bir ad yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-115">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="9c60d-116">Bir proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9c60d-116">A project is created.</span></span> <span data-ttu-id="9c60d-117">Varsayılan olarak, System.Core.dll bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-117">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="9c60d-118">Ayrıca, başvurular sayfasında **Içeri aktarılan ad alanları** listesi [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) <xref:System.Linq?displayProperty=nameWithType> ad alanını içerir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-118">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="9c60d-119">[Derleme sayfasında, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), **seçenek çıkarımı seçeneğinin** **Açık** olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="9c60d-119">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="9c60d-120">Bellek İçi Veri Kaynağı ekleme</span><span class="sxs-lookup"><span data-stu-id="9c60d-120">Add an In-Memory Data Source</span></span>

<span data-ttu-id="9c60d-121">Bu izlenecek yolda bulunan sorguların veri kaynağı bir `Student` nesne listesidir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-121">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="9c60d-122">Her `Student` nesne bir ad, soyadı, bir sınıf yılı ve öğrenci gövdesinde akademik bir derecelendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-122">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="9c60d-123">Veri kaynağını eklemek için</span><span class="sxs-lookup"><span data-stu-id="9c60d-123">To add the data source</span></span>

- <span data-ttu-id="9c60d-124">Bir `Student` sınıf tanımlayın ve sınıf örneklerinin bir listesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c60d-124">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9c60d-125">`Student`Sınıfını tanımlamak ve İzlenecek yol örneklerinde kullanılan listeyi oluşturmak için gereken kod, [nasıl yapılır: öğe listesi oluşturma](how-to-create-a-list-of-items.md)bölümünde verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-125">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="9c60d-126">Buradan kopyalayabilir ve projenize yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c60d-126">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="9c60d-127">Yeni kod, projeyi oluştururken görüntülenen kodun yerini alır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-127">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="9c60d-128">Öğrenciler listesine yeni bir öğrenci eklemek için</span><span class="sxs-lookup"><span data-stu-id="9c60d-128">To add a new student to the students list</span></span>

- <span data-ttu-id="9c60d-129">`getStudents`Bir sınıfın başka bir örneğini listeye eklemek için yöntemindeki kalıbı izleyin `Student` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-129">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="9c60d-130">Öğrenci eklemek sizi nesne başlatıcılarına tanıtacaktır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-130">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="9c60d-131">Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c60d-131">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="9c60d-132">Sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c60d-132">Create a Query</span></span>

<span data-ttu-id="9c60d-133">Yürütüldüğünde, bu bölüme eklenen sorgu, akademik derecesi bunları en üstteki on 'a yerleştiren öğrencilerin bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c60d-133">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="9c60d-134">Sorgu `Student` her seferinde tüm nesneyi seçtiğinden, sorgu sonucunun türü olur `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-134">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="9c60d-135">Ancak sorgu türü sorgu tanımlarında genellikle belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="9c60d-135">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="9c60d-136">Bunun yerine, derleyici türü tespit etmek için yerel tür çıkarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-136">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="9c60d-137">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="9c60d-137">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="9c60d-138">Sorgunun Aralık değişkeni, `currentStudent` kaynak içindeki her bir örneğe bir başvuru olarak görev yapar ve `Student` `students` içindeki her nesnenin özelliklerine erişim sağlar `students` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-138">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="9c60d-139">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9c60d-139">To create a simple query</span></span>

1. <span data-ttu-id="9c60d-140">`Main`Aşağıdaki şekilde işaretlenen projenin yönteminde yer bulun:</span><span class="sxs-lookup"><span data-stu-id="9c60d-140">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="9c60d-141">Aşağıdaki kodu kopyalayın ve içine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-141">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="9c60d-142">`studentQuery`Derleyici tarafından atanan türün olduğunu doğrulamak için fare işaretçisini kodunuzda bekletin `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-142">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="9c60d-143">Sorguyu çalıştır</span><span class="sxs-lookup"><span data-stu-id="9c60d-143">Run the Query</span></span>

<span data-ttu-id="9c60d-144">Değişkeni, `studentQuery` sorgunun çalıştırıldığı sonuçları değil sorgunun tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-144">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="9c60d-145">Sorgu çalıştırmaya yönelik tipik bir mekanizma bir `For Each` döngüdür.</span><span class="sxs-lookup"><span data-stu-id="9c60d-145">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="9c60d-146">Döndürülen dizideki her öğeye döngü yineleme değişkeni üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-146">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="9c60d-147">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="9c60d-147">For more information about query execution, see [Writing Your First LINQ Query](writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="9c60d-148">Sorguyu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9c60d-148">To run the query</span></span>

1. <span data-ttu-id="9c60d-149">Aşağıdaki `For Each` döngüyü projenizdeki sorgunun altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-149">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="9c60d-150">Veri türünü görmek için fare işaretçisini döngü denetim değişkeninin üzerine getirin `studentRecord` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-150">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="9c60d-151">Öğesinin türü olarak `studentRecord` algılanır `Student` , çünkü `studentQuery` bir örnek koleksiyonu döndürür `Student` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-151">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="9c60d-152">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-152">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="9c60d-153">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-153">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="9c60d-154">Sorguyu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9c60d-154">Modify the Query</span></span>

<span data-ttu-id="9c60d-155">Sorgu sonuçlarının belirtilen sırada olmaları durumunda taranması daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="9c60d-155">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="9c60d-156">Döndürülen sırayı kullanılabilir herhangi bir alana göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c60d-156">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="9c60d-157">Sonuçları sıralamak için</span><span class="sxs-lookup"><span data-stu-id="9c60d-157">To order the results</span></span>

1. <span data-ttu-id="9c60d-158">Aşağıdaki `Order By` yan tümceyi, `Where` ve sorgusunun deyimi arasına ekleyin `Select` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-158">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="9c60d-159">`Order By`Yan tümcesi, her öğrencinin son adına göre sonuçları a 'Dan Z 'ye sıralar.</span><span class="sxs-lookup"><span data-stu-id="9c60d-159">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="9c60d-160">Son ada göre sıralamak ve sonra adı için sorguya her iki alanı da ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9c60d-160">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="9c60d-161">Ayrıca, `Descending` Z 'Den A 'ya sıralama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c60d-161">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="9c60d-162">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-162">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="9c60d-163">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-163">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="9c60d-164">Yerel tanımlayıcı tanıtmak için</span><span class="sxs-lookup"><span data-stu-id="9c60d-164">To introduce a local identifier</span></span>

1. <span data-ttu-id="9c60d-165">Sorgu ifadesinde yerel bir tanımlayıcı tanıtmak için bu bölümdeki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-165">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="9c60d-166">Yerel tanımlayıcı bir ara sonuç tutacaktır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-166">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="9c60d-167">Aşağıdaki örnekte, `name` öğrencinin adı ve soyadlarını bir kez birleştirme tutan bir tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-167">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="9c60d-168">Yerel bir tanımlayıcı kolaylık sağlaması için kullanılabilir veya daha önce birden çok kez hesaplanabilecek bir ifadenin sonuçlarını depolayarak performansı geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-168">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="9c60d-169">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-169">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="9c60d-170">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-170">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="9c60d-171">Select yan tümcesinde bir alan planlamak için</span><span class="sxs-lookup"><span data-stu-id="9c60d-171">To project one field in the Select clause</span></span>

1. <span data-ttu-id="9c60d-172">`For Each`Öğeleri kaynaktaki öğelerden farklı olan bir dizi üreten bir sorgu oluşturmak için bu bölümden sorgu ve döngüyü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-172">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="9c60d-173">Aşağıdaki örnekte, kaynak bir `Student` nesne koleksiyonudur, ancak her bir nesnenin yalnızca bir üyesi döndürülür: son adı Garcia olan öğrencilerin ilk adı.</span><span class="sxs-lookup"><span data-stu-id="9c60d-173">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="9c60d-174">Çünkü `currentStudent.First` bir dizedir, tarafından döndürülen sıranın veri türü `studentQuery3` `IEnumerable(Of String)` , dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="9c60d-174">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="9c60d-175">Önceki örneklerde olduğu gibi, için bir veri türü ataması, `studentQuery3` derleyicinin yerel tür çıkarımı kullanılarak belirlenmesi için bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-175">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="9c60d-176">`studentQuery3`Atanan türün olduğunu doğrulamak için fare işaretçisini kodunuzda bekletin `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-176">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="9c60d-177">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-177">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="9c60d-178">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-178">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="9c60d-179">Select yan tümcesinde anonim bir tür oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9c60d-179">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="9c60d-180">Anonim türlerin sorgularda nasıl kullanıldığını görmek için bu bölümden kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-180">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="9c60d-181">Veri kaynağından, tüm kayıtlar ( `currentStudent` Önceki örneklerde kayıtlar) veya tek alanlar (önceki bölümde) yerine birden fazla alan döndürmek istediğinizde bunları sorgularda kullanırsınız `First` .</span><span class="sxs-lookup"><span data-stu-id="9c60d-181">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="9c60d-182">Sonuca eklemek istediğiniz alanları içeren yeni bir adlandırılmış tür tanımlamak yerine, `Select` yan tümcesindeki alanları belirtirsiniz ve derleyici, özellikleri olarak bu alanlarla anonim bir tür oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c60d-182">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="9c60d-183">Daha fazla bilgi için bkz. [anonim türler](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c60d-183">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="9c60d-184">Aşağıdaki örnek, akademik derecelendirmesi sırasında akademik derecesi 1 ile 10 arasında olan Seniors 'in adını ve derecesini döndüren bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c60d-184">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="9c60d-185">Bu örnekte, `studentQuery4` `Select` yan tümce anonim bir türün bir örneğini döndürdüğünden ve anonim bir türün kullanılabilir bir adı olmadığından, türü çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-185">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="9c60d-186">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-186">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="9c60d-187">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-187">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="9c60d-188">Ek Örnekler</span><span class="sxs-lookup"><span data-stu-id="9c60d-188">Additional Examples</span></span>

<span data-ttu-id="9c60d-189">Temel bilgileri anladığınıza göre, LINQ sorgularının esnekliğini ve gücünü göstermek için ek örneklerin bir listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9c60d-189">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of LINQ queries.</span></span> <span data-ttu-id="9c60d-190">Her örnek öncesinde ne yapabileceğinize ilişkin kısa bir açıklamadır.</span><span class="sxs-lookup"><span data-stu-id="9c60d-190">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="9c60d-191">Gösterilen türü görmek için fare işaretçisini her sorgu için sorgu sonuç değişkeninin üzerine getirin.</span><span class="sxs-lookup"><span data-stu-id="9c60d-191">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="9c60d-192">`For Each`Sonuçları oluşturmak için bir döngü kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c60d-192">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="9c60d-193">Ek Bilgi</span><span class="sxs-lookup"><span data-stu-id="9c60d-193">Additional Information</span></span>

<span data-ttu-id="9c60d-194">Sorgularla çalışmanın temel kavramlarıyla ilgili bilgi sahibi olduktan sonra, ilgilendiğiniz LINQ sağlayıcısı türü için belge ve örnekleri okumaya hazırsınızdır:</span><span class="sxs-lookup"><span data-stu-id="9c60d-194">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of LINQ provider that you are interested in:</span></span>

- [<span data-ttu-id="9c60d-195">Nesnelere LINQ</span><span class="sxs-lookup"><span data-stu-id="9c60d-195">LINQ to Objects</span></span>](linq-to-objects.md)

- [<span data-ttu-id="9c60d-196">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9c60d-196">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="9c60d-197">LINQ - XML</span><span class="sxs-lookup"><span data-stu-id="9c60d-197">LINQ to XML</span></span>](../../../../standard/linq/linq-xml-overview.md)

- [<span data-ttu-id="9c60d-198">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="9c60d-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="9c60d-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c60d-199">See also</span></span>

- [<span data-ttu-id="9c60d-200">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c60d-200">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="9c60d-201">Visual Basic'te LINQ'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="9c60d-201">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="9c60d-202">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c60d-202">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="9c60d-203">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="9c60d-203">Object Initializers: Named and Anonymous Types</span></span>](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="9c60d-204">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="9c60d-204">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="9c60d-205">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="9c60d-205">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9c60d-206">LINQ</span><span class="sxs-lookup"><span data-stu-id="9c60d-206">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="9c60d-207">Sorgular</span><span class="sxs-lookup"><span data-stu-id="9c60d-207">Queries</span></span>](../../../language-reference/queries/index.md)
