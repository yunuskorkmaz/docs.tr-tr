---
title: C# 6'da Yenilikler - C# Rehberi
description: C# Sürüm 6'daki yeni özellikleri öğrenin
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399394"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="755ce-103">C# 6'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="755ce-103">What's New in C# 6</span></span>

<span data-ttu-id="755ce-104">C#'ın 6.0 sürümü, geliştiriciler için üretkenliği artıran birçok özellik içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="755ce-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="755ce-105">Bu özelliklerin genel etkisi, aynı zamanda daha okunabilir daha kısa kod yazmak olduğunu.</span><span class="sxs-lookup"><span data-stu-id="755ce-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="755ce-106">Sözdizimi birçok yaygın uygulamalar için daha az tören içerir.</span><span class="sxs-lookup"><span data-stu-id="755ce-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="755ce-107">Daha az törenle tasarım niyetini görmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="755ce-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="755ce-108">Bu özellikleri iyi öğrenin ve daha üretken olun ve daha okunabilir kodlar yazın.</span><span class="sxs-lookup"><span data-stu-id="755ce-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="755ce-109">Dilin yapısından çok özelliklerinize odaklanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="755ce-110">Bu makalenin geri kalanı, her özelliği keşfetmek için bir bağlantı ile, bu özelliklerin her biri genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="755ce-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="755ce-111">Ayrıca, [c# 6'daki etkileşimli](../tutorials/exploration/csharp-6.yml) bir keşifte, öğreticiler bölümündeki özellikleri de keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="755ce-112">Salt okunur otomatik özellikler</span><span class="sxs-lookup"><span data-stu-id="755ce-112">Read-only auto-properties</span></span>

<span data-ttu-id="755ce-113">*Yalnızca okunur otomatik özellikler,* değişmez türler oluşturmak için daha kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="755ce-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="755ce-114">Otomatik özelliği yalnızca bir erişime sahip olarak bildirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="755ce-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="755ce-115">Ve `FirstName` `LastName` özellikleri yalnızca aynı sınıfın oluşturucusu gövdesinde ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="755ce-115">The `FirstName` and `LastName` properties can be set only in the body of the constructor of the same class:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="755ce-116">Başka bir `LastName` yöntemde ayarlanmayı denemek bir `CS0200` derleme hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="755ce-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="755ce-117">Bu özellik, değişmez türleri oluşturmak için gerçek dil desteği sağlar ve daha kısa ve kullanışlı otomatik özellik sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="755ce-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="755ce-118">Bu sözdizimini eklemek erişilebilir bir yöntemi kaldırmazsa, ikili uyumlu bir [değişikliktir.](version-update-considerations.md#binary-compatible-changes)</span><span class="sxs-lookup"><span data-stu-id="755ce-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="755ce-119">Otomatik özellik başlangıç layıcıları</span><span class="sxs-lookup"><span data-stu-id="755ce-119">Auto-property initializers</span></span>

<span data-ttu-id="755ce-120">*Otomatik özellik baş harfleri,* bir otomatik mülkün başlangıç değerini özellik bildiriminin bir parçası olarak beyan etmenize izin verebiliyor.</span><span class="sxs-lookup"><span data-stu-id="755ce-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="755ce-121">`Grades` Üye, beyan edildiği yerde paraya yatırılır.</span><span class="sxs-lookup"><span data-stu-id="755ce-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="755ce-122">Bu, başlatmayı tam olarak bir kez gerçekleştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="755ce-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="755ce-123">Başlatma özelliği bildiriminin bir parçasıdır, bu da depolama ayırmasını nesneler için `Student` ortak arabirimle eşitlemesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="755ce-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="755ce-124">İfade gövdeli işlev üyeleri</span><span class="sxs-lookup"><span data-stu-id="755ce-124">Expression-bodied function members</span></span>

<span data-ttu-id="755ce-125">Yazdığınız birçok üye, tek ifadeler olabilecek tek ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="755ce-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="755ce-126">Bunun yerine ifade gövdeli bir üye yazın.</span><span class="sxs-lookup"><span data-stu-id="755ce-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="755ce-127">Yöntemler ve salt okunur özellikler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="755ce-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="755ce-128">Örneğin, geçersiz kılma `ToString()` genellikle büyük bir adaydır:</span><span class="sxs-lookup"><span data-stu-id="755ce-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="755ce-129">Salt okunur özellikler için bu sözdizimini de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="755ce-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="755ce-130">Varolan bir üyeyi ifade gövdeli bir üyeye değiştirmek ikili uyumlu bir [değişikliktir.](version-update-considerations.md#binary-compatible-changes)</span><span class="sxs-lookup"><span data-stu-id="755ce-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="755ce-131">statik kullanarak</span><span class="sxs-lookup"><span data-stu-id="755ce-131">using static</span></span>

<span data-ttu-id="755ce-132">*Statik geliştirmeyi kullanma,* tek bir sınıfın statik yöntemlerini içe aktarmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="755ce-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="755ce-133">Kullandığınız sınıfı belirtin:</span><span class="sxs-lookup"><span data-stu-id="755ce-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="755ce-134">Herhangi <xref:System.Math> bir örnek yöntemi içermez.</span><span class="sxs-lookup"><span data-stu-id="755ce-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="755ce-135">Hem statik `using static` hem de örnek yöntemleri olan bir sınıf için sınıfın statik yöntemlerini almak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="755ce-136">En yararlı örneklerden <xref:System.String>biri:</span><span class="sxs-lookup"><span data-stu-id="755ce-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="755ce-137">Tam nitelikli sınıf adını statik `System.String` bir şekilde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="755ce-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="755ce-138">Bunun yerine `string` anahtar sözcüğü kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="755ce-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="755ce-139">Bir `static using` deyimden aktarıldığında, uzantı yöntemi sözdizimi kullanılarak çağrıldığında uzantı yöntemleri yalnızca kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="755ce-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="755ce-140">Statik bir yöntem olarak çağrıldığında kapsam içinde değildirler.</span><span class="sxs-lookup"><span data-stu-id="755ce-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="755ce-141">Bunu sık sık LINQ sorgularında görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="755ce-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="755ce-142">Linq deseni içe aktararak <xref:System.Linq.Enumerable>veya <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="755ce-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="755ce-143">Uzantı yöntemi çağırma ifadelerini kullanarak genellikle uzantı yöntemlerini çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="755ce-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="755ce-144">Statik yöntem kullanarak onları aramak nadir durumda sınıf adı ekleme sözdizimi çağrı belirsizliği giderir.</span><span class="sxs-lookup"><span data-stu-id="755ce-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="755ce-145">Yönerge `static using` ayrıca iç içe herhangi bir türü de içeri iter.</span><span class="sxs-lookup"><span data-stu-id="755ce-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="755ce-146">Nitelik olmadan iç içe herhangi bir tür başvuru yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="755ce-147">Null koşullu işleçler</span><span class="sxs-lookup"><span data-stu-id="755ce-147">Null-conditional operators</span></span>

<span data-ttu-id="755ce-148">*Null koşullu işleç* null kontrolleri çok daha kolay ve akışkan hale getirir.</span><span class="sxs-lookup"><span data-stu-id="755ce-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="755ce-149">Üye erişimini `.` aşağıdakilerle değiştirin: `?.`</span><span class="sxs-lookup"><span data-stu-id="755ce-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="755ce-150">Önceki örnekte, `first` `null` kişi nesnesi `null`.</span><span class="sxs-lookup"><span data-stu-id="755ce-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="755ce-151">Aksi takdirde, `FirstName` özelliğin değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="755ce-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="755ce-152">En önemlisi, `?.` bu kod satırı `person` değişkeni ise `null` `NullReferenceException` bir oluşturmaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="755ce-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="755ce-153">Bunun yerine, kısa devreler `null`ve döner.</span><span class="sxs-lookup"><span data-stu-id="755ce-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="755ce-154">Dizi veya dizinleyici erişimi için null koşullu işleci de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="755ce-155">Dizin `?[]` ifadesinde değiştirin. `[]`</span><span class="sxs-lookup"><span data-stu-id="755ce-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="755ce-156">Aşağıdaki ifade, `string`değerine bakılmaksızın bir `person`döndürür.</span><span class="sxs-lookup"><span data-stu-id="755ce-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="755ce-157">Bu yapıyı genellikle *null coalescing* işleci ile birlikte kullanırsınız, `null`özelliklerden biri .</span><span class="sxs-lookup"><span data-stu-id="755ce-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="755ce-158">İfade kısa devreyaptığında, döndürülen `null` değer tam ifadeyle eşleşecek şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="755ce-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="755ce-159">Yöntemleri koşullu `?.` olarak çağırmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="755ce-160">Null koşullu işleç ile üye işlevlerin en yaygın kullanımı güvenli bir şekilde temsilcileri çağırmak `null`için (veya olay işleyicileri) olabilir .</span><span class="sxs-lookup"><span data-stu-id="755ce-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="755ce-161">Üyeye erişmek için `Invoke` `?.` işleci kullanarak temsilcinin yöntemini ararsınız.</span><span class="sxs-lookup"><span data-stu-id="755ce-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="755ce-162">[Temsilci desenleri](../delegates-patterns.md#handling-null-delegates) makalesinde bir örnek görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="755ce-163">İşleticinin `?.` kuralları, işlecinin sol tarafının yalnızca bir kez değerlendirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="755ce-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="755ce-164">Olay işleyicileri kullanarak aşağıdaki örnek de dahil olmak üzere birçok deyimsağlar:</span><span class="sxs-lookup"><span data-stu-id="755ce-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="755ce-165">Sol tarafın sadece bir kez değerlendirilmesini sağlamak, yöntem aramaları da dahil olmak üzere, sol taraftaki herhangi bir ifadeyi`?.`</span><span class="sxs-lookup"><span data-stu-id="755ce-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="755ce-166">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="755ce-166">String interpolation</span></span>

<span data-ttu-id="755ce-167">C# 6 ile yeni [dize enterpolasyon](../language-reference/tokens/interpolated.md) özelliği ifadeleri bir dize ye gömmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="755ce-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="755ce-168">Yalnızca dize ile `$`önsöz ve `{` `}` yerine ordinals arasında ifadeler kullanın:</span><span class="sxs-lookup"><span data-stu-id="755ce-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="755ce-169">Bu örnek, değiştirilen ifadeler için özellikler kullanır.</span><span class="sxs-lookup"><span data-stu-id="755ce-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="755ce-170">Herhangi bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-170">You can use any expression.</span></span> <span data-ttu-id="755ce-171">Örneğin, bir öğrencinin not ortalamasını enterpolasyonun bir parçası olarak hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="755ce-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="755ce-172">Önceki kod satırı, iki ondalık basamakla kayan nokta sayısı `Grades.Average()` olarak değeri biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="755ce-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="755ce-173">Genellikle, belirli bir kültür kullanılarak üretilen dize biçimlendirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="755ce-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="755ce-174">Bir dize enterpolasyonu tarafından üretilen nesnenin örtülü olarak <xref:System.FormattableString?displayProperty=nameWithType>.'e dönüştürülebileceği gerçeğini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="755ce-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="755ce-175">Örnek, <xref:System.FormattableString> bileşik biçim dizesi ve dizeleri dönüştürmeden önce ifadeleri değerlendirme sonuçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="755ce-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="755ce-176">Bir <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> dize biçimlendirirken kültürü belirtmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="755ce-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="755ce-177">Aşağıdaki örnek, Almanca (de-DE) kültürünü kullanarak bir dize üretir.</span><span class="sxs-lookup"><span data-stu-id="755ce-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="755ce-178">(Varsayılan olarak, Alman kültürü ondalık ayırıcı için ',' karakterini ve binlerce ayırıcı olarak '.' karakterini kullanır.)</span><span class="sxs-lookup"><span data-stu-id="755ce-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="755ce-179">String enterpolasyonuile başlamak için C# etkileşimli [öğreticideki String enterpolasyonunu,](../tutorials/exploration/interpolated-strings.yml) [String enterpolasyon](../language-reference/tokens/interpolated.md) makalesini ve [C# öğreticisinde String enterpolasyonunu](../tutorials/string-interpolation.md) görün.</span><span class="sxs-lookup"><span data-stu-id="755ce-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="755ce-180">Özel durum filtreleri</span><span class="sxs-lookup"><span data-stu-id="755ce-180">Exception filters</span></span>

<span data-ttu-id="755ce-181">*Özel Durum Filtreleri,* belirli bir yakalama yan tümcesi uygulanacağı zaman belirleyen yan tümcelerdir.</span><span class="sxs-lookup"><span data-stu-id="755ce-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="755ce-182">Bir özel durum filtresi için kullanılan `true`ifade değerlendirirse, catch yan tümcesi bir özel durum üzerinde normal işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="755ce-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="755ce-183">İfade için `false`değerlendirilirse, `catch` yan tümce atlanır.</span><span class="sxs-lookup"><span data-stu-id="755ce-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="755ce-184">Bir kullanım, bir `catch` yan tümcenin özel durumu işleyip işlemeyebileceğini belirlemek için bir özel durum la ilgili bilgileri incelemektir:</span><span class="sxs-lookup"><span data-stu-id="755ce-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="755ce-185">İfade `nameof`</span><span class="sxs-lookup"><span data-stu-id="755ce-185">The `nameof` expression</span></span>

<span data-ttu-id="755ce-186">İfade [adı](../language-reference/operators/nameof.md) bir sembolün adını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="755ce-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="755ce-187">Bir değişkenin, bir özelliğin veya üye alanın adına ihtiyaç duyduğunuzda araçların çalışmasını sağlamak için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="755ce-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="755ce-188">Bunun en yaygın kullanımlarından `nameof` biri, özel bir özel durum oluşturan bir simgenin adını sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="755ce-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="755ce-189">Başka bir kullanım `INotifyPropertyChanged` arabirimi uygulayan XAML tabanlı uygulamalar ile:</span><span class="sxs-lookup"><span data-stu-id="755ce-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="755ce-190">Catch ve Finally bloklarda bekleyin</span><span class="sxs-lookup"><span data-stu-id="755ce-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="755ce-191">C# 5'in ifadelerin ilerleyebileceği `await` birkaç sınırlaması vardı.</span><span class="sxs-lookup"><span data-stu-id="755ce-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="755ce-192">C# 6 ile artık `await` ifadeleri `catch` `finally` veya ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="755ce-193">Bu en sık günlük senaryoları ile kullanılır:</span><span class="sxs-lookup"><span data-stu-id="755ce-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="755ce-194">İçeride `await` `catch` destek eklemek için `finally` uygulama ayrıntıları ve yan tümceler, davranışın eşzamanlı kod davranışıyla tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="755ce-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="755ce-195">Bir `catch` veya `finally` yan tümce de yürütüldüğünde, `catch` yürütme sonraki çevre bloğunda uygun bir yan tümce arar.</span><span class="sxs-lookup"><span data-stu-id="755ce-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="755ce-196">Geçerli bir özel durum varsa, bu özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="755ce-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="755ce-197">Aynı durum beklenen ifadeler `catch` ve `finally` yan tümceler `catch` ile de olur: uygun bir arama yapılır ve varsa geçerli özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="755ce-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="755ce-198">Bu davranış, yeni özel durumlar `catch` getirilmesini önlemek için dikkatle yazmak ve `finally` yantümler önerilir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="755ce-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="755ce-199">Dizinleyicileri kullanarak bağdaştırıcı koleksiyonları başlatma</span><span class="sxs-lookup"><span data-stu-id="755ce-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="755ce-200">*Dizin Initializers,* koleksiyon başlatılmasını dizin kullanımıyla daha tutarlı hale getiren iki özellikten biridir.</span><span class="sxs-lookup"><span data-stu-id="755ce-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="755ce-201">C#'ın önceki sürümlerinde, anahtar ve değer çiftleri etrafında <xref:System.Collections.Generic.Dictionary%602>ayraçlar ekleyerek sıra stili koleksiyonları içeren *koleksiyon başlatmalayıcılarını* kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="755ce-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="755ce-202">Bunları, erişilebilir `Add` <xref:System.Collections.Generic.Dictionary%602> yöntemin birden fazla bağımsız değişkeni kabul ettiği koleksiyonlar ve diğer türlerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755ce-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="755ce-203">Yeni sözdizimi, koleksiyona bir dizin kullanarak atamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="755ce-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="755ce-204">Bu özellik, bağşılı kapsayıcıların, çeşitli sürümler için sıra kapsayıcıları için yerinde olana benzer sözdizimi kullanılarak başharflerle başlatAbileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="755ce-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="755ce-205">Toplama `Add` başlatma da uzatma yöntemleri</span><span class="sxs-lookup"><span data-stu-id="755ce-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="755ce-206">Toplama başlatmayı kolaylaştıran bir diğer özellik de `Add` yöntem için bir *uzantı yöntemi* kullanabilme özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="755ce-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="755ce-207">Bu özellik Visual Basic ile eşlik için eklendi.</span><span class="sxs-lookup"><span data-stu-id="755ce-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="755ce-208">Bu özellik, semantik olarak yeni öğeler eklemek için farklı bir ada sahip bir yönteme sahip özel bir koleksiyon sınıfına sahipolduğunuzda en kullanışlı özelliktir.</span><span class="sxs-lookup"><span data-stu-id="755ce-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="755ce-209">Geliştirilmiş aşırı yük çözünürlüğü</span><span class="sxs-lookup"><span data-stu-id="755ce-209">Improved overload resolution</span></span>

<span data-ttu-id="755ce-210">Bu son özellik muhtemelen fark olmaz biridir.</span><span class="sxs-lookup"><span data-stu-id="755ce-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="755ce-211">C# derleyicisinin önceki sürümünün lambda ifadelerini içeren bazı yöntem çağrılarının belirsiz bulduğu yapılar vardı.</span><span class="sxs-lookup"><span data-stu-id="755ce-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="755ce-212">Bu yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="755ce-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="755ce-213">C#'ın önceki sürümlerinde, yöntem grubu sözdizimini kullanarak bu yöntemi çağırmak başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="755ce-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="755ce-214">Önceki derleyici ile `Task.Run(Action)` `Task.Run(Func<Task>())`' yi doğru ayırt edemedi.</span><span class="sxs-lookup"><span data-stu-id="755ce-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="755ce-215">Önceki sürümlerde, bir argüman olarak bir lambda ifadesi kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="755ce-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="755ce-216">C# 6 derleyicisi bunun `Task.Run(Func<Task>())` daha iyi bir seçim olduğunu doğru bir şekilde belirler.</span><span class="sxs-lookup"><span data-stu-id="755ce-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="755ce-217">Deterministik derleyici çıktısı</span><span class="sxs-lookup"><span data-stu-id="755ce-217">Deterministic compiler output</span></span>

<span data-ttu-id="755ce-218">Seçenek, `-deterministic` derleyiciye aynı kaynak dosyalarının ardışık derlemeleri için bayt için bir aynı çıktı derlemesi oluşturmasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="755ce-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="755ce-219">Varsayılan olarak, her derleme her derlemede benzersiz çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="755ce-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="755ce-220">Derleyici bir zaman damgası ve rasgele sayılardan oluşturulan bir GUID ekler.</span><span class="sxs-lookup"><span data-stu-id="755ce-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="755ce-221">Yapılar arasında tutarlılık sağlamak için bayt için bayt çıktısını karşılaştırmak istiyorsanız bu seçeneği kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="755ce-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="755ce-222">Daha fazla bilgi için [-deterministic derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="755ce-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
