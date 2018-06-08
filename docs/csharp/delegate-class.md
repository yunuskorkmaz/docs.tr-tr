---
title: System.Delegate ve `delegate` anahtar sözcüğü
description: .NET Framework'teki temsilcileri ve nasıl olanlar 'temsilci' anahtar sözcüğü eşleme desteği sınıfları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 39dca1053f87a5059bdc60f8b722091ba991cbd5
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827306"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="1faff-103">System.Delegate ve `delegate` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="1faff-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="1faff-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="1faff-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="1faff-105">Bu makalede Temsilciler ve nasıl olanlar için eşleme destekleyen sınıfları .NET Framework'teki ele alınacaktır `delegate` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1faff-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="1faff-106">Temsilci türleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="1faff-106">Defining Delegate Types</span></span>

<span data-ttu-id="1faff-107">Temsilciler ile çalışırken ne kullanır, öncelikle olduğu için 'temsilci' anahtar sözcüğüyle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1faff-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="1faff-108">Derleyici kullandığınızda oluşturduğu kodu `delegate` anahtar sözcüğü üyeleri çağırma yöntem çağrıları eşleme <xref:System.Delegate> ve <xref:System.MulticastDelegate> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1faff-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="1faff-109">Bir yöntem imzası tanımlamak için benzer sözdizimini kullanarak bir temsilci türü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1faff-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="1faff-110">Yalnızca Ekle `delegate` tanımına anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1faff-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="1faff-111">Şimdi List.Sort() yöntemi bizim örnek olarak kullanmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="1faff-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="1faff-112">İlk adım, bir tür için karşılaştırma temsilci oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="1faff-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="1faff-113">Derleyici türetilmiş bir sınıf oluşturur `System.Delegate` (Bu durumda, bir tamsayı döndürür ve iki bağımsız olan bir yöntem) kullanılan imzayı eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1faff-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="1faff-114">Bu temsilci türü `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="1faff-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="1faff-115">`Comparison` Temsilci türüdür genel bir tür.</span><span class="sxs-lookup"><span data-stu-id="1faff-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="1faff-116">Genel türler hakkında ayrıntılar için bkz: [burada](generics.md).</span><span class="sxs-lookup"><span data-stu-id="1faff-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="1faff-117">Sözdizimi değişken bildirme, ancak gerçekte bildirme gibi sorgulamanıza görünebilir bildirimi bir *türü*.</span><span class="sxs-lookup"><span data-stu-id="1faff-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="1faff-118">Sınıfları, ad alanları doğrudan içinde ya da hatta genel ad alanında temsilci türlerinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1faff-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="1faff-119">Doğrudan genel ad alanında temsilci türleri (veya diğer türleri) bildirme önerilmez.</span><span class="sxs-lookup"><span data-stu-id="1faff-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="1faff-120">Derleyici de oluşturur ekleyin ve böylece istemciler, bu sınıfın ekleyin ve yöntemleri bir örneğinin çağırma listesinden kaldırmak bu yeni tür için işleyiciler kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1faff-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="1faff-121">Derleyici eklendiğinde veya kaldırıldığında yöntemi imzası yöntemi bildirirken kullanılan imzayı eşleştiğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="1faff-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="1faff-122">Temsilciler örneklerini bildirme</span><span class="sxs-lookup"><span data-stu-id="1faff-122">Declaring instances of delegates</span></span>

<span data-ttu-id="1faff-123">Temsilci tanımladıktan sonra o türünün bir örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1faff-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="1faff-124">C# tüm değişkenler gibi bir ad alanındaki doğrudan ya da genel ad alanında temsilci örneklerinin bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1faff-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="1faff-125">Değişken türü `Comparison<T>`, daha önce tanımlanan temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="1faff-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="1faff-126">Değişken adı `comparator`.</span><span class="sxs-lookup"><span data-stu-id="1faff-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="1faff-127">Yukarıdaki kod parçacığında, bir üye değişkenine bir sınıf içinde bildirildi.</span><span class="sxs-lookup"><span data-stu-id="1faff-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="1faff-128">Yerel değişkenler ya da bağımsız değişkenleri yöntemleri için temsilci değişkenleri de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1faff-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="1faff-129">Çağıran temsilciler</span><span class="sxs-lookup"><span data-stu-id="1faff-129">Invoking Delegates</span></span>

<span data-ttu-id="1faff-130">Bu temsilci çağırarak bir temsilci çağırma listesi yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="1faff-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="1faff-131">İçinde `Sort()` yöntemi, kodun hangi sırada yerleştirmek için nesneleri belirlemek için karşılaştırma yöntemi çağıracaktır:</span><span class="sxs-lookup"><span data-stu-id="1faff-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="1faff-132">Yukarıdaki kod satırına *çağırır* yöntemi temsilciye bağlı.</span><span class="sxs-lookup"><span data-stu-id="1faff-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="1faff-133">Değişken bir yöntem adı kabul eder ve normal yöntemi çağrı sözdizimini kullanarak çağırma.</span><span class="sxs-lookup"><span data-stu-id="1faff-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="1faff-134">Bu kod satırı güvenli olmayan bir varsayım yapmaz: hedef temsilciye eklendi garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1faff-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="1faff-135">Hiçbir hedef eklediyseniz, yukarıdaki satır neden olacağından bir `NullReferenceException` oluşturulmasına.</span><span class="sxs-lookup"><span data-stu-id="1faff-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="1faff-136">Bu sorunu gidermek için kullanılan deyimleri basit bir null denetimi daha karmaşıktır ve daha sonra bu konuda ele alınmıştır [serisi](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="1faff-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="1faff-137">Atama, ekleme ve çağırma hedeflerini kaldırma</span><span class="sxs-lookup"><span data-stu-id="1faff-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="1faff-138">Bir temsilci türü nasıl tanımlanır ve temsilci örneklerinin nasıl bildirilir ve çağrılan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1faff-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="1faff-139">Kullanmak istediğiniz geliştiriciler `List.Sort()` yöntemi ihtiyacınız olan imza temsilci türü tanımı eşleşen bir yöntemi tanımlamak ve sıralama yöntemi tarafından kullanılan temsilci atamak.</span><span class="sxs-lookup"><span data-stu-id="1faff-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="1faff-140">Bu atama yöntemi temsilci nesnenin çağırma listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="1faff-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="1faff-141">Dizeleri listesini kendi uzunluğa göre sıralamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="1faff-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="1faff-142">Karşılaştırma işlevinizi şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="1faff-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="1faff-143">Yöntemi, özel bir yöntem olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="1faff-143">The method is declared as a private method.</span></span> <span data-ttu-id="1faff-144">Bu sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="1faff-144">That's fine.</span></span> <span data-ttu-id="1faff-145">Ortak arabirimi bir parçası olması için bu yöntemi istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1faff-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="1faff-146">Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1faff-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="1faff-147">Çağrıyı yapan kod temsilci nesnesini hedef listeye eklenen bu yöntem sahip olur ve bu temsilciyi erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1faff-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="1faff-148">Bu yönteme geçirerek bu ilişki oluşturmak `List.Sort()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1faff-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="1faff-149">Yöntem adı, parantez olmadan kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1faff-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="1faff-150">Yöntemin bağımsız değişken olarak kullanarak, bu yöntem çağırma hedefi olarak eklemek ve temsilci çağırma hedef olarak kullanılabilir bir başvuru yöntemi başvuru dönüştürmek için derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="1faff-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="1faff-151">Ayrıca türünde bir değişken bildirerek açık atanmış olmanız ' karşılaştırma<string>' ve bir ataması yapıyor:</span><span class="sxs-lookup"><span data-stu-id="1faff-151">You could also have been explicit by declaring a variable of type 'Comparison<string>\` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="1faff-152">Bir temsilci hedef küçük bir yöntem olarak kullanılmakta olan yöntemin olduğu kullanmak için yaygın kullanımları içinde [Lambda ifadesi](lambda-expressions.md) ataması gerçekleştirmek için söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="1faff-152">In uses where the method being used as a delegate target is a small method, it's common to use [Lambda Expression](lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="1faff-153">Lambda ifadeleri için temsilci hedefleri kullanarak kapsanan daha içinde bir [daha sonra bölüm](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="1faff-153">Using Lambda Expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="1faff-154">Sort() örnek, bir tek hedef yöntemi temsilciye genellikle iliştirir.</span><span class="sxs-lookup"><span data-stu-id="1faff-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="1faff-155">Ancak, temsilci nesneleri bir temsilci nesnesine bağlı birden çok hedef yöntemleri çağırma listelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1faff-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="1faff-156">Temsilci ve MulticastDelegate sınıfları</span><span class="sxs-lookup"><span data-stu-id="1faff-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="1faff-157">Yukarıda açıklanan dil desteği, özellikleri ve genellikle temsilciler ile çalışması gerekir desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1faff-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="1faff-158">Bu özellikler iki sınıf .NET Core Framework üzerine kurulu: <xref:System.Delegate> ve <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="1faff-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="1faff-159">`System.Delegate` Sınıfı ve onun tek doğrudan alt sınıfını `System.MulticastDelegate`, temsilci oluşturmak, yöntemleri temsilci hedefleri olarak kaydetme ve temsilci hedef olarak kayıtlı olan tüm yöntemleri çağırma framework desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1faff-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="1faff-160">İlginçtir ki, `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerini olmayan temsilci türleri.</span><span class="sxs-lookup"><span data-stu-id="1faff-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="1faff-161">Bunlar, tüm özel temsilci türleri için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="1faff-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="1faff-162">İşlem zorunlu bir sınıfı bildiremezsiniz aynı dil tasarımında, türetilen olduğunu `Delegate` veya `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="1faff-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="1faff-163">C# dil kurallarına yasaklayabilmek.</span><span class="sxs-lookup"><span data-stu-id="1faff-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="1faff-164">Bunun yerine, C# derleyici türetilmiş bir sınıf örneklerini oluşturur `MulticastDelegate` temsilci türleri bildirmek için C# dil anahtar sözcüğünü kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="1faff-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="1faff-165">Bu tasarım, kökleri ve C# .NET ilk sürümünde sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1faff-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="1faff-166">Dil temsilciler kullanırken tür güvenliği uygulanmasını sağlamak için bir hedef Tasarım ekibi için oluştu.</span><span class="sxs-lookup"><span data-stu-id="1faff-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="1faff-167">Temsilciler sağ türü ve bağımsız değişken sayısı ile çağrıldı emin olma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1faff-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="1faff-168">Derleme zamanı ve herhangi bir dönüş türü en doğru belirtildi.</span><span class="sxs-lookup"><span data-stu-id="1faff-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="1faff-169">Temsilciler önce genel türler edildi 1.0 .NET sürüm parçası olan.</span><span class="sxs-lookup"><span data-stu-id="1faff-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="1faff-170">Bu tür güvenliği zorlamak için en iyi yolu derleyici somut temsilci kullanılan yöntem imzası temsil sınıfları oluşturmak oluştu.</span><span class="sxs-lookup"><span data-stu-id="1faff-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="1faff-171">Türetilen sınıflar doğrudan oluşturamaz olsa da, bu sınıflara tanımlanan yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="1faff-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="1faff-172">Temsilciler ile çalışırken kullanacağınız en yaygın yöntemleri aracılığıyla edelim.</span><span class="sxs-lookup"><span data-stu-id="1faff-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="1faff-173">Anımsaması ilk ve en önemli ile çalışırsınız her temsilci türetilmiş gerçeğidir `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="1faff-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="1faff-174">Çok noktaya yayın temsilci bir temsilci çağrılırken, birden fazla yöntem hedef çağrılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1faff-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="1faff-175">Özgün Tasarım olarak kabul burada yalnızca bir hedef yönteme bağlı çağrılır ve yüklenemedi Temsilciler ve burada birden çok hedef yöntemi bağlı çağrılır ve yüklenemedi temsilciler arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="1faff-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="1faff-176">Bu ayrım başlangıçta zorlayıcı daha uygulamada daha az kullanışlı olması için oluyor uygulamasına yol açıyordu.</span><span class="sxs-lookup"><span data-stu-id="1faff-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="1faff-177">Farklı iki sınıf zaten oluşturulmuş ve framework ilk sürülmeden itibaren kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="1faff-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="1faff-178">En temsilciler ile kullanacağınız yöntemler `Invoke()` ve `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="1faff-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="1faff-179">`Invoke()` belirli temsilci örneğine bağlı tüm yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="1faff-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="1faff-180">Yukarıda gördüğünüz gibi genellikle temsilcileri temsilci değişkeni yöntemi çağrı sözdizimini kullanarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="1faff-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="1faff-181">Gördüğünüz gibi [bu serideki sonraki](delegates-patterns.md), doğrudan bu yöntemlerle iş desenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1faff-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="1faff-182">Dili sözdizimi ve temsilciler destekleyen sınıfları gördüğünüze göre nasıl kesin türü belirtilmiş temsilciler inceleyelim, oluşturulan çağrılır ve kullanıldığını.</span><span class="sxs-lookup"><span data-stu-id="1faff-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="1faff-183">Next</span><span class="sxs-lookup"><span data-stu-id="1faff-183">Next</span></span>](delegates-strongly-typed.md)
