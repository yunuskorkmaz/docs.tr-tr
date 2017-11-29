---
title: "System.Delegate ve 'temsilci' anahtar sözcüğü"
description: ".NET Framework'teki temsilcileri ve nasıl olanlar 'temsilci' anahtar sözcüğü eşleme desteği sınıfları hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 09c7da7c780389d3819cf23a533cc425b43ad5ff
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="9602f-104">System.Delegate ve `delegate` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="9602f-104">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="9602f-105">Önceki</span><span class="sxs-lookup"><span data-stu-id="9602f-105">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="9602f-106">Bu makalede Temsilciler ve nasıl olanlar için eşleme destekleyen sınıfları .NET Framework'teki ele alınacaktır `delegate` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9602f-106">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="9602f-107">Temsilci türleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="9602f-107">Defining Delegate Types</span></span>

<span data-ttu-id="9602f-108">Temsilciler ile çalışırken ne kullanır, öncelikle olduğu için 'temsilci' anahtar sözcüğüyle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="9602f-108">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="9602f-109">Derleyici kullandığınızda oluşturduğu kodu `delegate` anahtar sözcüğü üyeleri çağırma yöntem çağrıları eşleme <xref:System.Delegate> ve <xref:System.MulticastDelegate> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9602f-109">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="9602f-110">Bir yöntem imzası tanımlamak için benzer sözdizimini kullanarak bir temsilci türü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9602f-110">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="9602f-111">Yalnızca Ekle `delegate` tanımına anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9602f-111">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="9602f-112">Şimdi List.Sort() yöntemi bizim örnek olarak kullanmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="9602f-112">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="9602f-113">İlk adım, bir tür için karşılaştırma temsilci oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="9602f-113">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="9602f-114">Derleyici türetilmiş bir sınıf oluşturur `System.Delegate` (Bu durumda, bir tamsayı döndürür ve iki bağımsız olan bir yöntem) kullanılan imzayı eşleşir.</span><span class="sxs-lookup"><span data-stu-id="9602f-114">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="9602f-115">Bu temsilci türü `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="9602f-115">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="9602f-116">`Comparison` Temsilci türüdür genel bir tür.</span><span class="sxs-lookup"><span data-stu-id="9602f-116">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="9602f-117">Genel türler hakkında ayrıntılar için bkz: [burada](generics.md).</span><span class="sxs-lookup"><span data-stu-id="9602f-117">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="9602f-118">Sözdizimi değişken bildirme, ancak gerçekte bildirme gibi sorgulamanıza görünebilir bildirimi bir *türü*.</span><span class="sxs-lookup"><span data-stu-id="9602f-118">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="9602f-119">Sınıfları, ad alanları doğrudan içinde ya da hatta genel ad alanında temsilci türlerinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9602f-119">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="9602f-120">Doğrudan genel ad alanında temsilci türleri (veya diğer türleri) bildirme önerilmez.</span><span class="sxs-lookup"><span data-stu-id="9602f-120">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="9602f-121">Derleyici de oluşturur ekleyin ve böylece istemciler, bu sınıfın ekleyin ve yöntemleri bir örneğinin çağırma listesinden kaldırmak bu yeni tür için işleyiciler kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9602f-121">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="9602f-122">Derleyici eklendiğinde veya kaldırıldığında yöntemi imzası yöntemi bildirirken kullanılan imzayı eşleştiğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="9602f-122">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="9602f-123">Temsilciler örneklerini bildirme</span><span class="sxs-lookup"><span data-stu-id="9602f-123">Declaring instances of delegates</span></span>

<span data-ttu-id="9602f-124">Temsilci tanımladıktan sonra o türünün bir örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9602f-124">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="9602f-125">C# tüm değişkenler gibi bir ad alanındaki doğrudan ya da genel ad alanında temsilci örneklerinin bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9602f-125">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="9602f-126">Değişken türü `Comparison<T>`, daha önce tanımlanan temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="9602f-126">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="9602f-127">Değişken adı `comparator`.</span><span class="sxs-lookup"><span data-stu-id="9602f-127">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="9602f-128">Yukarıdaki kod parçacığında, bir üye değişkenine bir sınıf içinde bildirildi.</span><span class="sxs-lookup"><span data-stu-id="9602f-128">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="9602f-129">Yerel değişkenler ya da bağımsız değişkenleri yöntemleri için temsilci değişkenleri de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9602f-129">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="9602f-130">Çağıran temsilciler</span><span class="sxs-lookup"><span data-stu-id="9602f-130">Invoking Delegates</span></span>

<span data-ttu-id="9602f-131">Bu temsilci çağırarak bir temsilci çağırma listesi yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="9602f-131">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="9602f-132">İçinde `Sort()` yöntemi, kodun hangi sırada yerleştirmek için nesneleri belirlemek için karşılaştırma yöntemi çağıracaktır:</span><span class="sxs-lookup"><span data-stu-id="9602f-132">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="9602f-133">Yukarıdaki kod satırına *çağırır* yöntemi temsilciye bağlı.</span><span class="sxs-lookup"><span data-stu-id="9602f-133">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="9602f-134">Değişken bir yöntem adı kabul eder ve normal yöntemi çağrı sözdizimini kullanarak çağırma.</span><span class="sxs-lookup"><span data-stu-id="9602f-134">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="9602f-135">Bu kod satırı güvenli olmayan bir varsayım yapmaz: hedef temsilciye eklendi garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9602f-135">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="9602f-136">Hiçbir hedef eklediyseniz, yukarıdaki satır neden olacağından bir `NullReferenceException` oluşturulmasına.</span><span class="sxs-lookup"><span data-stu-id="9602f-136">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="9602f-137">Bu sorunu gidermek için kullanılan deyimleri basit bir null denetimi daha karmaşıktır ve daha sonra bu konuda ele alınmıştır [serisi](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="9602f-137">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="9602f-138">Atama, ekleme ve çağırma hedeflerini kaldırma</span><span class="sxs-lookup"><span data-stu-id="9602f-138">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="9602f-139">Bir temsilci türü nasıl tanımlanır ve temsilci örneklerinin nasıl bildirilir ve çağrılan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9602f-139">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="9602f-140">Kullanmak istediğiniz geliştiriciler `List.Sort()` yöntemi ihtiyacınız olan imza temsilci türü tanımı eşleşen bir yöntemi tanımlamak ve sıralama yöntemi tarafından kullanılan temsilci atamak.</span><span class="sxs-lookup"><span data-stu-id="9602f-140">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="9602f-141">Bu atama yöntemi temsilci nesnenin çağırma listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="9602f-141">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="9602f-142">Dizeleri listesini kendi uzunluğa göre sıralamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="9602f-142">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="9602f-143">Karşılaştırma işlevinizi şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="9602f-143">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right)
{
    return left.Length.CompareTo(right.Length);
}
```

<span data-ttu-id="9602f-144">Yöntemi, özel bir yöntem olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="9602f-144">The method is declared as a private method.</span></span> <span data-ttu-id="9602f-145">Bu sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="9602f-145">That's fine.</span></span> <span data-ttu-id="9602f-146">Ortak arabirimi bir parçası olması için bu yöntemi istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9602f-146">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="9602f-147">Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9602f-147">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="9602f-148">Çağrıyı yapan kod temsilci nesnesini hedef listeye eklenen bu yöntem sahip olur ve bu temsilciyi erişebilir.</span><span class="sxs-lookup"><span data-stu-id="9602f-148">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="9602f-149">Bu yönteme geçirerek bu ilişki oluşturmak `List.Sort()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="9602f-149">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="9602f-150">Yöntem adı, parantez olmadan kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9602f-150">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="9602f-151">Yöntemin bağımsız değişken olarak kullanarak, bu yöntem çağırma hedefi olarak eklemek ve temsilci çağırma hedef olarak kullanılabilir bir başvuru yöntemi başvuru dönüştürmek için derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="9602f-151">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="9602f-152">Ayrıca türünde bir değişken bildirerek açık atanmış olmanız ' karşılaştırma<string>' ve bir ataması yapıyor:</span><span class="sxs-lookup"><span data-stu-id="9602f-152">You could also have been explicit by declaring a variable of type 'Comparison<string>\` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="9602f-153">Bir temsilci hedef küçük bir yöntem olarak kullanılmakta olan yöntemin olduğu kullanmak için yaygın kullanımları içinde [Lambda ifadesi](lambda-expressions.md) ataması gerçekleştirmek için söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="9602f-153">In uses where the method being used as a delegate target is a small method, it's common to use [Lambda Expression](lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="9602f-154">Lambda ifadeleri için temsilci hedefleri kullanarak kapsanan daha içinde bir [daha sonra bölüm](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="9602f-154">Using Lambda Expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="9602f-155">Sort() örnek, bir tek hedef yöntemi temsilciye genellikle iliştirir.</span><span class="sxs-lookup"><span data-stu-id="9602f-155">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="9602f-156">Ancak, temsilci nesneleri bir temsilci nesnesine bağlı birden çok hedef yöntemleri çağırma listelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="9602f-156">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="9602f-157">Temsilci ve MulticastDelegate sınıfları</span><span class="sxs-lookup"><span data-stu-id="9602f-157">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="9602f-158">Yukarıda açıklanan dil desteği, özellikleri ve genellikle temsilciler ile çalışması gerekir desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="9602f-158">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="9602f-159">Bu özellikler iki sınıf .NET Core Framework üzerine kurulu: <xref:System.Delegate> ve <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="9602f-159">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="9602f-160">`System.Delegate` Sınıfı ve onun tek doğrudan alt sınıfını `System.MulticastDelegate`, temsilci oluşturmak, yöntemleri temsilci hedefleri olarak kaydetme ve temsilci hedef olarak kayıtlı olan tüm yöntemleri çağırma framework desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="9602f-160">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="9602f-161">İlginçtir ki, `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerini olmayan temsilci türleri.</span><span class="sxs-lookup"><span data-stu-id="9602f-161">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="9602f-162">Bunlar, tüm özel temsilci türleri için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="9602f-162">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="9602f-163">İşlem zorunlu bir sınıfı bildiremezsiniz aynı dil tasarımında, türetilen olduğunu `Delegate` veya `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="9602f-163">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="9602f-164">C# dil kurallarına yasaklayabilmek.</span><span class="sxs-lookup"><span data-stu-id="9602f-164">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="9602f-165">Bunun yerine, C# derleyici türetilmiş bir sınıf örneklerini oluşturur `MulticastDelegate` temsilci türleri bildirmek için C# dil anahtar sözcüğünü kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="9602f-165">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="9602f-166">Bu tasarım, kökleri ve C# .NET ilk sürümünde sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9602f-166">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="9602f-167">Dil temsilciler kullanırken tür güvenliği uygulanmasını sağlamak için bir hedef Tasarım ekibi için oluştu.</span><span class="sxs-lookup"><span data-stu-id="9602f-167">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="9602f-168">Temsilciler sağ türü ve bağımsız değişken sayısı ile çağrıldı emin olma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9602f-168">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="9602f-169">Derleme zamanı ve herhangi bir dönüş türü en doğru belirtildi.</span><span class="sxs-lookup"><span data-stu-id="9602f-169">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="9602f-170">Temsilciler önce genel türler edildi 1.0 .NET sürüm parçası olan.</span><span class="sxs-lookup"><span data-stu-id="9602f-170">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="9602f-171">Bu tür güvenliği zorlamak için en iyi yolu derleyici somut temsilci kullanılan yöntem imzası temsil sınıfları oluşturmak oluştu.</span><span class="sxs-lookup"><span data-stu-id="9602f-171">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="9602f-172">Türetilen sınıflar doğrudan oluşturamaz olsa da, bu sınıflara tanımlanan yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="9602f-172">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="9602f-173">Temsilciler ile çalışırken kullanacağınız en yaygın yöntemleri aracılığıyla edelim.</span><span class="sxs-lookup"><span data-stu-id="9602f-173">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="9602f-174">Anımsaması ilk ve en önemli ile çalışırsınız her temsilci türetilmiş gerçeğidir `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="9602f-174">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="9602f-175">Çok noktaya yayın temsilci bir temsilci çağrılırken, birden fazla yöntem hedef çağrılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9602f-175">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="9602f-176">Özgün Tasarım olarak kabul burada yalnızca bir hedef yönteme bağlı çağrılır ve yüklenemedi Temsilciler ve burada birden çok hedef yöntemi bağlı çağrılır ve yüklenemedi temsilciler arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="9602f-176">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="9602f-177">Bu ayrım başlangıçta zorlayıcı daha uygulamada daha az kullanışlı olması için oluyor uygulamasına yol açıyordu.</span><span class="sxs-lookup"><span data-stu-id="9602f-177">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="9602f-178">Farklı iki sınıf zaten oluşturulmuş ve framework ilk sürülmeden itibaren kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="9602f-178">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="9602f-179">En temsilciler ile kullanacağınız yöntemler `Invoke()` ve `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="9602f-179">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="9602f-180">`Invoke()`belirli temsilci örneğine bağlı tüm yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="9602f-180">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="9602f-181">Yukarıda gördüğünüz gibi genellikle temsilcileri temsilci değişkeni yöntemi çağrı sözdizimini kullanarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="9602f-181">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="9602f-182">Gördüğünüz gibi [bu serideki sonraki](delegates-patterns.md), doğrudan bu yöntemlerle iş desenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="9602f-182">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="9602f-183">Dili sözdizimi ve temsilciler destekleyen sınıfları gördüğünüze göre nasıl kesin türü belirtilmiş temsilciler inceleyelim, oluşturulan çağrılır ve kullanıldığını.</span><span class="sxs-lookup"><span data-stu-id="9602f-183">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="9602f-184">Sonraki</span><span class="sxs-lookup"><span data-stu-id="9602f-184">Next</span></span>](delegates-strongly-typed.md)
