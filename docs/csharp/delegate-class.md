---
title: System.Delegate ve `delegate` anahtar kelime
description: .NET'te delegeleri destekleyen sınıflar ve bu ların 'temsilci' anahtar kelimesine nasıl eşleneceği hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146287"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="1306c-103">System.Delegate ve `delegate` anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="1306c-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="1306c-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="1306c-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="1306c-105">Bu makalede, .NET'te delegeleri destekleyen sınıfları ve `delegate` bu eşin anahtar kelimeye nasıl eşlenebildiğini kapsar.</span><span class="sxs-lookup"><span data-stu-id="1306c-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="1306c-106">Temsilci türlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="1306c-106">Define delegate types</span></span>

<span data-ttu-id="1306c-107">'Temsilci' anahtar kelimesi ile başlayalım, çünkü öncelikle temsilcilerle çalışırken kullanacağınız şey budur.</span><span class="sxs-lookup"><span data-stu-id="1306c-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="1306c-108">`delegate` Anahtar kelimeyi kullandığınızda derleyicinin oluşturduğu kod, ve <xref:System.Delegate> <xref:System.MulticastDelegate> sınıfların üyelerini çağıran çağrıları yöntemle eşler.</span><span class="sxs-lookup"><span data-stu-id="1306c-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="1306c-109">Yöntem imzasını tanımlamaya benzer sözdizimini kullanarak bir temsilci türü tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="1306c-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="1306c-110">Sadece tanım `delegate` için anahtar kelime ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1306c-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="1306c-111">Liste.Sıralama() yöntemini örneğimiz olarak kullanmaya devam edelim.</span><span class="sxs-lookup"><span data-stu-id="1306c-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="1306c-112">İlk adım, karşılaştırma temsilcisi için bir tür oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="1306c-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="1306c-113">Derleyici, `System.Delegate` kullanılan imzayla eşleşen bir sınıf oluşturur (bu durumda, bir tamsayı döndüren ve iki bağımsız değişkeni olan bir yöntem).</span><span class="sxs-lookup"><span data-stu-id="1306c-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="1306c-114">Bu temsilcinin `Comparison`türü.</span><span class="sxs-lookup"><span data-stu-id="1306c-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="1306c-115">Temsilci `Comparison` türü genel bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="1306c-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="1306c-116">Jenerik hakkında ayrıntılı bilgi için [buraya](programming-guide/generics/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1306c-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="1306c-117">Sözdiziminin bir değişken beyan ediyormuş gibi görünebileceğine, ancak aslında bir *tür*beyan ettiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1306c-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="1306c-118">Sınıflar içinde, doğrudan ad alanları içinde ve hatta genel ad alanında temsilci türlerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1306c-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="1306c-119">Temsilci türlerinin (veya diğer türlerin) doğrudan genel ad alanında beyan olması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="1306c-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="1306c-120">Derleyici ayrıca, bu sınıfın istemcilerinin bir örneğin çağrı listesinden yöntem ekleyip kaldırabilmesi için bu yeni tür için işleyiciler ekleme ve kaldırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1306c-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="1306c-121">Derleyici, eklenen veya kaldırılan yöntemin imzasının yöntemi bildirirken kullanılan imzayla eşleştiğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="1306c-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="1306c-122">Temsilci örneklerini bildir</span><span class="sxs-lookup"><span data-stu-id="1306c-122">Declare instances of delegates</span></span>

<span data-ttu-id="1306c-123">Temsilciyi tanımladıktan sonra, bu tür bir örnek oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1306c-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="1306c-124">C#'daki tüm değişkenler gibi, temsilci örneklerini doğrudan bir ad alanında veya genel ad alanında bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1306c-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="1306c-125">Değişkenin `Comparison<T>`türü, daha önce tanımlanan temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="1306c-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="1306c-126">Değişkenin adı `comparator`.</span><span class="sxs-lookup"><span data-stu-id="1306c-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="1306c-127">Yukarıdaki kod parçacığı bir sınıf içinde bir üye değişken içinde ilan etti.</span><span class="sxs-lookup"><span data-stu-id="1306c-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="1306c-128">Yerel değişkenler veya bağımsız değişkenler olan temsilci değişkenlerini yöntemlere de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1306c-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="1306c-129">Delegeleri çağırma</span><span class="sxs-lookup"><span data-stu-id="1306c-129">Invoke delegates</span></span>

<span data-ttu-id="1306c-130">Bu temsilciyi çağırarak bir temsilcinin çağırma listesinde bulunan yöntemleri çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="1306c-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="1306c-131">Yöntemin `Sort()` içinde, kod nesneleri yerleştirmek için hangi sırayı belirlemek için karşılaştırma yöntemi çağırır:</span><span class="sxs-lookup"><span data-stu-id="1306c-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="1306c-132">Yukarıdaki satırda, kod temsilciye eklenen yöntemi *çağırır.*</span><span class="sxs-lookup"><span data-stu-id="1306c-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="1306c-133">Değişkeni bir yöntem adı olarak ele alıp, normal yöntem çağrı sözdizimini kullanarak çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="1306c-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="1306c-134">Bu kod satırı güvenli olmayan bir varsayım yapar: Temsilciye bir hedefekildiğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1306c-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="1306c-135">Hiçbir hedef eklenmediyse, yukarıdaki satır `NullReferenceException` a'nın atılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1306c-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="1306c-136">Bu sorunu gidermek için kullanılan deyimler basit bir null-check daha karmaşık, ve daha sonra bu serinin ele [alınmıştır.](delegates-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="1306c-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="1306c-137">Çağırma hedeflerini atama, ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="1306c-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="1306c-138">Temsilci türü bu şekilde tanımlanır ve temsilci örnekleri nasıl bildirilir ve çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1306c-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="1306c-139">`List.Sort()` Yöntemi kullanmak isteyen geliştiricilerin, imzası temsilci türü tanımıyla eşleşen bir yöntem tanımlaması ve sıralama yöntemi tarafından kullanılan temsilciye ataması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1306c-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="1306c-140">Bu atama, bu temsilci nesnesinin çağırma listesine yöntemi ekler.</span><span class="sxs-lookup"><span data-stu-id="1306c-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="1306c-141">Dizeleri uzunluklarına göre sıralamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="1306c-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="1306c-142">Karşılaştırma işleviniz aşağıdakiler olabilir:</span><span class="sxs-lookup"><span data-stu-id="1306c-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="1306c-143">Yöntem özel bir yöntem olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="1306c-143">The method is declared as a private method.</span></span> <span data-ttu-id="1306c-144">Sorun değil.</span><span class="sxs-lookup"><span data-stu-id="1306c-144">That's fine.</span></span> <span data-ttu-id="1306c-145">Bu yöntemin ortak arabiriminizin bir parçası olmasını istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1306c-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="1306c-146">Yine de bir temsilciye eklendiğinde karşılaştırma yöntemi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1306c-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="1306c-147">Arama kodu bu yöntemi temsilci nesnesinin hedef listesine iliştirecek ve bu temsilci aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1306c-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="1306c-148">Bu yöntemi yönteme geçirerek `List.Sort()` bu ilişkiyi oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="1306c-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="1306c-149">Yöntem adının parantez olmadan kullanıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1306c-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="1306c-150">Yöntemi bağımsız değişken olarak kullanmak, derleyiciye yöntem başvurularını temsilci çağırma hedefi olarak kullanılabilecek bir başvuruya dönüştürmesini ve bu yöntemi bir çağırma hedefi olarak eklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="1306c-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="1306c-151">Ayrıca, bir tür `Comparison<string>` değişkeni beyan ederek ve bir atama yaparak da açık olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1306c-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="1306c-152">Temsilci hedefi olarak kullanılan yöntemin küçük bir yöntem olduğu kullanımlarda, atamayı gerçekleştirmek için [lambda ifade](./programming-guide/statements-expressions-operators/lambda-expressions.md) sözdizimini kullanmak yaygındır:</span><span class="sxs-lookup"><span data-stu-id="1306c-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="1306c-153">Temsilci hedefleri için lambda ifadeleri kullanarak [daha sonraki](delegates-patterns.md)bir bölümde daha fazla ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="1306c-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="1306c-154">Sıralama() örneği genellikle temsilciye tek bir hedef yöntemi bağlar.</span><span class="sxs-lookup"><span data-stu-id="1306c-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="1306c-155">Ancak, temsilci nesneleri, bir temsilci nesnesine bağlı birden çok hedef yöntemi olan çağrı listelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1306c-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="1306c-156">Temsilci ve Çok Noktaya Yayın sınıfları</span><span class="sxs-lookup"><span data-stu-id="1306c-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="1306c-157">Yukarıda açıklanan dil desteği, genellikle temsilcilerle çalışmak için ihtiyaç duyduğunuz özellikleri ve desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1306c-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="1306c-158">Bu özellikler .NET Core çerçevesinde iki sınıf <xref:System.Delegate> <xref:System.MulticastDelegate>üzerine kurulmuştur: ve .</span><span class="sxs-lookup"><span data-stu-id="1306c-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="1306c-159">Sınıf `System.Delegate` ve onun tek doğrudan `System.MulticastDelegate`alt sınıfı, temsilci oluşturmak, yöntemleri temsilci hedefleri olarak kaydetmek ve temsilci hedefi olarak kaydedilmiş tüm yöntemleri çağırmak için çerçeve desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1306c-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="1306c-160">İlginçtir, `System.Delegate` ve `System.MulticastDelegate` sınıflar kendilerini temsilci türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="1306c-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="1306c-161">Bunlar, tüm belirli temsilci türleri için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="1306c-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="1306c-162">Aynı dil tasarımı işlemi, türeyen `Delegate` bir sınıfı veya `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="1306c-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="1306c-163">C# dil kuralları bunu yasaklıyor.</span><span class="sxs-lookup"><span data-stu-id="1306c-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="1306c-164">Bunun yerine, C# derleyicisi, temsilci `MulticastDelegate` türlerini bildirmek için C# dil anahtar sözcüklerini kullandığınızda türetilen bir sınıfın örneklerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1306c-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="1306c-165">Bu tasarımın kökleri C# ve .NET'in ilk sürümünde dir.</span><span class="sxs-lookup"><span data-stu-id="1306c-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="1306c-166">Tasarım ekibinin amaçlarından biri, temsilcilerini kullanırken dilin tür güvenliğini zorunlu kıldığından emin olmaktı.</span><span class="sxs-lookup"><span data-stu-id="1306c-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="1306c-167">Bu, delegelerin doğru argüman türü ve sayısıyla çağrılmasını sağlamak anlamına geliyordu.</span><span class="sxs-lookup"><span data-stu-id="1306c-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="1306c-168">Ve, herhangi bir dönüş türü doğru derleme zamanda belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1306c-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="1306c-169">Delegeler, jeneriklerden önce yapılan 1.0 .NET sürümünde yer alıyordu.</span><span class="sxs-lookup"><span data-stu-id="1306c-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="1306c-170">Bu tür güvenliğini zorlamanın en iyi yolu, derleyicinin kullanılan yöntem imzasını temsil eden somut temsilci sınıfları oluşturmasıydı.</span><span class="sxs-lookup"><span data-stu-id="1306c-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="1306c-171">Türemiş sınıfları doğrudan oluşturamasanız da, bu sınıflarda tanımlanan yöntemleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1306c-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="1306c-172">Temsilcilerle çalışırken kullanacağınız en yaygın yöntemleri gözden geçirelim.</span><span class="sxs-lookup"><span data-stu-id="1306c-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="1306c-173">Hatırlanması gereken ilk ve en önemli gerçek, çalıştığınız `MulticastDelegate`her temsilcinin.'den türetilmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1306c-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="1306c-174">Çok noktaya yayın temsilcisi, bir temsilci aracılığıyla çağrılırken birden fazla yöntem hedefinin çağrılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1306c-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="1306c-175">Özgün tasarım, yalnızca bir hedef yöntemin eklenebileceği ve çağrılabildiği temsilciler ile birden çok hedef yöntemin eklenebileceği ve çağrılabileceği temsilciler arasında ayrım yapmayı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1306c-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="1306c-176">Bu ayrım pratikte başlangıçta düşünülenden daha az yararlı olduğunu kanıtladı.</span><span class="sxs-lookup"><span data-stu-id="1306c-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="1306c-177">İki farklı sınıf zaten oluşturuldu ve ilk kamuoyuna açıklanmasından bu yana çerçeve içinde olmuştur.</span><span class="sxs-lookup"><span data-stu-id="1306c-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="1306c-178">Temsilcilerle en çok kullanacağınız yöntemler `Invoke()` ve `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="1306c-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="1306c-179">`Invoke()`belirli bir temsilci örneğine eklenen tüm yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="1306c-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="1306c-180">Yukarıda gördüğünüz gibi, genellikle temsilci değişkeninde sözdizimi arama yöntemini kullanarak temsilci çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="1306c-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="1306c-181">[Daha sonra bu seride](delegates-patterns.md)göreceğiniz gibi, bu yöntemlerle doğrudan çalışan desenler vardır.</span><span class="sxs-lookup"><span data-stu-id="1306c-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="1306c-182">Artık dil sözdizimini ve temsilcileri destekleyen sınıfları gördüğünüze göre, ne kadar güçlü bir şekilde yazılan temsilcilerin kullanıldığını, oluşturulduğunu ve çağrıldığını inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="1306c-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="1306c-183">Sonraki</span><span class="sxs-lookup"><span data-stu-id="1306c-183">Next</span></span>](delegates-strongly-typed.md)
