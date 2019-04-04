---
title: C# 6 - C# Kılavuzu yenilikler nelerdir?
description: C# sürüm 6'daki yeni özelliklerin öğrenin
ms.date: 12/12/2018
ms.openlocfilehash: 478fd512f6b6facfce6d7f70f9691ce15e418d6e
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920681"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="e78cb-103">C# 6 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="e78cb-103">What's New in C# 6</span></span>

<span data-ttu-id="e78cb-104">C# 6.0 sürüm, geliştiriciler için üretkenliği artıran birçok özellik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e78cb-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="e78cb-105">Bu özellikler genel etkisini de daha okunabilir daha kısa kod yazma ' dir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="e78cb-106">Birçok ortak uygulamalar için daha az seremoni söz dizimi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e78cb-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="e78cb-107">Tasarım hedefi ile daha az seremoni görmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="e78cb-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="e78cb-108">Bu özellikler de öğrenin ve daha üretken ve daha okunabilir bir kod yazma.</span><span class="sxs-lookup"><span data-stu-id="e78cb-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="e78cb-109">Daha özellikleri dil yapıları üzerinde odaklanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78cb-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="e78cb-110">Bu makalenin geri kalanında her bir özellik keşfetmek için bir bağlantı ile bu özelliklerin her biri bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78cb-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="e78cb-111">Özellikleri da keşfedebilirsiniz bir [üzerinde etkileşimli incelenmesi C# 6](../tutorials/exploration/csharp-6.yml) öğreticiler bölümünde.</span><span class="sxs-lookup"><span data-stu-id="e78cb-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="e78cb-112">Salt okunur otomatik özellikleri</span><span class="sxs-lookup"><span data-stu-id="e78cb-112">Read-only auto-properties</span></span>

<span data-ttu-id="e78cb-113">*Salt okunur otomatik özelliklerde* değişmez türleri oluşturmak için daha kısa bir söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78cb-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="e78cb-114">Otomatik özelliği yalnızca bir alma erişimcisi ile bildirdiğiniz:</span><span class="sxs-lookup"><span data-stu-id="e78cb-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="e78cb-115">`FirstName` Ve `LastName` özellikleri yalnızca Oluşturucu gövdesinde ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="e78cb-115">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="e78cb-116">Ayarlanmaya çalışılırken `LastName` içinde başka bir yöntem oluşturur bir `CS0200` derleme hatası:</span><span class="sxs-lookup"><span data-stu-id="e78cb-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="e78cb-117">Bu özellik sabit türleri oluşturmak için true dil desteği sağlar ve daha net ve uygun otomatik-özellik söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e78cb-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="e78cb-118">Bu sözdizimi, erişilebilir bir yöntemi kaldırmaz ekleme, eğer ise bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="e78cb-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="e78cb-119">Otomatik-özellik başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="e78cb-119">Auto-property initializers</span></span>

<span data-ttu-id="e78cb-120">*Otomatik-özellik başlatıcıları* başlangıç değeri otomatik özellik için özellik bildiriminde bir parçası olarak bildirmenize.</span><span class="sxs-lookup"><span data-stu-id="e78cb-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="e78cb-121">`Grades` Üyesi olduğu bildirilir başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e78cb-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="e78cb-122">Bu, tam bir kez başlatma gerçekleştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e78cb-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="e78cb-123">Başlatma ile ortak arabirim için depolama ayırmayı excel'dir kolaylaştırarak özellik bildiriminde bir parçasıdır `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e78cb-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="e78cb-124">İfade gövdeli işlev üyeleri</span><span class="sxs-lookup"><span data-stu-id="e78cb-124">Expression-bodied function members</span></span>

<span data-ttu-id="e78cb-125">Yazdığınız birçok tek ifadeleri olabilecek tek deyimler üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="e78cb-126">Bunun yerine bir ifade gövdeli üye yazın.</span><span class="sxs-lookup"><span data-stu-id="e78cb-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="e78cb-127">Bu yöntemler ve salt okunur özellikler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="e78cb-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="e78cb-128">Örneğin, bir geçersiz kılma `ToString()` genellikle iyi bir adaydır:</span><span class="sxs-lookup"><span data-stu-id="e78cb-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="e78cb-129">Salt okunur özellikler için de bu söz dizimini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e78cb-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="e78cb-130">Varolan bir üye ifadesi bodied üyesine değiştirme bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="e78cb-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="e78cb-131">' Using static</span><span class="sxs-lookup"><span data-stu-id="e78cb-131">using static</span></span>

<span data-ttu-id="e78cb-132">*'Using static* geliştirme, tek bir sınıfın statik yöntemleri içeri aktarmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78cb-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="e78cb-133">Kullanmakta olduğunuz sınıfı belirtin:</span><span class="sxs-lookup"><span data-stu-id="e78cb-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="e78cb-134"><xref:System.Math> Herhangi bir örnek yöntem içermiyor.</span><span class="sxs-lookup"><span data-stu-id="e78cb-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="e78cb-135">Ayrıca `using static` bir sınıfın statik yöntemleri statik bir sınıf için içeri aktarma ve örnek yöntemler.</span><span class="sxs-lookup"><span data-stu-id="e78cb-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="e78cb-136">En kullanışlı örneklerden biridir <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="e78cb-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="e78cb-137">Tam nitelikli sınıf adınız kullanmalısınız `System.String` statik olarak using deyimi.</span><span class="sxs-lookup"><span data-stu-id="e78cb-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="e78cb-138">Kullanamazsınız `string` anahtar sözcüğü yerine.</span><span class="sxs-lookup"><span data-stu-id="e78cb-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="e78cb-139">İçeri aktarılan olduğunda bir `static using` deyimi, genişletme yöntemleri olan uzantı metodu çağırma söz dizimi kullanılarak çağrıldığında yalnızca kapsam.</span><span class="sxs-lookup"><span data-stu-id="e78cb-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="e78cb-140">Bir statik yöntem olarak çağrıldığında kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="e78cb-141">Bu, LINQ sorgularında sık sık görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e78cb-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="e78cb-142">İçeri aktararak LINQ desen aktarabilirsiniz <xref:System.Linq.Enumerable>, veya <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="e78cb-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="e78cb-143">Genellikle uzantı metodu çağırma ifadeleri kullanarak genişletme yöntemlerini çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="e78cb-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="e78cb-144">Sınıf adı çağırdığınız bunları nadir durumlarda ekleme söz dizimi çözümler belirsizlik statik yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="e78cb-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="e78cb-145">`static using` Yönergesi, tüm iç içe geçmiş türler de alır.</span><span class="sxs-lookup"><span data-stu-id="e78cb-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="e78cb-146">Nitelik olmadan tüm iç içe geçmiş türler başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78cb-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="e78cb-147">Null koşullu işleçleri</span><span class="sxs-lookup"><span data-stu-id="e78cb-147">Null-conditional operators</span></span>

<span data-ttu-id="e78cb-148">*Null koşullu işleci* null denetimleri çok daha kolay ve akıcı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="e78cb-149">Üye erişimi yerine `.` ile `?.`:</span><span class="sxs-lookup"><span data-stu-id="e78cb-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="e78cb-150">Yukarıdaki örnekte, değişken `first` atanan `null` kişi nesnesi varsa `null`.</span><span class="sxs-lookup"><span data-stu-id="e78cb-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="e78cb-151">Aksi takdirde, değeri atanır `FirstName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e78cb-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="e78cb-152">En önemlisi de `?.` Bu kod satırı oluşturmadığını anlamına gelir bir `NullReferenceException` varsa `person` değişkendir `null`.</span><span class="sxs-lookup"><span data-stu-id="e78cb-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="e78cb-153">Bunun yerine, short-circuits ve döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="e78cb-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="e78cb-154">Null koşullu bir işleç dizi ya da dizin oluşturucu erişimi için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78cb-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="e78cb-155">Değiştirin `[]` ile `?[]` Dizin ifadesi içinde.</span><span class="sxs-lookup"><span data-stu-id="e78cb-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="e78cb-156">Aşağıdaki ifade döndürür bir `string`değerini bakılmaksızın `person`.</span><span class="sxs-lookup"><span data-stu-id="e78cb-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="e78cb-157">Bu yapı ile kullandığınız *null birleşim* varsayılan atamak için işleç değerleri özelliklerinden olduğunda `null`.</span><span class="sxs-lookup"><span data-stu-id="e78cb-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="e78cb-158">Ne zaman ifade short-circuits, `null` tam ifadeyle eşleşecek döndürülen değerin türü.</span><span class="sxs-lookup"><span data-stu-id="e78cb-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="e78cb-159">Ayrıca `?.` koşullu olarak yöntemlerini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="e78cb-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="e78cb-160">Temsilciler (veya olay işleyicileri) güvenli bir şekilde çağrılacak üye işlevleri null koşullu işleci ile en yaygın kullanımı olan olabilecek `null`.</span><span class="sxs-lookup"><span data-stu-id="e78cb-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="e78cb-161">Temsilcinin ararız `Invoke` yöntemi kullanarak `?.` üye erişim işleci.</span><span class="sxs-lookup"><span data-stu-id="e78cb-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="e78cb-162">Bir örnekte gördüğünüz [temsilci desenleri](../delegates-patterns.md#handling-null-delegates) makalesi.</span><span class="sxs-lookup"><span data-stu-id="e78cb-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="e78cb-163">Kurallarına `?.` işleci olun işlecinin sol tarafı yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="e78cb-164">Bu olay işleyicilerini kullanarak aşağıdaki örnekte de dahil olmak üzere birçok deyimleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="e78cb-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="e78cb-165">Sol tarafta yalnızca bir kez değerlendirilir sağlamak da sol tarafındaki yöntem çağrıları dahil olmak üzere herhangi bir ifade kullanmanıza olanak sağlar</span><span class="sxs-lookup"><span data-stu-id="e78cb-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the</span></span> `?.`

## <a name="string-interpolation"></a><span data-ttu-id="e78cb-166">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="e78cb-166">String interpolation</span></span>

<span data-ttu-id="e78cb-167">İle C# 6, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özellik ifadeleri bir dizeye katıştırmak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78cb-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="e78cb-168">Yalnızca dize ile yazdığınızdan `$`ve ifadeler arasında `{` ve `}` sıra sayıları yerine:</span><span class="sxs-lookup"><span data-stu-id="e78cb-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="e78cb-169">Bu örnek için yedek ifadeleri özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e78cb-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="e78cb-170">Herhangi bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78cb-170">You can use any expression.</span></span> <span data-ttu-id="e78cb-171">Örneğin, bir öğrencinin sınıf noktası ortalama ilişkilendirme bir parçası olarak işlem:</span><span class="sxs-lookup"><span data-stu-id="e78cb-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="e78cb-172">Önceki kod satırının değeri biçimlendirir `Grades.Average()` iki ondalık kayan noktalı bir sayı olarak.</span><span class="sxs-lookup"><span data-stu-id="e78cb-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="e78cb-173">Genellikle, belirli bir kültür kullanılarak üretilen dize biçimlendirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="e78cb-174">Bir dize ilişkilendirme tarafından üretilen nesne için örtük olarak dönüştürülebilir olgu kullandığınız <xref:System.FormattableString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e78cb-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e78cb-175"><xref:System.FormattableString> Örneği bileşik biçimlendirme dizesi ve dizeleri için dönüştürme önce ifadeleri değerlendirme sonuçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="e78cb-176">Kullanım <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> kültür biçimlendirme dizesi bir zaman belirtmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e78cb-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="e78cb-177">Aşağıdaki örnek, Almanca (de-DE) kültürü kullanarak bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e78cb-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="e78cb-178">(Varsayılan olarak, Alman kullanılan kültür ',' karakteri ondalık ayırıcısı için kullanır ve '.' karakteri olarak binlik ayırıcı.)</span><span class="sxs-lookup"><span data-stu-id="e78cb-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="e78cb-179">Dize ilişkilendirme ile çalışmaya başlamak için bkz. [dize ilişkilendirme, C# ](../tutorials/exploration/interpolated-strings.yml) etkileşimli öğreticisini [dize ilişkilendirme](../language-reference/tokens/interpolated.md) makalenin ve [dize ilişkilendirme C# ](../tutorials/string-interpolation.md) öğretici.</span><span class="sxs-lookup"><span data-stu-id="e78cb-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="e78cb-180">Özel durum filtreleri</span><span class="sxs-lookup"><span data-stu-id="e78cb-180">Exception filters</span></span>

<span data-ttu-id="e78cb-181">*Özel durum filtreleri* belirli bir catch yan tümcesinin ne zaman uygulanacağını belirleme yan tümceleri olan.</span><span class="sxs-lookup"><span data-stu-id="e78cb-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="e78cb-182">Bir özel durum filtresi için kullanılan ifade olmaması halinde `true`, catch yan tümcesi, bir özel normal işleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="e78cb-183">İfade değerlendirme sonucu `false`, ardından `catch` yan tümcesi atlandı.</span><span class="sxs-lookup"><span data-stu-id="e78cb-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="e78cb-184">Bir kullanım olup olmadığını belirlemek için bir özel durum hakkında bilgileri incelemek için bir `catch` yan tümcesi, özel durumu işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="e78cb-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="e78cb-185">`nameof` İfadesi</span><span class="sxs-lookup"><span data-stu-id="e78cb-185">The `nameof` expression</span></span>

<span data-ttu-id="e78cb-186">`nameof` Bir sembol adı için ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e78cb-186">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="e78cb-187">Her bir değişken, bir özellik veya üye alan adını ihtiyaç duyduğunuzda çalışma araçları almak için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="e78cb-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="e78cb-188">En yaygın birini kullanan için `nameof` bir özel durum nedeniyle bir sembol adını sağlar:</span><span class="sxs-lookup"><span data-stu-id="e78cb-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="e78cb-189">Başka bir uygulama XAML tabanlı uygulamalar ile kullanılır `INotifyPropertyChanged` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="e78cb-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="e78cb-190">Await catch ve Finally bloklarında</span><span class="sxs-lookup"><span data-stu-id="e78cb-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="e78cb-191">C# 5 vardı yerleştirdiğiniz etrafında bazı sınırlamaları `await` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="e78cb-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="e78cb-192">İle C# 6, hemen kullanabileceğiniz `await` içinde `catch` veya `finally` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="e78cb-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="e78cb-193">Bu, genellikle günlük kaydı senaryoları ile kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e78cb-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="e78cb-194">Uygulama ayrıntılarını ekleme `await` içinde destek `catch` ve `finally` yan tümceleri, davranışı davranış eş zamanlı kod için tutarlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e78cb-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="e78cb-195">Ne zaman yürütülen kod içinde bir `catch` veya `finally` yan tümcesi oluşturmaz, yürütme için uygun görünüyor `catch` yan tümcesinde sonraki çevreleyen bloğu.</span><span class="sxs-lookup"><span data-stu-id="e78cb-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="e78cb-196">Geçerli bir özel durum varsa, bu özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="e78cb-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="e78cb-197">Beklenen ifadelerinde ile aynı olur `catch` ve `finally` yan tümceleri: uygun bir `catch` , aranır ve varsa, geçerli özel durumun kaybolur.</span><span class="sxs-lookup"><span data-stu-id="e78cb-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="e78cb-198">Bu, davranıştır yazmak için önerilir nedeni `catch` ve `finally` yan tümceleri dikkatli bir şekilde, yeni özel durumlar önlemek için.</span><span class="sxs-lookup"><span data-stu-id="e78cb-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="e78cb-199">İlişkili koleksiyonlar dizin oluşturucuları kullanarak başlatma</span><span class="sxs-lookup"><span data-stu-id="e78cb-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="e78cb-200">*Dizin başlatıcılar* koleksiyon başlatıcıları dizin kullanımı ile daha tutarlı hale getirmek iki özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="e78cb-201">Önceki sürümlerinde C#, kullanabileceğinizi *koleksiyon başlatıcıları* dizisi stili koleksiyonlarıyla da dahil olmak üzere, <xref:System.Collections.Generic.Dictionary%602>, ile küme ayraçları anahtarı geçici bir çözüm ekleme ve değer çiftlerini:</span><span class="sxs-lookup"><span data-stu-id="e78cb-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="e78cb-202">Bunları ile kullanabileceğiniz <xref:System.Collections.Generic.Dictionary%602> koleksiyonlar ve diğer türleri nerede erişilebilir `Add` yöntemi, birden fazla bağımsız değişken kabul eder.</span><span class="sxs-lookup"><span data-stu-id="e78cb-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="e78cb-203">Yeni söz dizimini kullanarak koleksiyona bir dizin atama destekler:</span><span class="sxs-lookup"><span data-stu-id="e78cb-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="e78cb-204">Bu özellik, ilişkili kapsayıcılar dizisi kapsayıcıları çeşitli sürümleri için yerinde çürütülen için benzer bir sözdizimi kullanılarak başlatılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="e78cb-205">Uzantı `Add` koleksiyon başlatıcıları yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e78cb-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="e78cb-206">Toplama başlatma kolaylaştırır başka bir özellik kullanma yeteneğini olduğu bir *genişletme yöntemi* için `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e78cb-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="e78cb-207">Bu özellik, Visual Basic ile eşlik için eklendi.</span><span class="sxs-lookup"><span data-stu-id="e78cb-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="e78cb-208">Anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip bir yöntemi olan bir özel koleksiyon sınıfı varsa, en yararlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="e78cb-209">Geliştirilmiş aşırı yükleme çözünürlüğü</span><span class="sxs-lookup"><span data-stu-id="e78cb-209">Improved overload resolution</span></span>

<span data-ttu-id="e78cb-210">Son bu özellik, büyük olasılıkla fark olmaz biridir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="e78cb-211">C# derleyicisinin önceki sürümünü içeren lambda ifadeleri belirsiz bazı yöntem çağrıları bulunduğu yapıları vardı.</span><span class="sxs-lookup"><span data-stu-id="e78cb-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="e78cb-212">Bu yöntem göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e78cb-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="e78cb-213">Önceki sürümlerde, C#, yöntem grubu söz dizimini kullanarak bu yöntemini çağırmak başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="e78cb-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="e78cb-214">Önceki derleyici doğru arasında ayrım uygulanamadı `Task.Run(Action)` ve `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="e78cb-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="e78cb-215">Önceki sürümlerinde, bir lambda ifadesi bağımsız değişken olarak kullanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e78cb-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="e78cb-216">C# 6 derleyici doğru belirleyen `Task.Run(Func<Task>())` daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="e78cb-217">Belirleyici derleyici çıkışı</span><span class="sxs-lookup"><span data-stu-id="e78cb-217">Deterministic compiler output</span></span>

<span data-ttu-id="e78cb-218">`-deterministic` Bayt için aynı çıkış derlemesi için aynı kaynak dosyaları art arda gelen derlemesi üretmek için derleyici seçeneği bildirir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="e78cb-219">Varsayılan olarak, her derleme her derleme üzerinde benzersiz bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="e78cb-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="e78cb-220">Derleyici bir zaman damgası ekler ve rastgele sayı bir GUID oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e78cb-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="e78cb-221">İçin-derlemeler arasında tutarlılık sağlamak için çıkış bayt karşılaştırmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e78cb-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="e78cb-222">Daha fazla bilgi için [-belirleyici derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="e78cb-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
