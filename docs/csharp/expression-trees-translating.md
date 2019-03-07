---
title: İfade ağaçları çevirme
description: Bu ifade ağacını değiştirilmiş bir kopyasını oluşturulurken bir ifade ağacı içindeki her bir düğümün ziyaret öğrenin.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 4c14837c1d92845991d8ea9990b77eb9052757d8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490079"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="fa8f6-103">İfade ağaçları çevirme</span><span class="sxs-lookup"><span data-stu-id="fa8f6-103">Translating Expression Trees</span></span>

[<span data-ttu-id="fa8f6-104">Önceki--İfade derleme</span><span class="sxs-lookup"><span data-stu-id="fa8f6-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="fa8f6-105">Bu son bölümde her bir ifade ağacı düğümünde Bu ifade ağacını değiştirilmiş bir kopyasını oluşturulurken ziyaret öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="fa8f6-106">Bu iki önemli senaryoda kullanacağınız tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="fa8f6-107">İlk, böylece başka bir ortama çevrilebilir bir ifade ağacı tarafından ifade algoritmaları öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="fa8f6-108">Oluşturulmuş algoritma değiştirmek istediğinizde saniyedir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="fa8f6-109">Bu günlük, yöntem çağrılarını ıntercept ekleyip bunları veya başka amaçlarla izlemek olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="fa8f6-110">Çevirme ziyaret edin</span><span class="sxs-lookup"><span data-stu-id="fa8f6-110">Translating is Visiting</span></span>

<span data-ttu-id="fa8f6-111">Bir ifade ağacına çevrilemedi derleme kodu ne zaten bir ağaçtaki tüm düğümleri ziyaret etmek için gördüğünüz bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="fa8f6-112">Bir ifade ağacı Çevir, tüm düğümleri ziyaret edin ve bunları ziyaret ederken, yeni bir ağaç oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="fa8f6-113">Yeni ağaç özgün düğümleri veya ağacında yerleştirmiş olduğunuz yeni düğümler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="fa8f6-114">Bu eylem bir ifade ağacı ziyaret ve bazı değiştirme düğümlerle yeni bir ağaç oluşturma görelim.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="fa8f6-115">Bu örnekte, tüm sabiti şimdi on kat daha büyük bir sabit ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="fa8f6-116">Aksi takdirde, ifade ağacına değiştirmeden bırakacağız.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="fa8f6-117">Sabit değerini okumak ve yeni bir sabit ile değiştirerek yerine bu değiştirme sabit düğüm çarpma işlemi gerçekleştiren yeni bir düğüm ile değiştirerek oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="fa8f6-118">Sabit düğüm bulduğunuzda, burada, orijinal sabit ve sabit alt öğeleri olan yeni bir çarpma düğüm oluşturma `10`:</span><span class="sxs-lookup"><span data-stu-id="fa8f6-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="fa8f6-119">Özgün düğüme yedekle değiştirerek yeni bir ağaç yapacağımız değişiklikler burada sona içeren oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="fa8f6-120">Biz, derleme ve değiştirilen ağaç yürütme doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="fa8f6-121">Yeni bir ağaç oluşturmak mevcut Ağaçtaki düğümler ziyaret yeni düğümler oluşturma ve bunları ağacına ekleyerek bir birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="fa8f6-122">Bu örnek, sabit olan ifade ağaçları önemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="fa8f6-123">Yukarıda oluşturulan yeni ağaç yeni oluşturulan düğümleri ve mevcut ağaç düğümleri bir karışımını içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="fa8f6-124">Mevcut Ağaçtaki düğümler değiştirilemediğinden güvenli olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="fa8f6-125">Bu, önemli bellek sanayi neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="fa8f6-126">Aynı düğüm bir ağaç boyunca veya birden fazla ifade ağaçları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="fa8f6-127">Düğümleri değiştirilemediğinden aynı düğümde olabilir herhangi bir zamanda yeniden kendi gerekli.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="fa8f6-128">Geçiş ve ek yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="fa8f6-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="fa8f6-129">Bu ek düğüm ağacı gezer ve sonucu hesaplar ikinci bir ziyaretçi oluşturarak doğrulayalım.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="fa8f6-130">Şu ana kadar gördüğünüz ziyaretçi birkaç değişiklik yaparak bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="fa8f6-131">Bu yeni sürümde ziyaretçi toplama işlemi bu noktaya kadar kısmi toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="fa8f6-132">Sabit bir ifade için yalnızca sabit ifadenin değeri olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="fa8f6-133">Ağaçların geçiş sonra bir toplama ifadesi sonucu sol ve sağ işlenen toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="fa8f6-134">Kodu buraya olayın yoktur ancak kullanılmalarını kavramlardır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="fa8f6-135">Bu kod, alt derinliği ilk aramada ziyaret eder.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="fa8f6-136">Sabit düğüm karşılaştığında, ziyaretçi sabit değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="fa8f6-137">Ziyaretçi her iki alt öğe ziyaret ettikten sonra alt alt ağacı için hesaplanan toplamı hesaplanan.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="fa8f6-138">Ayrıca düğüm artık, sum hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="fa8f6-139">İfade ağacı tüm düğümlerin ziyaret sonra toplamı hesaplanan.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="fa8f6-140">Örnek hata ayıklayıcıda çalıştırma ve izleme yürütme yürütme izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="fa8f6-141">Şimdi, düğümleri nasıl analiz edilir ve toplamı ağacının çapraz geçişi tarafından nasıl hesaplanır izlemenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="fa8f6-142">Olayın izleme bilgilerini içeren bir toplama yöntemi güncelleştirilmiş bir sürümünü şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fa8f6-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="fa8f6-143">Aynı ifadeye çalışan aşağıdaki çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="fa8f6-143">Running it on the same expression yields the following output:</span></span>

```
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

<span data-ttu-id="fa8f6-144">İzleme çıkışı ve yukarıdaki kod örneği takip etmek.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="fa8f6-145">Nasıl kod her düğüm ziyaret eder ve ağaç geçer ve toplamı bulur toplamı hesaplar out çalışabilmek için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="fa8f6-146">Şimdi, farklı bir çalışma zamanında tarafından verilen ifadeyle bakalım `sum1`:</span><span class="sxs-lookup"><span data-stu-id="fa8f6-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="fa8f6-147">Bu ifade İnceleme gelen çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fa8f6-147">Here's the output from examining this expression:</span></span>

```
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

<span data-ttu-id="fa8f6-148">Son yanıt aynı olsa da, ağaç geçişi tamamen farklıdır.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="fa8f6-149">Ağaç önce gerçekleşen farklı işlemler ile oluşturulmuş olduğundan düğümler farklı bir sırada imkansız.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="fa8f6-150">Daha fazla öğrenme</span><span class="sxs-lookup"><span data-stu-id="fa8f6-150">Learning More</span></span>

<span data-ttu-id="fa8f6-151">Bu örnek, geçiş ve bir ifade ağacı tarafından temsil edilen algoritmaları yorumlamak için derleme kodu küçük bir kısmı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="fa8f6-152">İfade ağaçları başka bir dile çevirir bir genel amaçlı kitaplık oluşturmak için gereken tüm iş tam bir açıklaması için lütfen okuyun [Bu seriyi](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) Matt Warren tarafından.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="fa8f6-153">Herhangi bir ifade ağacı içinde bulabileceğiniz kod çevirme konusunda harika ayrıntıya gider.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="fa8f6-154">Umarım ifade ağaçları'nın gerçek gücünü artık gördünüz.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="fa8f6-155">Bir dizi kodla incelemek, bu kodu ister ve değiştirilen sürüm yürütme herhangi bir değişiklik yapın.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="fa8f6-156">İfade ağaçları sabit olduğundan, mevcut ağaçları bileşenlerini kullanarak yeni ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="fa8f6-157">Bu, değiştirilmiş bir ifade ağacı oluşturmak için gerekli bellek miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="fa8f6-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="fa8f6-158">Sonraki--Özetle</span><span class="sxs-lookup"><span data-stu-id="fa8f6-158">Next -- Summing up</span></span>](expression-trees-summary.md)
