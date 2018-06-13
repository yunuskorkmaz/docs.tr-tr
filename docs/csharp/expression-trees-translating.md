---
title: İfade ağaçları çevirme
description: Bu ifade ağacına değiştirilmiş bir kopyasını oluşturulurken bir ifade ağacına her düğümünde ziyaret öğrenin.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 9483cbe75b4bf5a38dd791633c852eb0b8473944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217122"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="f3840-103">İfade ağaçları çevirme</span><span class="sxs-lookup"><span data-stu-id="f3840-103">Translating Expression Trees</span></span>

[<span data-ttu-id="f3840-104">Önceki--Yapı ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f3840-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="f3840-105">Son Bu bölümde, bir ifade ağacına içindeki her düğüm bu ifade ağacına değiştirilmiş bir kopyasını oluşturulurken ziyaret etmek öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f3840-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="f3840-106">Bu iki önemli senaryolarda kullanacağınız tekniklerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f3840-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="f3840-107">İlk böylece başka bir ortama çevrilebilir bir ifade ağacına tarafından ifade algoritmaları anlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f3840-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="f3840-108">Oluşturuldu algoritması değiştirmek istediğinizde saniyedir.</span><span class="sxs-lookup"><span data-stu-id="f3840-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="f3840-109">Bu günlük kaydı ekleyin, yöntem çağrıları durdurur ve bunları veya başka amaçlarla izlemek için olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3840-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="f3840-110">Çevirme ziyaret edin</span><span class="sxs-lookup"><span data-stu-id="f3840-110">Translating is Visiting</span></span>

<span data-ttu-id="f3840-111">Bir ifade ağacına çevrilemedi derleme kodu ne ağacındaki tüm düğümleri ziyaret etmek için gördünüz bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="f3840-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="f3840-112">Bir ifade ağacına çevrilemedi, tüm düğümlere ziyaret edin ve bunları ziyaret ederken yeni ağacını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f3840-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="f3840-113">Yeni ağaç özgün düğümleri veya ağacında yerleştirdiğiniz yeni düğümler başvurular içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3840-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="f3840-114">Bu eylem bir ifade ağacına ziyaret eden ve bazı değiştirme düğümlerle yeni bir ağaç oluşturarak görelim.</span><span class="sxs-lookup"><span data-stu-id="f3840-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="f3840-115">Bu örnekte, tüm sabit şimdi on kez daha büyük bir sabit ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f3840-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="f3840-116">Aksi takdirde, ifade ağacına sağlam bırakacağız.</span><span class="sxs-lookup"><span data-stu-id="f3840-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="f3840-117">Sabit değer okuma ve yeni bir sabit ile değiştirerek yerine bu değiştirme çarpma gerçekleştiren sahip yeni bir düğüm sabit düğüm değiştirerek vermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="f3840-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="f3840-118">Burada, sabit bir düğüm bulduktan sonra alt öğeleri olan özgün sabiti ve sabiti yeni bir çarpma düğüm oluşturun `10`:</span><span class="sxs-lookup"><span data-stu-id="f3840-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="f3840-119">Özgün düğüme ikame ile değiştirerek, yeni bir ağaç bizim değişiklikler içeren biçimlendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="f3840-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="f3840-120">Biz, derleme ve değiştirilen ağaç yürütme doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3840-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="f3840-121">Yeni bir ağacı oluşturma, varolan ağacında düğümlerin ziyaret ve yeni düğümler oluşturma ve bunları ağacına ekleyerek bir birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="f3840-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="f3840-122">Bu örnek değişmez olan ifade ağaçları önemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3840-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="f3840-123">Yukarıda oluşturduğunuz yeni ağaç yeni oluşturulan düğümlerini ve mevcut ağaç düğümü bileşimi içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f3840-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="f3840-124">Varolan ağacında düğümlerin değiştirdiğinden güvenli olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3840-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="f3840-125">Bu, önemli bellek verimliliği neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3840-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="f3840-126">Aynı düğümlerine bir ağaç boyunca veya birden çok ifade ağaçları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3840-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="f3840-127">Düğümleri değiştirilemediği aynı düğüm olabilir her yeniden kendi gerekli.</span><span class="sxs-lookup"><span data-stu-id="f3840-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="f3840-128">Çapraz geçiş yapma ve ek yürütme</span><span class="sxs-lookup"><span data-stu-id="f3840-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="f3840-129">Şimdi bu toplama düğümlerin ağacı anlatılmaktadır ve sonucu hesaplar ikinci bir ziyaretçi oluşturarak doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f3840-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="f3840-130">Şu ana kadar gördüğünüz vistor birkaç değişiklik yaparak bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3840-130">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="f3840-131">Bu yeni sürümde ziyaretçi ekleme işlemi bu noktaya kadar kısmi toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3840-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="f3840-132">Sabit bir ifade için yalnızca sabit ifadenin değerini olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3840-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="f3840-133">Bu ağaçlar geçiş sonra bir toplama ifadesi için sonuç sol ve sağ işlenen toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="f3840-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="f3840-134">Oldukça biraz kod burada yoktur, ancak kavramları kullanılmalarını.</span><span class="sxs-lookup"><span data-stu-id="f3840-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="f3840-135">Bu kod derinliği ilk aramaya alt ziyaret eder.</span><span class="sxs-lookup"><span data-stu-id="f3840-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="f3840-136">Sabit düğüm ile karşılaştığında ziyaretçi sabiti değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3840-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="f3840-137">Ziyaretçi her iki alt ziyaret ettikten sonra bu alt alt ağacı için hesaplanan toplam hesaplanan.</span><span class="sxs-lookup"><span data-stu-id="f3840-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="f3840-138">Ek düğüm artık kendi sum hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3840-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="f3840-139">İfade ağacına tüm düğümlerin ziyaret sonra toplamı hesaplandıktan.</span><span class="sxs-lookup"><span data-stu-id="f3840-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="f3840-140">Hata Ayıklayıcısı'ndaki örnek çalıştıran ve yürütme izleme yürütme izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3840-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="f3840-141">İzleme düğümleri nasıl analiz ve toplamı travsersing tarafından nasıl hesaplanır daha kolay olalım ağacı.</span><span class="sxs-lookup"><span data-stu-id="f3840-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="f3840-142">İzleme bilgilerinin oldukça bit içerir toplama yöntemi güncelleştirilmiş bir sürümünü şöyledir:</span><span class="sxs-lookup"><span data-stu-id="f3840-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="f3840-143">Aynı ifadeye çalıştıran aşağıdaki çıktısı verir:</span><span class="sxs-lookup"><span data-stu-id="f3840-143">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="f3840-144">İzleme çıkışı ve yukarıdaki kod izleyin.</span><span class="sxs-lookup"><span data-stu-id="f3840-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="f3840-145">Nasıl kodu her düğüm ziyaret eder ve ağacıyla gider ve toplamını bulur toplamı hesaplar çıkışı iş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3840-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="f3840-146">Şimdi, Farklı Çalıştır tarafından verilen ifade ile bakalım `sum1`:</span><span class="sxs-lookup"><span data-stu-id="f3840-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="f3840-147">Bu ifade inceleniyor gelen çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="f3840-147">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="f3840-148">Son yanıt aynı olsa da, ağaç geçişi tamamen farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f3840-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="f3840-149">Ağaç önce yürütülen farklı işlem ile oluşturulan çünkü düğümlerin farklı bir sırayla seyahat.</span><span class="sxs-lookup"><span data-stu-id="f3840-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="f3840-150">Daha fazla öğrenme</span><span class="sxs-lookup"><span data-stu-id="f3840-150">Learning More</span></span>

<span data-ttu-id="f3840-151">Bu örnek, küçük bir alt kümesine çapraz geçiş ve bir ifade ağacına tarafından temsil edilen algoritmaları yorumlamak için derleme kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3840-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="f3840-152">İfade ağaçları başka bir diline çeviren bir genel amaçlı kitaplığı oluşturmak için gereken tüm iş tam bir tartışma için lütfen okuyun [bu seri](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) Matt Warren tarafından.</span><span class="sxs-lookup"><span data-stu-id="f3840-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="f3840-153">Herhangi bir ifade ağacına bulabileceğiniz kod Çevir konusunda harika ayrıntıya gider.</span><span class="sxs-lookup"><span data-stu-id="f3840-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="f3840-154">I ifade ağaçları true gücünü şimdi gördüğünüz umuyoruz.</span><span class="sxs-lookup"><span data-stu-id="f3840-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="f3840-155">Kod kümesi inceleyin, bu kodu ister ve değiştirilen sürüm yürütme tüm değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="f3840-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="f3840-156">İfade ağaçları değişmez olduğundan, varolan ağaçları bileşenlerinin kullanarak yeni ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3840-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="f3840-157">Bu değiştirilmiş ifade ağaçları oluşturmak için gerekli bellek miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="f3840-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="f3840-158">Sonraki--Özetle</span><span class="sxs-lookup"><span data-stu-id="f3840-158">Next -- Summing up</span></span>](expression-trees-summary.md)
