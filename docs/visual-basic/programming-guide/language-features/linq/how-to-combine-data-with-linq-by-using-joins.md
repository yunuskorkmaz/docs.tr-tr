---
description: 'Şunları öğrenin: nasıl yapılır: birleştirmeleri kullanarak verileri LINQ ile birleştirme (Visual Basic)'
title: 'Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 69cf0bcfb8d9241afdd0616621f35d7ca93bbb9e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422750"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="19547-103">Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19547-103">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>

<span data-ttu-id="19547-104">Visual Basic, `Join` ve `Group Join` sorgu yan tümcelerini, Koleksiyonlar arasındaki ortak değerlere göre birden çok koleksiyonun içeriğini birleştirmeniz için sağlar.</span><span class="sxs-lookup"><span data-stu-id="19547-104">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="19547-105">Bu değerler *anahtar* değerleri olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="19547-105">These values are known as *key* values.</span></span> <span data-ttu-id="19547-106">İlişkisel veritabanı kavramlarını bilen geliştiriciler `Join` yan tümceyi BIR Iç birleşim ve `Group Join` yan tümce olarak, ETKIN BIR sol dış birleşim olarak tanır.</span><span class="sxs-lookup"><span data-stu-id="19547-106">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="19547-107">Bu konudaki örneklerde, `Join` ve sorgu yan tümcelerini kullanarak verileri birleştirmenin birkaç yolu gösterilmektedir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="19547-107">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="19547-108">Proje oluşturma ve örnek veri ekleme</span><span class="sxs-lookup"><span data-stu-id="19547-108">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="19547-109">Örnek veri ve türleri içeren bir proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19547-109">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="19547-110">Bu konudaki örnekleri çalıştırmak için, Visual Studio 'Yu açın ve yeni bir Visual Basic konsol uygulaması projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19547-110">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="19547-111">Visual Basic tarafından oluşturulan Module1. vb dosyasını çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="19547-111">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="19547-112">Bu konudaki örnekler, `Person` `Pet` Aşağıdaki kod örneğinde ve türlerini ve verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="19547-112">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="19547-113">Bu kodu, `Module1` Visual Basic tarafından oluşturulan varsayılan modüle kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="19547-113">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="19547-114">JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="19547-114">Perform an Inner Join by Using the Join Clause</span></span>  

 <span data-ttu-id="19547-115">Bir Iç BIRLEŞIM, verileri iki koleksiyondan birleştirir.</span><span class="sxs-lookup"><span data-stu-id="19547-115">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="19547-116">Belirtilen anahtar değerlerinin eşleştiği öğeler dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="19547-116">Items for which the specified key values match are included.</span></span> <span data-ttu-id="19547-117">Diğer koleksiyonda eşleşen bir öğeye sahip olmayan her türlü öğe hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="19547-117">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="19547-118">Visual Basic, LINQ bir Iç BIRLEŞIM gerçekleştirmeye yönelik iki seçenek sunar: örtük bir birleşim ve açık birleşim.</span><span class="sxs-lookup"><span data-stu-id="19547-118">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="19547-119">Örtük bir katılım, bir yan tümcesine katılacak koleksiyonları belirtir `From` ve bir yan tümcedeki eşleşen anahtar alanlarını tanımlar `Where` .</span><span class="sxs-lookup"><span data-stu-id="19547-119">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="19547-120">Visual Basic, belirtilen anahtar alanları temelinde iki koleksiyonu örtülü olarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="19547-120">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="19547-121">`Join`Birleşimde hangi anahtar alanlarının kullanılacağı konusunda özel olmasını istediğinizde yan tümcesini kullanarak açık bir JOIN belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19547-121">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="19547-122">Bu durumda, `Where` sorgu sonuçlarını filtrelemek için bir yan tümce hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19547-122">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="19547-123">JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="19547-123">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="19547-124">`Module1`Hem örtük hem de açık iç birleşim örneklerini görmek için aşağıdaki kodu projenizdeki modüle ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19547-124">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="19547-125">Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="19547-125">Perform a Left Outer Join by Using the Group Join Clause</span></span>  

 <span data-ttu-id="19547-126">SOL dış BIRLEŞIM, birleştirmenin sol taraftaki koleksiyonundan tüm öğeleri ve yalnızca birleştirmenin sağ taraftaki koleksiyonundan eşleşen değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="19547-126">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="19547-127">Sol taraftaki koleksiyonda eşleşen bir öğeye sahip olmayan birleştirmenin sağ taraftaki koleksiyonundan herhangi bir öğe sorgu sonucundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="19547-127">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="19547-128">`Group Join`Yan tümce, BIR sol dış birleşimi etkili bir şekilde gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="19547-128">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="19547-129">Genellikle bir sol dış BIRLEŞIM olarak bilinen ve yan tümcesinin döndürdüğü farklar arasındaki fark, `Group Join` `Group Join` yan tümcesinin, sol taraftaki koleksiyondaki her öğe için birleştirmenin sağ tarafındaki koleksiyonundan sonuçlar vermesinin ne olduğunu ifade ediyor.</span><span class="sxs-lookup"><span data-stu-id="19547-129">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="19547-130">İlişkisel bir veritabanında, bir sol dış BIRLEŞIM, sorgu sonucundaki her bir öğenin JOIN içindeki her iki koleksiyondan eşleşen öğeler içerdiği Gruplandırılmamış bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="19547-130">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="19547-131">Bu durumda, birleştirmenin sol taraftaki koleksiyonundaki öğeler, her eşleşen öğe için sağ taraftaki koleksiyondan yinelenir.</span><span class="sxs-lookup"><span data-stu-id="19547-131">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="19547-132">Sonraki yordamı tamamladığınızda bunun nasıl göründüğünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="19547-132">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="19547-133">Sorgu sonuçlarını `Group Join` her gruplanmış sorgu sonucu için bir öğe döndürecek şekilde genişleterek, bir sorgunun sonuçlarını Gruplandırılmamış bir sonuç olarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19547-133">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="19547-134">Bunu gerçekleştirmek için, `DefaultIfEmpty` gruplandırılmış koleksiyonun yönteminde sorgulama yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="19547-134">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="19547-135">Bu, birleştirmenin sol taraftaki koleksiyonundan gelen öğelerin, sağ taraftaki koleksiyondan eşleşen bir sonuçları olmasa bile sorgu sonucuna dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19547-135">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="19547-136">Birleştirmenin sağ taraftaki koleksiyonundan eşleşen bir değer olmadığında varsayılan bir sonuç değeri sağlamak için sorgunuza kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19547-136">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="19547-137">Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="19547-137">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="19547-138">`Module1`Hem gruplanmış bir sol dış birleşimin hem de Gruplandırılmamış bir sol dış birleşimin örneklerini görmek için aşağıdaki kodu projenizdeki modüle ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19547-138">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="19547-139">Bileşik anahtar kullanarak bir JOIN gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="19547-139">Perform a Join by Using a Composite Key</span></span>  

 <span data-ttu-id="19547-140">`And` `Join` `Group Join` Katılmakta olan koleksiyonlardan değerleri eşleştirirken kullanılacak birden çok anahtar alanını tanımlamak için bir veya yan tümcesindeki anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19547-140">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="19547-141">`And`Anahtar sözcüğü, birleştirilecek öğeler için belirtilen tüm anahtar alanlarının eşleşmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19547-141">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="19547-142">Bileşik anahtar kullanarak bir JOIN gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="19547-142">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="19547-143">`Module1`Birleşik anahtar kullanan bir birleşimin örneklerini görmek için aşağıdaki kodu projenizdeki modüle ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19547-143">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="19547-144">Kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="19547-144">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="19547-145">Örnekleri çalıştırmak için kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="19547-145">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="19547-146">`Sub Main` `Module1` Bu konudaki örnekleri çalıştırmak için projenizdeki modülün içindeki modülünü aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="19547-146">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="19547-147">Örnekleri çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="19547-147">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19547-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19547-148">See also</span></span>

- [<span data-ttu-id="19547-149">LINQ</span><span class="sxs-lookup"><span data-stu-id="19547-149">LINQ</span></span>](index.md)
- [<span data-ttu-id="19547-150">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="19547-150">Introduction to LINQ in Visual Basic</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="19547-151">JOIN yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="19547-151">Join Clause</span></span>](../../../language-reference/queries/join-clause.md)
- [<span data-ttu-id="19547-152">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="19547-152">Group Join Clause</span></span>](../../../language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="19547-153">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="19547-153">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="19547-154">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="19547-154">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="19547-155">Sorgular</span><span class="sxs-lookup"><span data-stu-id="19547-155">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="19547-156">LINQ ile Veri Dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="19547-156">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
