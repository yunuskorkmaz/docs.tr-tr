---
title: System.Delegate ve `delegate` anahtar sözcüğü
description: .NET Framework'teki temsilcileri ve bu 'temsilci' anahtar sözcüğü nasıl eşleştiği destekleyen sınıfları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 4cf2b113fc9e2c6621f648af7ecb272a42b1f056
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465782"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="00e75-103">System.Delegate ve `delegate` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="00e75-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="00e75-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="00e75-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="00e75-105">Bu makalede, temsilciler ve bu'nasıl eşleştiğini destekleyen sınıfları .NET Framework'teki kapsar `delegate` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="00e75-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="00e75-106">Temsilci türleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="00e75-106">Defining Delegate Types</span></span>

<span data-ttu-id="00e75-107">Temsilciler ile çalışırken kullandığınız, öncelikle olduğu için 'temsilci' anahtar sözcüğü ile başlayalım.</span><span class="sxs-lookup"><span data-stu-id="00e75-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="00e75-108">Kullandığınızda, derleyici oluşturan kod `delegate` anahtar sözcüğü, üyelerini çağırmak için yöntem çağrıları eşleme <xref:System.Delegate> ve <xref:System.MulticastDelegate> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="00e75-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="00e75-109">Bir yöntem imzasını tanımlayan benzer söz dizimini kullanarak bir temsilci türü tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="00e75-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="00e75-110">Yalnızca eklediğiniz `delegate` tanımına anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="00e75-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="00e75-111">Bizim örnek olarak List.Sort() yöntemi kullanmak üzere devam edelim.</span><span class="sxs-lookup"><span data-stu-id="00e75-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="00e75-112">İlk adım, bir tür karşılaştırma temsilcisi oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="00e75-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="00e75-113">Derleyici, türetilen bir sınıf oluşturur `System.Delegate` eşleştiren (Bu durumda bir tamsayı döndürür ve iki bağımsız değişkeni olan bir yöntem) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00e75-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="00e75-114">Bu temsilci türü `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="00e75-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="00e75-115">`Comparison` Temsilci türü olan genel bir tür.</span><span class="sxs-lookup"><span data-stu-id="00e75-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="00e75-116">Genel türler hakkında ayrıntılar için bkz. [burada](generics.md).</span><span class="sxs-lookup"><span data-stu-id="00e75-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="00e75-117">Sözdizimi, bir değişken bildiriyor, ancak gerçekte bildirme gibi sorgulamanıza görünebilir bildirimi bir *türü*.</span><span class="sxs-lookup"><span data-stu-id="00e75-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="00e75-118">Temsilci türleri sınıflar, ad alanları doğrudan içinde veya hatta genel ad içinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e75-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="00e75-119">Doğrudan genel ad alanında temsilci türleri (veya diğer türleri) bildirme önerilmez.</span><span class="sxs-lookup"><span data-stu-id="00e75-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="00e75-120">Derleyici ayrıca oluşturur ekleyin ve böylece istemciler bu sınıfın ekleyebilir ve yöntemleri bir örneğin çağırma listesinden kaldırmak için bu yeni türü işleyicilerini kaldırmak.</span><span class="sxs-lookup"><span data-stu-id="00e75-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="00e75-121">Derleyici, eklendiğinde veya kaldırıldığında metodun imzası yöntem bildirirken kullanılan imzayla eşleşen zorlar.</span><span class="sxs-lookup"><span data-stu-id="00e75-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="00e75-122">Temsilci örneklerini bildirme</span><span class="sxs-lookup"><span data-stu-id="00e75-122">Declaring instances of delegates</span></span>

<span data-ttu-id="00e75-123">Temsilci tanımladıktan sonra bu türün bir örneği oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e75-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="00e75-124">Tüm değişkenler gibi C#, doğrudan bir ad alanında ya da genel ad alanında temsilci örneklerini bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e75-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="00e75-125">Değişken türü `Comparison<T>`, daha önce tanımlanan temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="00e75-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="00e75-126">Değişken adı `comparator`.</span><span class="sxs-lookup"><span data-stu-id="00e75-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="00e75-127">Yukarıdaki Bu kod parçacığında, bir sınıf içinde bir üye değişkeni bildirildi.</span><span class="sxs-lookup"><span data-stu-id="00e75-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="00e75-128">Ayrıca, yerel değişkenler veya yöntemlerinin bağımsız değişkenleri temsilci değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e75-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="00e75-129">Çağrılıyor temsilciler</span><span class="sxs-lookup"><span data-stu-id="00e75-129">Invoking Delegates</span></span>

<span data-ttu-id="00e75-130">Bu temsilciyi çağırarak bir temsilci çağırma listesinde yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="00e75-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="00e75-131">İçinde `Sort()` yöntemi, kod nesneleri yerleştirmek için sırasını belirlemek için karşılaştırma metodu çağıracaktır:</span><span class="sxs-lookup"><span data-stu-id="00e75-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="00e75-132">Yukarıdaki kod satırında *çağırır* yöntem temsilciye bağlı.</span><span class="sxs-lookup"><span data-stu-id="00e75-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="00e75-133">Değişkeni bir yöntem adı kabul et ve normal yöntem çağrı sözdizimini kullanarak çağırma.</span><span class="sxs-lookup"><span data-stu-id="00e75-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="00e75-134">Bu kod satırı, güvenli olmayan bir varsayım yapmaz: Bir hedef temsilciye eklendiğini garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="00e75-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="00e75-135">Hiçbir hedef bağlı değilse, yukarıdaki satırı neden bir `NullReferenceException` oluşturulması için.</span><span class="sxs-lookup"><span data-stu-id="00e75-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="00e75-136">Bu sorunu gidermek için kullanılan deyimleri basit bir null denetimi daha karmaşıktır ve daha sonra bu konuda ele alınmaktadır [serisi](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="00e75-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="00e75-137">Atama, ekleme ve kaldırma çağırma hedefleri</span><span class="sxs-lookup"><span data-stu-id="00e75-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="00e75-138">Bir temsilci türü nasıl tanımlandığını ve temsilci örneklerini nasıl bildirildi ve çağrılan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="00e75-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="00e75-139">Kullanmak istediğiniz geliştiriciler `List.Sort()` imzası olan, temsilci türü tanımı eşleşen bir yöntemi tanımlamak ve sıralama yöntemi tarafından kullanılan temsilci atamak yöntem gerekir.</span><span class="sxs-lookup"><span data-stu-id="00e75-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="00e75-140">Bu atama yöntemi, temsilci nesnesini çağırma listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="00e75-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="00e75-141">Bir dize listesi kendi uzunluğa göre sıralamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="00e75-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="00e75-142">Karşılaştırma işlevinizi aşağıdakiler olabilir:</span><span class="sxs-lookup"><span data-stu-id="00e75-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="00e75-143">Yöntemi, özel bir yöntem bildirilir.</span><span class="sxs-lookup"><span data-stu-id="00e75-143">The method is declared as a private method.</span></span> <span data-ttu-id="00e75-144">İyi olur.</span><span class="sxs-lookup"><span data-stu-id="00e75-144">That's fine.</span></span> <span data-ttu-id="00e75-145">Bu yöntem, genel arabiriminin bir parçası olmasını istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e75-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="00e75-146">Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00e75-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="00e75-147">Çağıran kod bu yöntem hedef temsilci nesne listesine bağlı olacaktır ve bu temsilci erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e75-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="00e75-148">Bu yönteme geçirerek bu ilişki oluşturma `List.Sort()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="00e75-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="00e75-149">Yöntem adı, parantez olmadan kullanıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="00e75-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="00e75-150">Bağımsız değişken olarak yöntemi kullanarak, bir temsilci çağırma hedefi olarak kullanılabilir ve bu yöntem bir çağırma hedefi olarak ekleme başvuru yöntemi başvuru dönüştürmek için derleyiciye bildirir.</span><span class="sxs-lookup"><span data-stu-id="00e75-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="00e75-151">Ayrıca türünün bir değişkeni bildirerek açık atanmış `Comparison<string>` ve atama:</span><span class="sxs-lookup"><span data-stu-id="00e75-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="00e75-152">Small yöntemi temsilci hedefi olarak kullanılan yöntemin olduğu kullanmak yaygın kullanır [lambda ifadesi](./programming-guide/statements-expressions-operators/lambda-expressions.md) ataması gerçekleştirmek için söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="00e75-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="00e75-153">Lambda ifadeleri için temsilci hedefleri kullanarak kapsanan daha bir [daha sonra bölüm](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="00e75-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="00e75-154">Sort() örnek bir tek hedef yöntem temsilciye genellikle ekler.</span><span class="sxs-lookup"><span data-stu-id="00e75-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="00e75-155">Ancak, temsilci nesneleri birden çok hedef yöntem bir temsilci nesnesine ekli olan çağırma listelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="00e75-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="00e75-156">Temsilci ve MulticastDelegate sınıfları</span><span class="sxs-lookup"><span data-stu-id="00e75-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="00e75-157">Yukarıda açıklanan dil desteği, destek temsilcileri ile çalışmak için genellikle gerekir ve özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="00e75-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="00e75-158">Bu özelliklerin .NET Core Framework iki sınıf temel alır: <xref:System.Delegate> ve <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="00e75-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="00e75-159">`System.Delegate` Sınıfı ve onun tek doğrudan alt sınıfını `System.MulticastDelegate`, temsilciler oluşturma yöntemleri temsilci hedefler olarak kaydetme ve temsilci hedef olarak kayıtlı olan tüm yöntemlerini çağırmaktan framework desteği sağlayın.</span><span class="sxs-lookup"><span data-stu-id="00e75-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="00e75-160">İlginçtir ki, `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerini olmayan temsilci türleri.</span><span class="sxs-lookup"><span data-stu-id="00e75-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="00e75-161">Bunlar, tüm özel temsilci türleri için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="00e75-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="00e75-162">Aynı dil tasarım işlemi uygulanan bir sınıfı bildiremez öğesinden türetilen `Delegate` veya `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="00e75-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="00e75-163">C# Dil kuralları yasaklar.</span><span class="sxs-lookup"><span data-stu-id="00e75-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="00e75-164">Bunun yerine, C# derleyici türetilmiş bir sınıfın örneklerini oluşturur `MulticastDelegate` kullandığınızda C# temsilci türleri bildirmek için dil anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="00e75-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="00e75-165">Bu tasarım, ilk sürümünde, kökleri sahip C# ve .NET.</span><span class="sxs-lookup"><span data-stu-id="00e75-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="00e75-166">Temsilcileri kullanarak zaman dil tür güvenliği zorunlu emin olmak için Tasarım ekibi için bir hedef oluştu.</span><span class="sxs-lookup"><span data-stu-id="00e75-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="00e75-167">Bu temsilciler doğru tür ve sayıda bağımsız değişken ile çağrılan sağlama geliyordu.</span><span class="sxs-lookup"><span data-stu-id="00e75-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="00e75-168">Derleme zamanı ve herhangi bir dönüş türü, doğru şekilde belirtildi.</span><span class="sxs-lookup"><span data-stu-id="00e75-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="00e75-169">Temsilciler genel türler önce olan 1.0 .NET sürümünün bir parçası olan.</span><span class="sxs-lookup"><span data-stu-id="00e75-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="00e75-170">En iyi yolu, bu tür güvenliği zorlamak için kullanılan yöntem imzası temsil sınıflar somut temsilci oluşturmak derleyicinin için oluştu.</span><span class="sxs-lookup"><span data-stu-id="00e75-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="00e75-171">Türetilmiş sınıflar doğrudan oluşturamazsınız olsa da, bu sınıflarında tanımlanan yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="00e75-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="00e75-172">Temsilciler ile çalışırken kullanacağınız en yaygın yöntemleri aracılığıyla Bahsedelim.</span><span class="sxs-lookup"><span data-stu-id="00e75-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="00e75-173">Anımsanması ilk ve en önemli iş her temsilci türetilir gerçeğidir `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="00e75-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="00e75-174">Çok noktaya yayın temsilci, bir temsilci çağrılırken birden fazla yöntem hedef çağrılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="00e75-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="00e75-175">Yalnızca bir hedef yöntemi burada bağlı ve çağrılan Temsilciler ve birden çok hedef yöntem nereye eklenmiş ve çağrılan temsilcileri arasında bir ayrım yapma özgün tasarımda dikkate.</span><span class="sxs-lookup"><span data-stu-id="00e75-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="00e75-176">İlk olarak düşünülebilir daha uygulamada daha az kullanışlı olması için Bu ayrım kanıtladılar.</span><span class="sxs-lookup"><span data-stu-id="00e75-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="00e75-177">Farklı iki sınıf zaten oluşturulduğunu ve framework ilk genel sürümünden sonra olmuştur.</span><span class="sxs-lookup"><span data-stu-id="00e75-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="00e75-178">En iyi temsilcilerinden kullanacağınız yöntemler `Invoke()` ve `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="00e75-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="00e75-179">`Invoke()` belirli bir temsilci örneğine eklenmiş olan tüm yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="00e75-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="00e75-180">Yukarıda anlatıldığı gibi genellikle temsilcileri yöntemi çağrı sözdizimini kullanarak temsilci değişkeni çağırır.</span><span class="sxs-lookup"><span data-stu-id="00e75-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="00e75-181">Gördüğünüz gibi [bu serideki sonraki](delegates-patterns.md), doğrudan bu yöntemlerle iş desenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="00e75-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="00e75-182">Dilinin sözdizimi ve temsilcileri destekleyen sınıfları gördüğünüze göre şimdi nasıl kesin tür belirtilmiş temsilciler inceleyin, oluşturulan çağrılır ve kullanıldığını.</span><span class="sxs-lookup"><span data-stu-id="00e75-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="00e75-183">Next</span><span class="sxs-lookup"><span data-stu-id="00e75-183">Next</span></span>](delegates-strongly-typed.md)
