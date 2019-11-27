---
title: 'Nasıl yapılır: birleştirmeleri kullanarak verileri LINQ ile birleştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344995"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="ac7b1-102">Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac7b1-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="ac7b1-103">Visual Basic, Koleksiyonlar arasındaki ortak değerlere bağlı olarak birden çok koleksiyonun içeriğini birleştirmenize olanak tanımak için `Join` ve `Group Join` sorgu yan tümcelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="ac7b1-104">Bu değerler *anahtar* değerleri olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-104">These values are known as *key* values.</span></span> <span data-ttu-id="ac7b1-105">İlişkisel veritabanı kavramlarıyla tanıdık geliştiriciler `Join` yan tümcesini bir Iç BIRLEŞIM ve `Group Join` yan tümcesi, etkin bir şekilde sol dış BIRLEŞIM olarak tanır.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="ac7b1-106">Bu konudaki örneklerde `Join` ve `Group Join` sorgu yan tümcelerini kullanarak verileri birleştirmenin birkaç yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="ac7b1-107">Proje oluşturma ve örnek veri ekleme</span><span class="sxs-lookup"><span data-stu-id="ac7b1-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="ac7b1-108">Örnek veri ve türleri içeren bir proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ac7b1-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="ac7b1-109">Bu konudaki örnekleri çalıştırmak için, Visual Studio 'Yu açın ve yeni bir Visual Basic konsol uygulaması projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="ac7b1-110">Visual Basic tarafından oluşturulan Module1. vb dosyasını çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="ac7b1-111">Bu konudaki örnekler, aşağıdaki kod örneğinde `Person` ve `Pet` türlerini ve verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="ac7b1-112">Bu kodu, Visual Basic tarafından oluşturulan varsayılan `Module1` modüle kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="ac7b1-113">JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ac7b1-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="ac7b1-114">Bir Iç BIRLEŞIM, verileri iki koleksiyondan birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="ac7b1-115">Belirtilen anahtar değerlerinin eşleştiği öğeler dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="ac7b1-116">Diğer koleksiyonda eşleşen bir öğeye sahip olmayan her türlü öğe hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="ac7b1-117">Visual Basic, LINQ bir Iç BIRLEŞIM gerçekleştirmeye yönelik iki seçenek sunar: örtük bir birleşim ve açık birleşim.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="ac7b1-118">Örtük bir katılım, bir `From` yan tümcesine katılacak koleksiyonları belirtir ve bir `Where` yan tümcesinde eşleşen anahtar alanlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="ac7b1-119">Visual Basic, belirtilen anahtar alanları temelinde iki koleksiyonu örtülü olarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="ac7b1-120">Birleşimde hangi anahtar alanlarının kullanılacağı konusunda özel olmasını istediğiniz zaman, `Join` yan tümcesini kullanarak açık bir JOIN belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="ac7b1-121">Bu durumda, sorgu sonuçlarını filtrelemek için bir `Where` yan tümcesi hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="ac7b1-122">JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ac7b1-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="ac7b1-123">Hem örtük hem de açık iç birleşim örneklerini görmek için aşağıdaki kodu projenizdeki `Module1` modüle ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="ac7b1-124">Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ac7b1-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="ac7b1-125">SOL dış BIRLEŞIM, birleştirmenin sol taraftaki koleksiyonundan tüm öğeleri ve yalnızca birleştirmenin sağ taraftaki koleksiyonundan eşleşen değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="ac7b1-126">Sol taraftaki koleksiyonda eşleşen bir öğeye sahip olmayan birleştirmenin sağ taraftaki koleksiyonundan herhangi bir öğe sorgu sonucundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="ac7b1-127">`Group Join` yan tümcesi, bir sol dış BIRLEŞIMI etkili bir şekilde gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="ac7b1-128">Genellikle bir sol dış BIRLEŞIM olarak bilinen ve `Group Join` yan tümcesinin döndürdüğü fark, `Group Join` yan tümcesinin, sol taraftaki koleksiyondaki her öğe için birleştirmenin sağ taraftaki koleksiyonundan sonuçlar vermesinin ne olduğunu gösteren fark.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="ac7b1-129">İlişkisel bir veritabanında, bir sol dış BIRLEŞIM, sorgu sonucundaki her bir öğenin JOIN içindeki her iki koleksiyondan eşleşen öğeler içerdiği Gruplandırılmamış bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="ac7b1-130">Bu durumda, birleştirmenin sol taraftaki koleksiyonundaki öğeler, her eşleşen öğe için sağ taraftaki koleksiyondan yinelenir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="ac7b1-131">Sonraki yordamı tamamladığınızda bunun nasıl göründüğünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="ac7b1-132">Bir `Group Join` sorgusunun sonuçlarını, gruplanmış her sorgu sonucu için bir öğe döndürecek şekilde genişleterek, Gruplandırılmamış bir sonuç olarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="ac7b1-133">Bunu gerçekleştirmek için, gruplandırılmış koleksiyonun `DefaultIfEmpty` yönteminde sorgulama yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="ac7b1-134">Bu, birleştirmenin sol taraftaki koleksiyonundan gelen öğelerin, sağ taraftaki koleksiyondan eşleşen bir sonuçları olmasa bile sorgu sonucuna dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="ac7b1-135">Birleştirmenin sağ taraftaki koleksiyonundan eşleşen bir değer olmadığında varsayılan bir sonuç değeri sağlamak için sorgunuza kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="ac7b1-136">Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ac7b1-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="ac7b1-137">Hem gruplanmış bir sol dış birleşimin hem de Gruplandırılmamış bir sol dış birleşimin örneklerini görmek için aşağıdaki kodu projenizdeki `Module1` modüle ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="ac7b1-138">Bileşik anahtar kullanarak bir JOIN gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ac7b1-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="ac7b1-139">Katılmakta olan koleksiyonlardan değerleri eşleştirirken kullanılacak birden çok anahtar alanını tanımlamak için bir `Join` veya `Group Join` yan tümcesindeki `And` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="ac7b1-140">`And` anahtar sözcüğü belirtilen tüm anahtar alanlarının birleştirilecek öğelerin eşleşmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="ac7b1-141">Bileşik anahtar kullanarak bir JOIN gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ac7b1-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="ac7b1-142">Bileşik anahtar kullanan bir birleşimin örneklerini görmek için, aşağıdaki kodu projenizdeki `Module1` modüle ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="ac7b1-143">Kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ac7b1-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="ac7b1-144">Örnekleri çalıştırmak için kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="ac7b1-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="ac7b1-145">Bu konudaki örnekleri çalıştırmak için projenizdeki `Module1` modülündeki `Sub Main` aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="ac7b1-146">Örnekleri çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7b1-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-147">See also</span></span>

- [<span data-ttu-id="ac7b1-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="ac7b1-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="ac7b1-149">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="ac7b1-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ac7b1-150">Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ac7b1-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="ac7b1-151">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ac7b1-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="ac7b1-152">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ac7b1-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ac7b1-153">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ac7b1-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="ac7b1-154">Sorgular</span><span class="sxs-lookup"><span data-stu-id="ac7b1-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ac7b1-155">LINQ (C#) Ile veri dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="ac7b1-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
