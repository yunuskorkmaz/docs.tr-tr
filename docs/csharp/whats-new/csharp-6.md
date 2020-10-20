---
title: C# 6 ' daki yenilikler-C# Kılavuzu
description: C# sürüm 6 ' daki yeni özellikleri öğrenin
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224234"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="df753-103">C# 6 ' daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="df753-103">What's New in C# 6</span></span>

<span data-ttu-id="df753-104">C# 6,0 sürümü, geliştiriciler için üretkenliği geliştiren birçok özellik Içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="df753-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="df753-105">Bu özelliklerin genel etkisi, daha okunaklı olan daha kısa kodlar yazmanızı de ister.</span><span class="sxs-lookup"><span data-stu-id="df753-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="df753-106">Söz dizimi birçok yaygın uygulama için daha az sertifika içerir.</span><span class="sxs-lookup"><span data-stu-id="df753-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="df753-107">Tasarım amacını daha az seremle görmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="df753-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="df753-108">Bu özellikleri iyi öğrenin ve daha üretken olacak daha fazla kod yazmanız ve daha fazla okunabilir kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="df753-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="df753-109">Özelliklerden daha fazlasını, dilin yapılarından daha fazla odaklanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="df753-110">Bu makalenin geri kalanında, her bir özelliği keşfetmeye yönelik bir bağlantı ile bu özelliklerin her biri için bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df753-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="df753-111">Ayrıca öğreticiler bölümünde [C# 6 ' da etkileşimli bir araştırmayla ilgili](../tutorials/exploration/csharp-6.yml) özellikleri inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="df753-112">Salt okunurdur otomatik Özellikler</span><span class="sxs-lookup"><span data-stu-id="df753-112">Read-only auto-properties</span></span>

<span data-ttu-id="df753-113">*Salt okuma otomatik özellikleri* , sabit türler oluşturmak için daha kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="df753-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="df753-114">Auto özelliğini yalnızca bir get erişimcisi ile bildirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df753-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="df753-115">`FirstName`Ve `LastName` özellikleri yalnızca aynı sınıfın oluşturucusunun gövdesinde ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="df753-115">The `FirstName` and `LastName` properties can be set only in the body of the constructor of the same class:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="df753-116">Başka bir yöntemde ayarlamaya çalışmak `LastName` , `CS0200` derleme hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="df753-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="df753-117">Bu özellik, sabit türler oluşturmak için gerçek dil desteğini sunar ve daha kısa ve uygun otomatik özellik sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="df753-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="df753-118">Bu söz dizimini eklemek erişilebilir bir yöntemi kaldırmazsa, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.</span><span class="sxs-lookup"><span data-stu-id="df753-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="df753-119">Otomatik Özellik başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="df753-119">Auto-property initializers</span></span>

<span data-ttu-id="df753-120">*Otomatik Özellik başlatıcıları* , otomatik özellik için ilk değeri özellik bildiriminin bir parçası olarak bildirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="df753-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="df753-121">`Grades`Üye, bildirildiği yerde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="df753-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="df753-122">Bu, başlatmayı tam olarak bir kez gerçekleştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="df753-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="df753-123">Başlatma, özellik bildiriminin bir parçasıdır ve bu, depolama ayırmasının nesneler için ortak arabirimle daha kolay olmasını sağlar `Student` .</span><span class="sxs-lookup"><span data-stu-id="df753-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="df753-124">İfade-Bodied işlev üyeleri</span><span class="sxs-lookup"><span data-stu-id="df753-124">Expression-bodied function members</span></span>

<span data-ttu-id="df753-125">Yazdığınız birçok üye tek deyimler olabilecek tek ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="df753-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="df753-126">Bunun yerine Expression-Bodied üyesi yazın.</span><span class="sxs-lookup"><span data-stu-id="df753-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="df753-127">Yöntemler ve salt okunurdur özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="df753-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="df753-128">Örneğin, bir geçersiz kılma `ToString()` genellikle harika bir adaydır:</span><span class="sxs-lookup"><span data-stu-id="df753-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="df753-129">Bu sözdizimini salt okuma özellikleri için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df753-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="df753-130">Varolan bir üyenin bir ifade ile değiştirilmesi, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.</span><span class="sxs-lookup"><span data-stu-id="df753-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="df753-131">statik kullanma</span><span class="sxs-lookup"><span data-stu-id="df753-131">using static</span></span>

<span data-ttu-id="df753-132">*Statik geliştirme kullanımı* , tek bir sınıfın statik yöntemlerini içeri aktarmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="df753-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="df753-133">Kullanmakta olduğunuz sınıfı belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df753-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="df753-134"><xref:System.Math>Herhangi bir örnek yöntemi içermez.</span><span class="sxs-lookup"><span data-stu-id="df753-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="df753-135">`using static`Statik ve örnek yöntemlerine sahip bir sınıf için sınıf ' statik yöntemleri içeri aktarmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="df753-136">En yararlı örneklerden biri şunlardır <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="df753-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="df753-137">Statik bir using ifadesinde tam sınıf adını kullanmanız gerekir `System.String`  .</span><span class="sxs-lookup"><span data-stu-id="df753-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="df753-138">`string`Bunun yerine anahtar sözcüğünü kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="df753-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="df753-139">Bir `static using` deyimden içeri aktarıldığında, genişletme yöntemleri yalnızca uzantı yöntemi çağırma sözdizimi kullanılarak çağrıldığında kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="df753-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="df753-140">Statik bir yöntem olarak çağrıldığında kapsamda değildir.</span><span class="sxs-lookup"><span data-stu-id="df753-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="df753-141">Bunu genellikle LINQ sorgularında görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="df753-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="df753-142">Ya da içeri aktararak LINQ deseninin içeri aktarabilirsiniz <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="df753-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="df753-143">Uzantı yöntemlerini, genellikle uzantı yöntemi çağırma ifadelerini kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="df753-144">Statik yöntem çağrısı sözdizimini kullanarak çağırdığınız nadir bir durumda sınıf adı ekleme belirsizlik çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="df753-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="df753-145">`static using`Yönerge, iç içe geçmiş türleri de içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="df753-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="df753-146">Herhangi bir iç içe geçmiş türe, nitelik olmadan başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="df753-147">Null-koşullu işleçler</span><span class="sxs-lookup"><span data-stu-id="df753-147">Null-conditional operators</span></span>

<span data-ttu-id="df753-148">*Null koşullu işleç* , null denetimleri çok daha kolay ve akıcı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="df753-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="df753-149">Üye erişimini bununla değiştirin `.` `?.` :</span><span class="sxs-lookup"><span data-stu-id="df753-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="df753-150">Önceki örnekte, değişken, `first` kişi nesnesi ise atanır `null` `null` .</span><span class="sxs-lookup"><span data-stu-id="df753-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="df753-151">Aksi takdirde, özelliğin değeri atanır `FirstName` .</span><span class="sxs-lookup"><span data-stu-id="df753-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="df753-152">En önemlisi, `?.` Bu kod satırının, değişkeni ise, bir olarak yaramayacağı anlamına gelir `NullReferenceException` `person` `null` .</span><span class="sxs-lookup"><span data-stu-id="df753-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="df753-153">Bunun yerine, kısa devreler ve döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="df753-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="df753-154">Dizi veya Dizin Oluşturucu erişimi için null koşullu bir işleç de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="df753-155">`[]` `?[]` Dizin ifadesinde ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="df753-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="df753-156">Aşağıdaki ifade, değerinden bağımsız olarak bir döndürür `string` `person` .</span><span class="sxs-lookup"><span data-stu-id="df753-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="df753-157">Bu yapıyı genellikle, özelliklerden biri olduğunda varsayılan değerleri atamak için *null birleşim* işleciyle kullanırsınız `null` .</span><span class="sxs-lookup"><span data-stu-id="df753-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="df753-158">Kısa devre ifadesi olduğunda `null` döndürülen değer tam ifadeyle eşleşecek şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="df753-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="df753-159">`?.`Yöntemleri koşullu olarak çağırmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="df753-160">Null koşullu işleçle üye işlevlerinin en yaygın kullanımı, güvenli temsilcileri (veya olay işleyicilerini) güvenle çağırmadır `null` .</span><span class="sxs-lookup"><span data-stu-id="df753-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="df753-161">`Invoke`Üyeye erişmek için işlecini kullanarak temsilcinin yöntemini çağıracaksınız `?.` .</span><span class="sxs-lookup"><span data-stu-id="df753-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="df753-162">[Temsilci desenleri](../delegates-patterns.md#handling-null-delegates) makalesinde bir örnek görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="df753-163">İşlecinin kuralları, `?.` işlecin sol tarafının yalnızca bir kez değerlendirildiğinden emin olur.</span><span class="sxs-lookup"><span data-stu-id="df753-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="df753-164">Olay işleyicilerini kullanarak aşağıdaki örnek dahil olmak üzere birçok deyim sunar:</span><span class="sxs-lookup"><span data-stu-id="df753-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="df753-165">Sol tarafının yalnızca bir kez değerlendirilmesinin yanı sıra, yöntemin sol tarafındaki Yöntem çağrıları dahil herhangi bir ifadeyi kullanmanıza de olanak sağlar. `?.`</span><span class="sxs-lookup"><span data-stu-id="df753-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="df753-166">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="df753-166">String interpolation</span></span>

<span data-ttu-id="df753-167">C# 6 ile, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği bir dizeye ifade eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="df753-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="df753-168">Dizeyi yalnızca ile önyüz ve `$` `{` sıra sayıları yerine ve arasında ifadeleri kullanın `}` :</span><span class="sxs-lookup"><span data-stu-id="df753-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="df753-169">Bu örnek, değiştirilen ifadeler için özellikleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="df753-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="df753-170">Herhangi bir ifadeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-170">You can use any expression.</span></span> <span data-ttu-id="df753-171">Örneğin, ilişkilendirme 'nin bir parçası olarak bir öğrencinin sınıf noktası ortalamasını hesaplamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="df753-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="df753-172">Yukarıdaki kod satırı, değeri `Grades.Average()` iki ondalık basamakla kayan noktalı sayı olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="df753-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="df753-173">Genellikle, belirli bir kültür kullanılarak üretilen dizeyi biçimlendirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="df753-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="df753-174">Dize ilişkilendirme tarafından üretilen nesnenin örtük olarak öğesine dönüştürülebileceği olguyu kullanırsınız <xref:System.FormattableString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="df753-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="df753-175"><xref:System.FormattableString>Örnek, bileşik biçim dizesini ve ifadeleri dizelere dönüştürmeden önce değerlendirme sonuçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="df753-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="df753-176"><xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType>Bir dizeyi biçimlendirirken kültürü belirtmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="df753-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="df753-177">Aşağıdaki örnek, Almanya (de-DE) kültürünü kullanarak bir dize üretir.</span><span class="sxs-lookup"><span data-stu-id="df753-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="df753-178">(Varsayılan olarak, Almanya kültürü ondalık ayırıcı için ', ' karakterini ve binlik ayırıcı olarak '. ' karakterini kullanır.)</span><span class="sxs-lookup"><span data-stu-id="df753-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="df753-179">Dize ilişkilendirmeyi kullanmaya başlamak için bkz. c# etkileşimli öğreticisinde [dize ilişkilendirme](../tutorials/exploration/interpolated-strings.yml) , [dize ilişkilendirme](../language-reference/tokens/interpolated.md) makalesi ve c# öğreticisinde [dize ilişkilendirme](../tutorials/string-interpolation.md) .</span><span class="sxs-lookup"><span data-stu-id="df753-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="df753-180">Özel durum filtreleri</span><span class="sxs-lookup"><span data-stu-id="df753-180">Exception filters</span></span>

<span data-ttu-id="df753-181">*Özel durum filtreleri* , belirli bir catch yan tümcesinin ne zaman uygulanacağını tespit eden yan tümcelerdir.</span><span class="sxs-lookup"><span data-stu-id="df753-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="df753-182">Özel durum filtresi için kullanılan ifade olarak değerlendirilirse `true` , catch yan tümcesi bir özel durum üzerinde normal işlemesini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="df753-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="df753-183">İfade olarak değerlendirilirse `false` , `catch` yan tümce atlanır.</span><span class="sxs-lookup"><span data-stu-id="df753-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="df753-184">Bir kullanım, bir `catch` yan tümcenin özel durumu işleyebilmesine izin vermek için bir özel durumla ilgili bilgileri incelemektir:</span><span class="sxs-lookup"><span data-stu-id="df753-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="df753-185">`nameof`İfade</span><span class="sxs-lookup"><span data-stu-id="df753-185">The `nameof` expression</span></span>

<span data-ttu-id="df753-186">[NameOf](../language-reference/operators/nameof.md) ifadesinin bir sembolün adı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="df753-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="df753-187">Bir değişken, özellik veya üye alanı için her ihtiyaç duyduğunuzda, araçların çalışmasını sağlamak için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="df753-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="df753-188">İçin en yaygın `nameof` kullanımlardır bir özel duruma neden olan bir simgenin adını sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="df753-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="df753-189">Başka bir kullanım, arabirimini uygulayan XAML tabanlı uygulamalardır `INotifyPropertyChanged` :</span><span class="sxs-lookup"><span data-stu-id="df753-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="df753-190">Catch ve finally bloklarında await</span><span class="sxs-lookup"><span data-stu-id="df753-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="df753-191">C# 5 ' te ifadeler yerleştirebileceğiniz yerde çeşitli sınırlamalar vardı `await` .</span><span class="sxs-lookup"><span data-stu-id="df753-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="df753-192">C# 6 ile artık `await` `catch` veya ifadeleri içinde kullanabilirsiniz `finally` .</span><span class="sxs-lookup"><span data-stu-id="df753-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="df753-193">Bu, genellikle günlük senaryolarıyla kullanılır:</span><span class="sxs-lookup"><span data-stu-id="df753-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="df753-194">İçinde destek eklemek için uygulama ayrıntıları `await` `catch` ve `finally` yan tümceleri, davranışın zaman uyumlu kod davranışıyla tutarlı olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="df753-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="df753-195">`catch`Or `finally` yan tümcesinde yürütülen kod oluşturduğunda, yürütme `catch` sonraki çevresindeki blokta uygun bir yan tümce arar.</span><span class="sxs-lookup"><span data-stu-id="df753-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="df753-196">Geçerli bir özel durum varsa, bu özel durum kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="df753-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="df753-197">Aynı durum, `catch` ve `finally` yan tümcelerinde beklenen ifadelerle aynıdır: için uygun bir `catch` aranır ve varsa geçerli özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="df753-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="df753-198">Bu davranış, `catch` `finally` Yeni özel durumlar oluşturmamaya özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="df753-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="df753-199">Dizin oluşturucular kullanarak ilişkilendirilebilir koleksiyonları başlatma</span><span class="sxs-lookup"><span data-stu-id="df753-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="df753-200">*Dizin başlatıcıları* , koleksiyon başlatıcılarının Dizin kullanımıyla daha tutarlı olmasını sağlayan iki özellikten biridir.</span><span class="sxs-lookup"><span data-stu-id="df753-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="df753-201">C# ' nin önceki sürümlerinde, *collection initializers* <xref:System.Collections.Generic.Dictionary%602> anahtar ve değer çiftleri etrafında küme ayraçları ekleyerek sıra stili koleksiyonlarıyla koleksiyon başlatıcıları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df753-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="df753-202">Bunları, <xref:System.Collections.Generic.Dictionary%602> erişilebilir `Add` yöntemin birden fazla bağımsız değişken kabul ettiği koleksiyonlar ve diğer türlerle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df753-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="df753-203">Yeni sözdizimi, koleksiyona bir dizin kullanılarak atamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="df753-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="df753-204">Bu özellik, çeşitli sürümlere yönelik dizi kapsayıcılarına benzer bir sözdizimi kullanılarak ilişkilendirilebilir kapsayıcıların başlatılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="df753-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="df753-205">`Add`Koleksiyon başlatıcılarında uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="df753-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="df753-206">Koleksiyon başlatmayı daha kolay hale getiren başka bir özellik, yöntemi için bir *genişletme yöntemi* kullanma olanağıdır `Add` .</span><span class="sxs-lookup"><span data-stu-id="df753-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="df753-207">Bu özellik Visual Basic eşlik için eklendi.</span><span class="sxs-lookup"><span data-stu-id="df753-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="df753-208">Özelliği, en çok, anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip bir yöntemi olan bir özel koleksiyon sınıfınız olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="df753-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="df753-209">Geliştirilmiş aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="df753-209">Improved overload resolution</span></span>

<span data-ttu-id="df753-210">Bu son özellik, büyük olasılıkla fark edilmeyecek bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="df753-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="df753-211">Önceki C# derleyicisi sürümünde lambda ifadeleri içeren bazı yöntem çağrılarının bulduğu yapılar vardı.</span><span class="sxs-lookup"><span data-stu-id="df753-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="df753-212">Şu yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="df753-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="df753-213">C# ' nin önceki sürümlerinde, Yöntem grubu sözdizimini kullanarak bu yöntemi çağırmak başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="df753-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="df753-214">Önceki derleyici ve arasında doğru şekilde ayırt `Task.Run(Action)` edilemedi `Task.Run(Func<Task>())` .</span><span class="sxs-lookup"><span data-stu-id="df753-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="df753-215">Önceki sürümlerde bağımsız değişken olarak bir lambda ifadesi kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="df753-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="df753-216">C# 6 derleyicisi, `Task.Run(Func<Task>())` daha iyi bir seçim olduğunu doğru şekilde belirler.</span><span class="sxs-lookup"><span data-stu-id="df753-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="df753-217">Belirleyici derleyici çıkışı</span><span class="sxs-lookup"><span data-stu-id="df753-217">Deterministic compiler output</span></span>

<span data-ttu-id="df753-218">`-deterministic`Seçeneği derleyiciye aynı kaynak dosyaların birbirini izleyen derlemeler için bayt için aynı çıkış derlemesi oluşturmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="df753-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="df753-219">Varsayılan olarak, her derleme her derlemede benzersiz çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="df753-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="df753-220">Derleyici, bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekler.</span><span class="sxs-lookup"><span data-stu-id="df753-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="df753-221">Bu seçeneği, derlemeler genelinde tutarlılığı sağlamak üzere bayt için bayt çıkışı karşılaştırmak istiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="df753-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="df753-222">Daha fazla bilgi için, bkz. [belirleyici derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="df753-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
