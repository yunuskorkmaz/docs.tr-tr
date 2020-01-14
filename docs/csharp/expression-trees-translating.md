---
title: Ifade ağaçları çevriliyor
description: Bu ifade ağacının değiştirilmiş bir kopyasını oluştururken bir ifade ağacındaki her bir düğümü ziyaret etmeyi öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: a4cb40e439726e5fff60fe697da70d61bb24cb68
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937228"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="6d8c7-103">Ifade ağaçları çevriliyor</span><span class="sxs-lookup"><span data-stu-id="6d8c7-103">Translating Expression Trees</span></span>

[<span data-ttu-id="6d8c7-104">Previous--Ifadeleri derleme</span><span class="sxs-lookup"><span data-stu-id="6d8c7-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="6d8c7-105">Bu son bölümde, bu ifade ağacının değiştirilmiş bir kopyasını oluştururken bir ifade ağacındaki her bir düğümü ziyaret etmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="6d8c7-106">Bunlar, iki önemli senaryoda kullanacağınız tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="6d8c7-107">Birincisi, başka bir ortama çevrilebilmesi için bir ifade ağacı tarafından ifade edilen algoritmaları anlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="6d8c7-108">İkincisi, oluşturulan algoritmayı değiştirmek istediğinizde olur.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="6d8c7-109">Bu, günlük kaydı eklemek, Yöntem çağrılarını ele almak ve izlemek ya da başka amaçlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="6d8c7-110">Çeviri ziyaret ediyor</span><span class="sxs-lookup"><span data-stu-id="6d8c7-110">Translating is Visiting</span></span>

<span data-ttu-id="6d8c7-111">Bir ifade ağacını çevirmek için oluşturduğunuz kod, bir ağaçtaki tüm düğümleri ziyaret etmek için zaten gördüğünüze ait bir uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="6d8c7-112">Bir ifade ağacını çevirirken, tüm düğümleri ziyaret edersiniz ve ziyaret edilirken yeni ağacı derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="6d8c7-113">Yeni ağaç orijinal düğümlere veya ağaca yerleştirdiğiniz yeni düğümlere başvuru içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="6d8c7-114">Bu işlemi, bir ifade ağacını ziyaret ederek ve değişiklik düğümleri içeren yeni bir ağaç oluşturarak görelim.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="6d8c7-115">Bu örnekte, her sabiti on kat daha büyük olan bir sabit ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="6d8c7-116">Aksi takdirde, ifade ağacını bozulmadan bırakıyoruz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="6d8c7-117">Sabitin değerini okumak ve yeni bir sabitle değiştirmek yerine, sabit düğümü çarpma işlemini gerçekleştiren yeni bir düğümle değiştirerek bu değişikliği yapacağız.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="6d8c7-118">Burada, sabit bir düğüm bulduktan sonra, alt öğeleri orijinal sabit olan ve sabit `10`yeni bir çarpma düğümü oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="6d8c7-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="6d8c7-119">Özgün düğümü yenisiyle değiştirerek, değişikliklerinizi içeren yeni bir ağaç oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="6d8c7-120">Değiştirilmiş ağacı derleyip yürüterek bunu doğrulayabiliriz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="6d8c7-121">Yeni bir ağaç oluşturmak, var olan ağaçtaki düğümleri ziyaret etme ve yeni düğümler oluşturma ve bunları ağaca ekleme birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="6d8c7-122">Bu örnek, ifade ağaçlarının sabit olmasının önemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="6d8c7-123">Yukarıda oluşturulan yeni ağacın yeni oluşturulan düğümlerin bir karışımını ve var olan ağaçtaki düğümleri içerdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="6d8c7-124">Bu, var olan ağaçtaki düğümler değiştirilemediği için güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="6d8c7-125">Bu, önemli ölçüde bellek verimliliklerini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="6d8c7-126">Aynı düğümler bir ağacın tamamında veya birden çok ifade ağacında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="6d8c7-127">Düğümler değiştirilemediğinden, her gerektiğinde aynı düğüm yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="6d8c7-128">Çapraz geçiş ve yürütme</span><span class="sxs-lookup"><span data-stu-id="6d8c7-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="6d8c7-129">Ayrıca, ek düğüm ağacını gösteren ve sonucu hesaplayan ikinci bir ziyaretçi oluşturarak bunu doğrulayalım.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="6d8c7-130">Şimdiye kadar gördüğünüz ziyaretçi üzerinde birkaç değişiklik yaparak bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="6d8c7-131">Bu yeni sürümde ziyaretçi, toplama işleminin kısmi toplamını bu noktaya kadar döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="6d8c7-132">Sabit bir ifade için yalnızca sabit ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="6d8c7-133">Bir toplama ifadesi için, bu ağaçlar alındıktan sonra, sonuç sol ve sağ işlenenlerinin toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="6d8c7-134">Burada bir kod biraz daha vardır ancak kavramlar çok ulaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="6d8c7-135">Bu kod, alt öğeleri derinlemesine bir ilk aramada ziyaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="6d8c7-136">Sabit bir düğümle karşılaştığında, ziyaretçi sabit değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="6d8c7-137">Ziyaretçi her iki öğeyi de ziyaret ettikten sonra bu alt ağaç için hesaplanan toplamı hesaplamıştır.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="6d8c7-138">Toplama düğümü artık toplamını hesaplaedebilir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="6d8c7-139">İfade ağacındaki tüm düğümler ziyaret edildikten sonra toplam hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="6d8c7-140">Örneği hata ayıklayıcıda çalıştırıp yürütmeyi izleyerek yürütmeyi izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="6d8c7-141">Düğümlerin nasıl çözümlenmekte olduğunu ve ağacın çapraz geçiş yaparak nasıl hesaplantığını izlemeyi daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="6d8c7-142">Toplam yönteminin, tam olarak bir izleme bilgisi içeren güncelleştirilmiş bir sürümü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6d8c7-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="6d8c7-143">Aynı ifadede çalıştırmak aşağıdaki çıktıyı verir:</span><span class="sxs-lookup"><span data-stu-id="6d8c7-143">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="6d8c7-144">Çıktıyı izleyin ve yukarıdaki kodda izleyin.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="6d8c7-145">Kodun her bir düğümü nasıl ziyaret edebilmeli ve toplam ağaçta gezinilerek toplamı nasıl hesapladığını ve toplamı bulabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="6d8c7-146">Şimdi, `sum1`tarafından verilen ifadeyle farklı bir çalıştırmaya bakalım:</span><span class="sxs-lookup"><span data-stu-id="6d8c7-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="6d8c7-147">Bu ifadeyi inceleyerek çıkış şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="6d8c7-147">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="6d8c7-148">Nihai yanıt aynı olsa da, ağaç geçişi tamamen farklıdır.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="6d8c7-149">Ağaç, ilk olarak oluşan farklı işlemlerle oluşturulduğundan, bu düğümler farklı bir sıraya göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="6d8c7-150">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="6d8c7-150">Learning More</span></span>

<span data-ttu-id="6d8c7-151">Bu örnek, bir ifade ağacı tarafından temsil edilen algoritmaları çapraz olarak geçirmek ve yorumlamak için derleyerek kodun küçük bir alt kümesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="6d8c7-152">İfade ağaçlarını başka bir dile çeviren genel amaçlı bir kitaplık oluşturmak için gereken tüm çalışmalar hakkında ayrıntılı bir açıklama için lütfen [Bu seriyi](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) Matt Warren ile okuyun.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="6d8c7-153">Bir ifade ağacında bulabileceğiniz herhangi bir kodun nasıl çevrilebileceğini gösteren harika bir ayrıntıya gider.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="6d8c7-154">Artık ifade ağaçlarının gerçek gücünü gördük.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="6d8c7-155">Bir kod kümesini inceleyebilir, bu koda istediğiniz değişiklikleri yapabilir ve değiştirilen sürümü yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="6d8c7-156">İfade ağaçları sabit olduğundan, varolan ağaçların bileşenlerini kullanarak yeni ağaçlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="6d8c7-157">Bu, değiştirilen ifade ağaçları oluşturmak için gereken bellek miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="6d8c7-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="6d8c7-158">İleri--toplam</span><span class="sxs-lookup"><span data-stu-id="6d8c7-158">Next -- Summing up</span></span>](expression-trees-summary.md)
