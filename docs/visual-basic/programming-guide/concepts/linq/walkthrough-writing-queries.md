---
title: Sorgu Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 6a9f229697ce3d6328c6fb09d18d4cc2627eab10
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351023"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="a5ae5-102">İzlenecek Yol: Visual Basic'de Sorgu Yazma</span><span class="sxs-lookup"><span data-stu-id="a5ae5-102">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="a5ae5-103">Bu izlenecek yol, [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu ifadeleri yazmak için Visual Basic dil özelliklerini nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query expressions.</span></span> <span data-ttu-id="a5ae5-104">İzlenecek yol, öğrenci nesneleri listesinde sorgu oluşturmayı, sorguların nasıl çalıştırılacağını ve bunların nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="a5ae5-105">Sorgular, nesne başlatıcıları, yerel tür çıkarımı ve anonim türler dahil olmak üzere çeşitli özellikler birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="a5ae5-106">Bu yönergeyi tamamladıktan sonra, ilgilendiğiniz belirli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıya yönelik örneklere ve belgelere geçiş yapmaya hazırlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider you are interested in.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="a5ae5-107">sağlayıcılar [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-107">providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="a5ae5-108">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5ae5-108">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="a5ae5-109">Konsol uygulama projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-109">To create a console application project</span></span>

1. <span data-ttu-id="a5ae5-110">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-110">Start Visual Studio.</span></span>

2. <span data-ttu-id="a5ae5-111">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="a5ae5-112">**Yüklü şablonlar** listesinde **Visual Basic**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="a5ae5-113">Proje türleri listesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="a5ae5-114">**Ad** kutusuna proje için bir ad yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="a5ae5-115">Bir proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-115">A project is created.</span></span> <span data-ttu-id="a5ae5-116">Varsayılan olarak, System. Core. dll öğesine bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="a5ae5-117">Ayrıca, başvurular sayfasında **Içeri aktarılan ad alanları** listesi [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) <xref:System.Linq?displayProperty=nameWithType> ad alanını içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="a5ae5-118">[Derleme sayfasında, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), **seçenek çıkarımı seçeneğinin** **Açık**olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="a5ae5-119">Bellek İçi Veri Kaynağı ekleme</span><span class="sxs-lookup"><span data-stu-id="a5ae5-119">Add an In-Memory Data Source</span></span>

<span data-ttu-id="a5ae5-120">Bu izlenecek yolda bulunan sorguların veri kaynağı, `Student` nesnelerinin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="a5ae5-121">Her `Student` nesnesi bir ad, soyadı, bir sınıf yılı ve öğrenci gövdesinde akademik bir derecelendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="a5ae5-122">Veri kaynağını eklemek için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-122">To add the data source</span></span>

- <span data-ttu-id="a5ae5-123">Bir `Student` sınıfı tanımlayın ve sınıf örneklerinin bir listesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-123">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="a5ae5-124">`Student` sınıfını tanımlamak ve İzlenecek yol örneklerinde kullanılan listeyi oluşturmak için gereken kod, [nasıl yapılır: öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)bölümünde verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="a5ae5-125">Buradan kopyalayabilir ve projenize yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="a5ae5-126">Yeni kod, projeyi oluştururken görüntülenen kodun yerini alır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-126">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="a5ae5-127">Öğrenciler listesine yeni bir öğrenci eklemek için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-127">To add a new student to the students list</span></span>

- <span data-ttu-id="a5ae5-128">`Student` sınıfının başka bir örneğini listeye eklemek için `getStudents` yöntemindeki kalıbı izleyin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="a5ae5-129">Öğrenci eklemek sizi nesne başlatıcılarına tanıtacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="a5ae5-130">Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a5ae5-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="a5ae5-131">Sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5ae5-131">Create a Query</span></span>

<span data-ttu-id="a5ae5-132">Yürütüldüğünde, bu bölüme eklenen sorgu, akademik derecesi bunları en üstteki on 'a yerleştiren öğrencilerin bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="a5ae5-133">Sorgu her seferinde tüm `Student` nesnesini seçtiği için, sorgu sonucunun türü `IEnumerable(Of Student)`.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="a5ae5-134">Ancak sorgu türü sorgu tanımlarında genellikle belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="a5ae5-135">Bunun yerine, derleyici türü tespit etmek için yerel tür çıkarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="a5ae5-136">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a5ae5-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="a5ae5-137">Sorgunun Aralık değişkeni `currentStudent`, `students`içindeki her bir nesnenin özelliklerine erişim sağlayan `students`kaynaktaki her bir `Student` örneğine başvuru işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="a5ae5-138">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-138">To create a simple query</span></span>

1. <span data-ttu-id="a5ae5-139">Aşağıdaki şekilde işaretlenen projenin `Main` yönteminde yer bulun:</span><span class="sxs-lookup"><span data-stu-id="a5ae5-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="a5ae5-140">Aşağıdaki kodu kopyalayın ve içine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-140">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="a5ae5-141">Derleyici tarafından atanan türün `IEnumerable(Of Student)`olduğunu doğrulamak için fare işaretçisini kodunuzda `studentQuery` üzerinde bekletin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="a5ae5-142">Sorguyu çalıştır</span><span class="sxs-lookup"><span data-stu-id="a5ae5-142">Run the Query</span></span>

<span data-ttu-id="a5ae5-143">`studentQuery` değişkeni sorgu çalıştırmanın sonuçlarını değil sorgunun tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="a5ae5-144">Sorgu çalıştırmaya yönelik tipik bir mekanizma `For Each` döngüdür.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="a5ae5-145">Döndürülen dizideki her öğeye döngü yineleme değişkeni üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="a5ae5-146">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="a5ae5-146">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="a5ae5-147">Sorguyu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-147">To run the query</span></span>

1. <span data-ttu-id="a5ae5-148">Aşağıdaki `For Each` döngüsünü projenizdeki sorgunun altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-148">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="a5ae5-149">Veri türünü görmek için fare işaretçisini döngü denetimi değişkeninin üzerine `studentRecord`.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="a5ae5-150">`studentQuery` `Student` örneklerinin bir koleksiyonunu döndürdüğünden `studentRecord` türü `Student`olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="a5ae5-151">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="a5ae5-152">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-152">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="a5ae5-153">Sorguyu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a5ae5-153">Modify the Query</span></span>

<span data-ttu-id="a5ae5-154">Sorgu sonuçlarının belirtilen sırada olmaları durumunda taranması daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="a5ae5-155">Döndürülen sırayı kullanılabilir herhangi bir alana göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-155">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="a5ae5-156">Sonuçları sıralamak için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-156">To order the results</span></span>

1. <span data-ttu-id="a5ae5-157">Aşağıdaki `Order By` yan tümcesini sorgunun `Where` deyimi ve `Select` deyimi arasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="a5ae5-158">`Order By` yan tümcesi, her öğrencinin son adına göre sonuçları A 'dan Z 'ye sıralar.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="a5ae5-159">Son ada göre sıralamak ve sonra adı için sorguya her iki alanı da ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a5ae5-159">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="a5ae5-160">Ayrıca, Z 'den A 'ya sıralama için `Descending` belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-160">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="a5ae5-161">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="a5ae5-162">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-162">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="a5ae5-163">Yerel tanımlayıcı tanıtmak için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-163">To introduce a local identifier</span></span>

1. <span data-ttu-id="a5ae5-164">Sorgu ifadesinde yerel bir tanımlayıcı tanıtmak için bu bölümdeki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="a5ae5-165">Yerel tanımlayıcı bir ara sonuç tutacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="a5ae5-166">Aşağıdaki örnekte `name`, öğrencinin adı ve soyadlarını bir kez birleştirme tutan bir tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="a5ae5-167">Yerel bir tanımlayıcı kolaylık sağlaması için kullanılabilir veya daha önce birden çok kez hesaplanabilecek bir ifadenin sonuçlarını depolayarak performansı geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="a5ae5-168">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="a5ae5-169">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-169">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="a5ae5-170">Select yan tümcesinde bir alan planlamak için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-170">To project one field in the Select clause</span></span>

1. <span data-ttu-id="a5ae5-171">Öğeleri kaynaktaki öğelerden farklı olan bir dizi üreten bir sorgu oluşturmak için bu bölümden sorgu ve `For Each` döngüsünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="a5ae5-172">Aşağıdaki örnekte, kaynak bir `Student` nesneleri koleksiyonudur, ancak her bir nesnenin yalnızca bir üyesi döndürülür: Soyacıadı olan öğrencilerin ilk adı.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="a5ae5-173">`currentStudent.First` bir dize olduğundan, `studentQuery3` tarafından döndürülen sıranın veri türü `IEnumerable(Of String)`, dizeler dizisi olur.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="a5ae5-174">Önceki örneklerde olduğu gibi, `studentQuery3` için bir veri türü ataması, derleyicinin yerel tür çıkarımı kullanılarak belirlenmesi için bırakılır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="a5ae5-175">Atanan türün `IEnumerable(Of String)`olduğunu doğrulamak için fare işaretçisini kodunuzda `studentQuery3` üzerinde bekletin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="a5ae5-176">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="a5ae5-177">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-177">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="a5ae5-178">Select yan tümcesinde anonim bir tür oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a5ae5-178">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="a5ae5-179">Anonim türlerin sorgularda nasıl kullanıldığını görmek için bu bölümden kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="a5ae5-180">Verileri, veri kaynağından, tüm kayıtlar (önceki örneklerde`currentStudent` kayıtlar) veya tek alanlar (önceki bölümde`First`) yerine birden çok alan döndürmek istediğinizde bu sorguları sorgular halinde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="a5ae5-181">Sonuca eklemek istediğiniz alanları içeren yeni bir adlandırılmış tür tanımlamak yerine, `Select` yan tümcesindeki alanları belirtirsiniz ve derleyici, özellikleri olarak bu alanlarla anonim bir tür oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="a5ae5-182">Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a5ae5-182">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="a5ae5-183">Aşağıdaki örnek, akademik derecelendirmesi sırasında akademik derecesi 1 ile 10 arasında olan Seniors 'in adını ve derecesini döndüren bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="a5ae5-184">Bu örnekte, `Select` yan tümcesi anonim bir türün bir örneğini döndürdüğünden ve anonim bir türün kullanılabilir bir adı olmadığı için `studentQuery4` türü çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="a5ae5-185">CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="a5ae5-186">Konsol penceresindeki sonuçları aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-186">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="a5ae5-187">Ek Örnekler</span><span class="sxs-lookup"><span data-stu-id="a5ae5-187">Additional Examples</span></span>

<span data-ttu-id="a5ae5-188">Temel bilgileri anladığınıza göre, aşağıda [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularının esnekliğini ve gücünü gösteren ek örneklerin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="a5ae5-189">Her örnek öncesinde ne yapabileceğinize ilişkin kısa bir açıklamadır.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="a5ae5-190">Gösterilen türü görmek için fare işaretçisini her sorgu için sorgu sonuç değişkeninin üzerine getirin.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="a5ae5-191">Sonuçları oluşturmak için bir `For Each` döngüsü kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-191">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="a5ae5-192">Ek Bilgiler</span><span class="sxs-lookup"><span data-stu-id="a5ae5-192">Additional Information</span></span>

<span data-ttu-id="a5ae5-193">Sorgularla çalışmanın temel kavramlarıyla ilgili bilgi sahibi olduktan sonra, ilgilendiğiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı türü için belge ve örnekleri okumaya hazırsınızdır:</span><span class="sxs-lookup"><span data-stu-id="a5ae5-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider that you are interested in:</span></span>

- [<span data-ttu-id="a5ae5-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="a5ae5-194">LINQ to Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [<span data-ttu-id="a5ae5-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a5ae5-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="a5ae5-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a5ae5-196">LINQ to XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [<span data-ttu-id="a5ae5-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="a5ae5-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="a5ae5-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5ae5-198">See also</span></span>

- [<span data-ttu-id="a5ae5-199">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5ae5-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="a5ae5-200">Visual Basic LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a5ae5-200">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="a5ae5-201">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="a5ae5-201">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="a5ae5-202">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="a5ae5-202">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="a5ae5-203">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="a5ae5-203">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="a5ae5-204">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="a5ae5-204">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="a5ae5-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="a5ae5-205">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="a5ae5-206">Sorgular</span><span class="sxs-lookup"><span data-stu-id="a5ae5-206">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
