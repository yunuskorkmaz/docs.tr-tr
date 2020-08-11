---
title: System. Delegate ve `delegate` anahtar sözcüğü
description: Temsilcileri destekleyen ve bunların ' Delegate ' anahtar sözcüğüyle nasıl eşlendikleri .NET sınıfları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 9df8ad68f6bfa62863ee047875b6419fc81ad779
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062476"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="a8ce8-103">System. Delegate ve `delegate` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a8ce8-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="a8ce8-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="a8ce8-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="a8ce8-105">Bu makalede temsilcileri destekleyen .NET sınıfları ve bunların anahtar kelimesiyle nasıl eşlendikleri ele alınmaktadır `delegate` .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="a8ce8-106">Temsilci türlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="a8ce8-106">Define delegate types</span></span>

<span data-ttu-id="a8ce8-107">' Delegate ' anahtar sözcüğüyle başlayalım, çünkü bu aslında temsilcilerle çalışırken kullanacağınız şeydir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="a8ce8-108">Anahtar sözcüğünü kullandığınızda derleyicinin ürettiği kod, `delegate` ve sınıflarının üyelerini çağıran yöntem çağrılarına eşlenir <xref:System.Delegate> <xref:System.MulticastDelegate> .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="a8ce8-109">Yöntem imzasını tanımlamaya benzer bir sözdizimi kullanarak bir temsilci türü tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="a8ce8-110">`delegate`Anahtar sözcüğünü yalnızca tanımına eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="a8ce8-111">Bizim örneğimizde List. Sort () yöntemini kullanmaya devam edelim.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="a8ce8-112">İlk adım, karşılaştırma temsilcisi için bir tür oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="a8ce8-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="a8ce8-113">Derleyici, kullanılan imzayla eşleşen bir sınıf oluşturur `System.Delegate` (Bu durumda, bir tamsayı döndüren ve iki bağımsız değişkeni olan bir yöntem).</span><span class="sxs-lookup"><span data-stu-id="a8ce8-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="a8ce8-114">Bu temsilcinin türü `Comparison` .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="a8ce8-115">`Comparison`Temsilci türü genel bir tür.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="a8ce8-116">Genel türler hakkında daha fazla bilgi için [buraya](programming-guide/generics/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="a8ce8-117">Sözdiziminin bir değişken bildirmiş gibi görünebileceğini ancak gerçekten bir *tür*bildirdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="a8ce8-118">Sınıf içinde doğrudan ad alanları içinde veya genel ad alanında temsilci türleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="a8ce8-119">Temsilci türlerinin (veya diğer türlerin) doğrudan genel ad alanında bildirilmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="a8ce8-120">Derleyici Ayrıca bu yeni tür için ekleme ve kaldırma işleyicileri üretir. bu sayede, bu sınıfın istemcileri bir örneğin çağrı listesinden Yöntem ekleyebilir ve kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="a8ce8-121">Derleyici, eklenen veya kaldırılan yöntemin imzasının, yöntemi bildirirken kullanılan imza ile eşleştiğinden zorlanır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="a8ce8-122">Temsilcilerin örneklerini bildirme</span><span class="sxs-lookup"><span data-stu-id="a8ce8-122">Declare instances of delegates</span></span>

<span data-ttu-id="a8ce8-123">Temsilciyi tanımladıktan sonra, bu türün bir örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="a8ce8-124">C# ' deki tüm değişkenler gibi, temsilci örneklerini doğrudan bir ad alanında veya genel ad alanında bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="a8ce8-125">Değişkenin türü `Comparison<T>` , daha önce tanımlanan temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="a8ce8-126">Değişkenin adı `comparator` .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="a8ce8-127">Yukarıdaki kod parçacığı, bir sınıf içinde bir üye değişkeni bildirdi.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="a8ce8-128">Yerel değişkenler veya yöntemler için bağımsız değişkenler olan temsilci değişkenlerini de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="a8ce8-129">Temsilcileri çağır</span><span class="sxs-lookup"><span data-stu-id="a8ce8-129">Invoke delegates</span></span>

<span data-ttu-id="a8ce8-130">Bu temsilciyi çağırarak bir temsilcinin çağırma listesindeki yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="a8ce8-131">Yöntemi içinde `Sort()` , kod, nesnelerin yerleştirileceği sırayı belirleyen karşılaştırma yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="a8ce8-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="a8ce8-132">Yukarıdaki satırda kod, temsilciye iliştirilmiş yöntemi *çağırır* .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="a8ce8-133">Değişkeni bir yöntem adı olarak değerlendirir ve normal Yöntem çağrısı söz dizimini kullanarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="a8ce8-134">Bu kod satırı güvenli olmayan bir varsayımına neden olur: temsilciye bir hedefin eklendiğinden emin olmaz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="a8ce8-135">Hiçbir hedef iliştirilmişse yukarıdaki satır bir oluşturulmasına neden olur `NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="a8ce8-136">Bu sorunu gidermek için kullanılan ıoms, basit bir null denetiminden daha karmaşıktır ve bu [serinin](delegates-patterns.md)ilerleyen kısımlarında ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="a8ce8-137">Çağırma hedeflerini atama, ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="a8ce8-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="a8ce8-138">Temsilci türünün tanımlanması ve temsilci örneklerinin nasıl bildirildiği ve çağrıldığı.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="a8ce8-139">Yöntemini kullanmak isteyen geliştiriciler, `List.Sort()` imzası temsilci türü tanımıyla eşleşen bir yöntem tanımlamak ve bunu sıralama yöntemi tarafından kullanılan temsilciye atamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="a8ce8-140">Bu atama, yöntemi bu temsilci nesnesinin çağırma listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="a8ce8-141">Dizelerin bir listesini uzunluğuna göre sıralamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="a8ce8-142">Karşılaştırma işleviniz aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="a8ce8-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="a8ce8-143">Yöntemi özel bir yöntem olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-143">The method is declared as a private method.</span></span> <span data-ttu-id="a8ce8-144">Bu çok güzel.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-144">That's fine.</span></span> <span data-ttu-id="a8ce8-145">Bu yöntemin ortak arayüzün bir parçası olmasını istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="a8ce8-146">Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak yine de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="a8ce8-147">Çağıran kod bu yöntemi temsilci nesnesinin hedef listesine iliştirilir ve bu temsilci aracılığıyla erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="a8ce8-148">Yöntemi yöntemine geçirerek bu ilişkiyi oluşturursunuz `List.Sort()` :</span><span class="sxs-lookup"><span data-stu-id="a8ce8-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="a8ce8-149">Yöntem adının parantez olmadan kullanıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="a8ce8-150">Yöntemin bağımsız değişken olarak kullanılması, derleyicinin Yöntem başvurusunu temsilci çağırma hedefi olarak kullanılabilecek bir başvuruya dönüştürmesini ve bu yöntemi bir çağırma hedefi olarak iliştirmesine söyler.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="a8ce8-151">Ayrıca, türünde bir değişken bildirerek ve ödev yaparak da açık olabilirsiniz `Comparison<string>` :</span><span class="sxs-lookup"><span data-stu-id="a8ce8-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="a8ce8-152">' De, bir temsilci hedefi olarak kullanılan yöntemin küçük bir yöntem olduğu durumlarda, atamayı gerçekleştirmek için [lambda ifadesi](language-reference/operators/lambda-expressions.md) sözdizimini kullanmak yaygındır:</span><span class="sxs-lookup"><span data-stu-id="a8ce8-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](language-reference/operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="a8ce8-153">Temsilci hedefleri için lambda ifadelerinin kullanılması, [sonraki bölümde](delegates-patterns.md)daha fazla ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="a8ce8-154">Sort () örneği genellikle temsilciye tek bir hedef yöntemi iliştirir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="a8ce8-155">Ancak, temsilci nesneleri, temsilci nesnesine eklenmiş birden çok Target yöntemi olan çağrı listelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="a8ce8-156">Temsilci ve MulticastDelegate sınıfları</span><span class="sxs-lookup"><span data-stu-id="a8ce8-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="a8ce8-157">Yukarıda açıklanan dil desteği, genellikle temsilcilerle çalışmanız gereken özellikleri ve desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="a8ce8-158">Bu özellikler .NET Core Framework 'te iki sınıf üzerine kurulmuştur: <xref:System.Delegate> ve <xref:System.MulticastDelegate> .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="a8ce8-159">`System.Delegate`Sınıfı ve tek bir doğrudan alt sınıfı olan, `System.MulticastDelegate` Temsilciler oluşturmak, yöntemleri temsilci hedefleri olarak kaydetmek ve temsilci hedefi olarak kaydedilen tüm yöntemleri çağırmak için çerçeve desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="a8ce8-160">Intergelme, `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerine temsilci türleri değil.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="a8ce8-161">Bunlar, tüm özel temsilci türleri için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="a8ce8-162">Aynı dil tasarım süreci, veya ' den türetilen bir sınıfı bildiremezsiniz `Delegate` `MulticastDelegate` .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="a8ce8-163">C# dil kuralları bunu yasaklar.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="a8ce8-164">Bunun yerine, C# derleyicisi `MulticastDelegate` temsilci türlerini bildirmek Için C# Language anahtar sözcüğünü kullandığınızda öğesinden türetilmiş bir sınıfın örneklerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="a8ce8-165">Bu tasarımın ilk C# ve .NET sürümünde köklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="a8ce8-166">Tasarım ekibi için bir hedef, temsilci kullanılırken dilin tür güvenliğini zorlamasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="a8ce8-167">Bu, temsilcilerin doğru tür ve bağımsız değişken sayısıyla çağrılmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="a8ce8-168">Ve herhangi bir dönüş türü, derleme zamanında doğru şekilde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="a8ce8-169">Temsilciler, genel türler 'den önce olan 1,0 .NET sürümünün bir parçası idi.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="a8ce8-170">Bu tür güvenliğini zorlamak için en iyi yol, derleyicinin kullanılan yöntem imzasını temsil eden somut temsilci sınıfları oluşturmasına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="a8ce8-171">Türetilmiş sınıfları doğrudan oluşturamasanız bile, bu sınıflarda tanımlanan yöntemleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="a8ce8-172">Temsilcilerle çalışırken kullanacağınız en yaygın yöntemlerle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="a8ce8-173">Anımsanması gereken ilk, en önemli olgu, ile birlikte çalıştığınız her temsilcinin türetiliyor `MulticastDelegate` .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="a8ce8-174">Çok noktaya yayın temsilcisi, bir temsilci aracılığıyla çağrıldığında birden fazla yöntem hedefinin çağrılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="a8ce8-175">Özgün tasarım, yalnızca bir hedef yöntemin iliştirilebileceği ve çağrılabildiği temsilciler arasında ayrım yapmayı ve birden çok hedef metodun iliştirilebileceği ve çağrılabileceği temsilcileri arasında ayrım yapmayı düşünüder.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="a8ce8-176">Bu ayrım, ilk düşünmeden uygulamada daha az yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="a8ce8-177">İki farklı sınıf zaten oluşturuldu ve ilk genel sürümünden bu yana çerçevede vardı.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="a8ce8-178">Temsilcilerle en çok kullanacağınız Yöntemler `Invoke()` ve ' dir `BeginInvoke()`  /  `EndInvoke()` .</span><span class="sxs-lookup"><span data-stu-id="a8ce8-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="a8ce8-179">`Invoke()`, belirli bir temsilci örneğine eklenmiş olan tüm yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="a8ce8-180">Yukarıda gördüğünüz gibi genellikle temsilci değişkeninde Yöntem çağrısı söz dizimini kullanarak temsilciler çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="a8ce8-181">[Bu serinin ilerleyen kısımlarında](delegates-patterns.md)göreceğiniz gibi, bu yöntemlerle doğrudan çalışan desenler vardır.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="a8ce8-182">Artık dil sözdizimini ve temsilcileri destekleyen sınıfları gördüğünüze göre, türü kesin belirlenmiş temsilcilerin ne kullanıldığını, oluşturulduğunu ve çağrılmasını incelim.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="a8ce8-183">Sonraki</span><span class="sxs-lookup"><span data-stu-id="a8ce8-183">Next</span></span>](delegates-strongly-typed.md)
