---
title: İfade Ağaçlarını Çevirme
description: Bu ifade ağacının değiştirilmiş bir kopyasını yaparken bir ifade ağacındaki her düğümü nasıl ziyaret edin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: f60c447d5c89aa83f85073e642e621608131ed8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76115784"
---
# <a name="translate-expression-trees"></a><span data-ttu-id="93e43-103">İfade ağaçlarını çevir</span><span class="sxs-lookup"><span data-stu-id="93e43-103">Translate expression trees</span></span>

[<span data-ttu-id="93e43-104">Önceki -- Yapı İfadeleri</span><span class="sxs-lookup"><span data-stu-id="93e43-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="93e43-105">Bu son bölümde, bu ifade ağacının değiştirilmiş bir kopyasını yaparken bir ifade ağacındaki her düğümü nasıl ziyaret edeceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="93e43-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="93e43-106">Bunlar, iki önemli senaryoda kullanacağınız tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="93e43-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="93e43-107">Birincisi, bir ifade ağacı tarafından ifade edilen algoritmaları anlamak, böylece başka bir ortama çevrilebilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="93e43-108">İkincisi, oluşturulan algoritmayı değiştirmek istediğiniz dedir.</span><span class="sxs-lookup"><span data-stu-id="93e43-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="93e43-109">Bu, günlüğe kaydetme, yöntem aramalarını engellemek ve bunları izlemek veya başka amaçlar eklemek olabilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="93e43-110">Tercüme Etmek Ziyaret Etmektir</span><span class="sxs-lookup"><span data-stu-id="93e43-110">Translating is Visiting</span></span>

<span data-ttu-id="93e43-111">İfade ağacını çevirmek için oluşturduğunuz kod, ağaçtaki tüm düğümleri ziyaret etmek için gördüğünüz şeyin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="93e43-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="93e43-112">Bir ifade ağacını çevirdiğinizde, tüm düğümleri ziyaret edeyim ve onları ziyaret ederken yeni ağaç oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="93e43-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="93e43-113">Yeni ağaç, özgün düğümlere veya ağaca yerleştirdiğiniz yeni düğümlere başvurular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="93e43-114">Bir ifade ağacını ziyaret ederek ve bazı değiştirme düğümleri ile yeni bir ağaç oluşturarak bunu iş başında görelim.</span><span class="sxs-lookup"><span data-stu-id="93e43-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="93e43-115">Bu örnekte, herhangi bir sabiti on kat daha büyük bir sabitle değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="93e43-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="93e43-116">Aksi takdirde, ifade ağacını sağlam bırakırız.</span><span class="sxs-lookup"><span data-stu-id="93e43-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="93e43-117">Sabitin değerini okumak ve yeni bir sabitle değiştirmek yerine, sabit düğümü çarpma işlemini gerçekleştiren yeni bir düğümle değiştirerek bu değişikliği yapacağız.</span><span class="sxs-lookup"><span data-stu-id="93e43-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="93e43-118">Burada, sabit bir düğüm bulduğunuzda, çocukları orijinal sabit olan yeni bir çarpma `10`düğümü oluşturursunuz ve sabit:</span><span class="sxs-lookup"><span data-stu-id="93e43-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="93e43-119">Orijinal düğümü yedekle değiştirerek, modifikasyonlarımızı içeren yeni bir ağaç oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="93e43-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="93e43-120">Değiştirilen ağacı derleyip çalıştırarak bunu doğrulayabiliriz.</span><span class="sxs-lookup"><span data-stu-id="93e43-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="93e43-121">Yeni bir ağaç oluşturmak, varolan ağaçtaki düğümleri ziyaret etmenin ve yeni düğümler oluşturmanın ve bunları ağaca eklemenin bir kombinasyonudur.</span><span class="sxs-lookup"><span data-stu-id="93e43-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="93e43-122">Bu örnek, ifade ağaçlarının değişmez olmasının önemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="93e43-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="93e43-123">Yukarıda oluşturulan yeni ağacın yeni oluşturulan düğümlerin ve varolan ağaçtan düğümlerin bir karışımını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="93e43-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="93e43-124">Bu güvenlidir, çünkü varolan ağaçtaki düğümler değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="93e43-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="93e43-125">Bu önemli bellek verimliliği neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="93e43-126">Aynı düğümler bir ağaç boyunca veya birden çok ifade ağacında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="93e43-127">Düğümler değiştirilemediğinden, aynı düğüm gerektiğinde yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-127">Since nodes can't be modified, the same node can be reused whenever it's needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="93e43-128">Bir Eklemeyi Geçiş ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="93e43-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="93e43-129">Bunu, ek düğümler ağacında yürüyen ve sonucu hesaplayan ikinci bir ziyaretçi oluşturarak doğrulayalım.</span><span class="sxs-lookup"><span data-stu-id="93e43-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="93e43-130">Bunu, şimdiye kadar gördüğünüz ziyaretçiiçin birkaç değişiklik yaparak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e43-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="93e43-131">Bu yeni sürümde, ziyaretçi ekleme işleminin kısmi toplamını bu noktaya kadar döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="93e43-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="93e43-132">Sabit bir ifade için, bu sadece sabit ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="93e43-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="93e43-133">Ek bir ifade için, sonuç, bu ağaçlar geçildikten sonra, sol ve sağ operands toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="93e43-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="93e43-134">Burada biraz kod var, ama kavramlar çok yaklaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="93e43-135">Bu kod, derinlemesine ilk aramada çocukları ziyaret eder.</span><span class="sxs-lookup"><span data-stu-id="93e43-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="93e43-136">Sabit bir düğümle karşılaştığında, ziyaretçi sabitin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="93e43-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="93e43-137">Ziyaretçi her iki çocuğu da ziyaret ettikten sonra, bu çocuklar bu alt ağaç için hesaplanan toplamı hesaplamış olacaklar.</span><span class="sxs-lookup"><span data-stu-id="93e43-137">After the visitor has visited both children, those children will have computed the sum computed for that subtree.</span></span> <span data-ttu-id="93e43-138">Ek düğüm artık toplamını hesaplayabilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="93e43-139">İfade ağacındaki tüm düğümler ziyaret edildikten sonra, toplam hesaplanmış olur.</span><span class="sxs-lookup"><span data-stu-id="93e43-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="93e43-140">Örneği hata ayıklamada çalıştırarak ve yürütmeyi izleyerek yürütmeyi izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e43-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="93e43-141">Düğümlerin nasıl analiz edildiğini ve ağacın geçişiyle toplamın nasıl hesaplandırılanını izlemeyi kolaylaştıralım.</span><span class="sxs-lookup"><span data-stu-id="93e43-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="93e43-142">Aşağıda, agrega yönteminin oldukça fazla izleme bilgisi içeren güncelleştirilmiş bir sürümü verem:</span><span class="sxs-lookup"><span data-stu-id="93e43-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="93e43-143">Aynı ifade üzerinde çalıştırmak aşağıdaki çıktıyı verir:</span><span class="sxs-lookup"><span data-stu-id="93e43-143">Running it on the same expression yields the following output:</span></span>

```output
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="93e43-144">Çıktıyı izleyin ve yukarıdaki kodda izleyin.</span><span class="sxs-lookup"><span data-stu-id="93e43-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="93e43-145">Kodun her düğümü nasıl ziyaret ettiğinizi ve ağaçtan geçerken toplamı nasıl hesaplayabilmelisinizi ve toplamı nasıl bulduğunu öğrenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e43-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="93e43-146">Şimdi, farklı bir çalışma bakalım, ifade ile: `sum1`</span><span class="sxs-lookup"><span data-stu-id="93e43-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="93e43-147">Bu ifadeyi incelemenin çıktısı aşağıda verebisi aşağıda veda edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93e43-147">Here's the output from examining this expression:</span></span>

```output
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="93e43-148">Son yanıt aynı olsa da, ağaç geçişi tamamen farklıdır.</span><span class="sxs-lookup"><span data-stu-id="93e43-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="93e43-149">Ağaç ilk meydana gelen farklı işlemler ile inşa edildi, çünkü düğümleri farklı bir sırada seyahat edilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="93e43-150">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="93e43-150">Learning More</span></span>

<span data-ttu-id="93e43-151">Bu örnek, bir ifade ağacı tarafından temsil edilen algoritmaları geçiş ve yorumlamak için oluşturacağınız kodun küçük bir alt kümesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="93e43-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="93e43-152">İfade ağaçlarını başka bir dile çeviren genel amaçlı bir kütüphane oluşturmak için gereken tüm çalışmaların tam bir tartışması için lütfen Matt Warren'ın [bu dizisini](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) okuyun.</span><span class="sxs-lookup"><span data-stu-id="93e43-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="93e43-153">Bir ifade ağacında bulabileceğiniz kodlardan herhangi birinin nasıl çevrilebileceği hakkında ayrıntılı bilgi edinilir.</span><span class="sxs-lookup"><span data-stu-id="93e43-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="93e43-154">Umarım ifade ağaçlarının gerçek gücünü görmüşsunuzdur.</span><span class="sxs-lookup"><span data-stu-id="93e43-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="93e43-155">Bir kod kümesini inceleyebilir, bu kodda istediğiniz değişiklikleri yapabilir ve değiştirilen sürümü çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e43-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="93e43-156">İfade ağaçları değişmez olduğundan, varolan ağaçların bileşenlerini kullanarak yeni ağaçlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e43-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="93e43-157">Bu, değiştirilmiş ifade ağaçları oluşturmak için gereken bellek miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="93e43-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="93e43-158">Sonraki -- Özetleme</span><span class="sxs-lookup"><span data-stu-id="93e43-158">Next -- Summing up</span></span>](expression-trees-summary.md)
