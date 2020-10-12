---
title: 'C# ayrılmış öznitelikleri: Nullable statik analiz'
ms.date: 04/14/2020
description: Bu öznitelikler, null yapılabilir ve null yapılamayan başvuru türleri için daha iyi statik analiz sağlamak üzere derleyici tarafından yorumlanır.
ms.openlocfilehash: 6678cd21de23d4ed391eff089e33939b5adff0fa
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955609"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="1b981-103">Ayrılmış öznitelikler derleyicinin null durum statik analizine katkıda bulunur</span><span class="sxs-lookup"><span data-stu-id="1b981-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="1b981-104">Null yapılabilir bir bağlamda, derleyici, tüm başvuru türü değişkenlerinin null durumunu tespit etmek üzere kodun statik analizini yapar:</span><span class="sxs-lookup"><span data-stu-id="1b981-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="1b981-105">*null değil*: statik analiz bir değişkene null olmayan bir değer atandığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1b981-105">*not null*: Static analysis determines that a variable is assigned a non-null value.</span></span>
- <span data-ttu-id="1b981-106">*null olabilir*: statik analiz, bir değişkene null olmayan bir değer atandığını belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="1b981-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="1b981-107">API 'lerinizin semantiği hakkında bilgi sağlayan bir dizi öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b981-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="1b981-108">Bu bilgiler derleyicinin statik analiz gerçekleştirmesini ve bir değişkenin ne zaman null kalmadığını belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1b981-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="1b981-109">Bu makalede, bu özniteliklerin her biri ve nasıl kullanılacağı hakkında kısa bir açıklama sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b981-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="1b981-110">Tüm örneklerde C# 8,0 veya üzeri varsayılır ve kod null yapılabilir bir bağlamda yer almıyor.</span><span class="sxs-lookup"><span data-stu-id="1b981-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="1b981-111">Tanıdık bir örnekle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1b981-111">Let's start with a familiar example.</span></span> <span data-ttu-id="1b981-112">Kitaplığınızın bir kaynak dizesini almak için aşağıdaki API 'ye sahip olduğunu düşünün:</span><span class="sxs-lookup"><span data-stu-id="1b981-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="1b981-113">Yukarıdaki örnek, `Try*` .net 'teki tanıdık olan bir model izler.</span><span class="sxs-lookup"><span data-stu-id="1b981-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="1b981-114">Bu API için iki başvuru bağımsız değişkeni vardır: `key` ve `message` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1b981-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="1b981-115">Bu API, bu bağımsız değişkenlerin nulldurumuyla ilgili aşağıdaki kurallara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1b981-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="1b981-116">Çağıranlar `null` için bağımsız değişken olarak geçmemelidir `key` .</span><span class="sxs-lookup"><span data-stu-id="1b981-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="1b981-117">Çağıranlar, değeri bağımsız değişkeni olan bir değişken geçirebilir `null` `message` .</span><span class="sxs-lookup"><span data-stu-id="1b981-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="1b981-118">`TryGetMessage`Yöntemi döndürürse `true` , değeri `message` null değildir.</span><span class="sxs-lookup"><span data-stu-id="1b981-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="1b981-119">Dönüş değeri `false,` `message` (ve null durumu) değeri null ise.</span><span class="sxs-lookup"><span data-stu-id="1b981-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="1b981-120">Kuralı `key` değişken türüne göre ifade edilebilir: `key` null yapılamayan bir başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b981-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="1b981-121">`message`Parametresi daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="1b981-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="1b981-122">`null`Bağımsız değişken olarak izin verir, ancak başarıyı, bu `out` bağımsız değişkenin null olmadığını garanti eder.</span><span class="sxs-lookup"><span data-stu-id="1b981-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="1b981-123">Bu senaryolar için beklentileri betimleyen daha zengin bir sözlük gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b981-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="1b981-124">Değişkenlerin null durumu hakkında ek bilgileri ifade etmek için çeşitli öznitelikler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b981-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="1b981-125">C# 8 ' den önce yazdığınız tüm kod null yapılabilir başvuru türleri olarak *null zorunluluvou*idi.</span><span class="sxs-lookup"><span data-stu-id="1b981-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="1b981-126">Yani herhangi bir başvuru türü değişkeni null olabilir, ancak null denetimleri gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1b981-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="1b981-127">Kodunuz *Nullable olarak farkında*olduktan sonra bu kurallar değişir.</span><span class="sxs-lookup"><span data-stu-id="1b981-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="1b981-128">Başvuru türleri asla `null` değer olmamalı ve null yapılabilir başvuru türleri `null` başvurulmadan önce denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1b981-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="1b981-129">API 'si senaryosuyla gördüğünüz gibi API 'lerinizin kuralları büyük olasılıkla daha karmaşıktır `TryGetValue` .</span><span class="sxs-lookup"><span data-stu-id="1b981-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="1b981-130">API 'lerinizin birçoğu, değişkenlerin ne zaman veya ne zaman oluşturulabileceğine ilişkin daha karmaşık kurallara sahiptir `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="1b981-131">Bu durumlarda, bu kuralları ifade etmek için aşağıdaki özniteliklerden birini kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="1b981-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="1b981-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="1b981-133">[Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b981-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="1b981-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="1b981-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.</span><span class="sxs-lookup"><span data-stu-id="1b981-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="1b981-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir `bool` .</span><span class="sxs-lookup"><span data-stu-id="1b981-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="1b981-137">[Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılabilir giriş bağımsız değişkeni null olmaz `bool` .</span><span class="sxs-lookup"><span data-stu-id="1b981-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="1b981-138">[Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin bağımsız değişkeni null değilse, dönüş değeri null olamaz.</span><span class="sxs-lookup"><span data-stu-id="1b981-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="1b981-139">Hayır: bir yöntem hiçbir [şekilde döndürmez.](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)</span><span class="sxs-lookup"><span data-stu-id="1b981-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="1b981-140">Diğer bir deyişle, her zaman bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b981-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="1b981-141">Yok [: ilişkili](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute) `bool` parametre belirtilen değere sahipse, bu yöntem hiçbir şekilde döndürmez.</span><span class="sxs-lookup"><span data-stu-id="1b981-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="1b981-142">Yukarıdaki açıklamalar, her bir özniteliğin yaptığı işe yönelik hızlı bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="1b981-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="1b981-143">Aşağıdaki her bölümde davranışı ve anlamı daha kapsamlı bir şekilde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1b981-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="1b981-144">Bu özniteliklerin eklenmesi, derleyiciye API 'nizin kuralları hakkında daha fazla bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="1b981-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="1b981-145">Kodu çağırma özelliği, null yapılabilir etkin bir bağlamda derlenirse, derleyici bu kuralları ihlal ettiklerinde çağıranları uyarır.</span><span class="sxs-lookup"><span data-stu-id="1b981-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="1b981-146">Bu öznitelikler, uygulamanızda ek denetimleri etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="1b981-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="1b981-147">Önkoşulları belirtin: `AllowNull` ve `DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="1b981-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="1b981-148">`null`Makul bir varsayılan değere sahip olduğu için hiçbir süre döndürülmediği bir okuma/yazma özelliği düşünün.</span><span class="sxs-lookup"><span data-stu-id="1b981-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="1b981-149">Çağıranlar `null` , bu varsayılan değere ayarlarken ayarlanan erişimciye geçer.</span><span class="sxs-lookup"><span data-stu-id="1b981-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="1b981-150">Örneğin, bir sohbet odasında ekran adı isteyen bir mesajlaşma sistemi düşünün.</span><span class="sxs-lookup"><span data-stu-id="1b981-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="1b981-151">Hiçbiri sağlanmazsa, sistem rastgele bir ad üretir:</span><span class="sxs-lookup"><span data-stu-id="1b981-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName;
```

<span data-ttu-id="1b981-152">Önceki kodu null olabilir bir zorunluluvou bağlamında derlerken her şey iyidir.</span><span class="sxs-lookup"><span data-stu-id="1b981-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="1b981-153">Null yapılabilir başvuru türlerini etkinleştirdikten sonra, `ScreenName` özelliği null yapılamayan bir başvuru haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1b981-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="1b981-154">Bu, erişimci için doğrudur `get` : hiçbir şekilde döndürmez `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="1b981-155">Çağıranlar için döndürülen özelliği denetmek zorunda değildir `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="1b981-156">Ancak şimdi özelliği `null` bir uyarı oluşturacak şekilde ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="1b981-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="1b981-157">Bu tür bir kodu desteklemeye devam etmek için, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi özniteliğini özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1b981-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName = GenerateRandomScreenName();
```

<span data-ttu-id="1b981-158">Bu `using` <xref:System.Diagnostics.CodeAnalysis> makalede ele alınan bu ve diğer özniteliklerin kullanılması için bir yönerge eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="1b981-159">Özniteliği, erişimciye değil, özelliğine uygulanır `set` .</span><span class="sxs-lookup"><span data-stu-id="1b981-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="1b981-160">`AllowNull`Öznitelik, *ön koşulları*belirtir ve yalnızca girişler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1b981-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="1b981-161">`get`Erişimcinin dönüş değeri var, ancak giriş bağımsız değişkeni yok.</span><span class="sxs-lookup"><span data-stu-id="1b981-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="1b981-162">Bu nedenle, `AllowNull` öznitelik yalnızca erişimci için geçerlidir `set` .</span><span class="sxs-lookup"><span data-stu-id="1b981-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="1b981-163">Yukarıdaki örnekte, `AllowNull` bir bağımsız değişkende özniteliği eklenirken ne aranacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1b981-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="1b981-164">Bu değişken için genel sözleşme bunun olmaması `null` , bu nedenle null atanamaz bir başvuru türü istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b981-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="1b981-165">Giriş değişkeninin en yaygın kullanımları olmadıkları halde olması için senaryolar vardır `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="1b981-166">Çoğu kez bu özniteliğe özellikler, veya `in` , `out` ve bağımsız değişkenler için ihtiyaç duyarsınız `ref` .</span><span class="sxs-lookup"><span data-stu-id="1b981-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="1b981-167">`AllowNull`Özniteliği genellikle null olmayan ancak önkoşul olarak izin vermeniz gereken en iyi seçenektir `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="1b981-168">Kullanma senaryolarıyla karşıtlık `DisallowNull` : Bu özniteliği, null atanabilir bir başvuru türünün giriş değişkeninin olmaması gerektiğini belirtmek için kullanırsınız `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="1b981-169">`null`Varsayılan değer olan, ancak istemciler yalnızca null olmayan bir değere ayarlayabileceği bir özelliği düşünün.</span><span class="sxs-lookup"><span data-stu-id="1b981-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="1b981-170">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="1b981-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="1b981-171">Önceki kod, tasarımınızı ifade etmenin en iyi yoludur `ReviewComment` `null` , ancak olarak ayarlanamaz `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="1b981-172">Bu kod null yapılabilir olduğunda, bu kavramı kullanarak çağıranlara daha net bir şekilde ifade edebilirsiniz <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="1b981-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="1b981-173">Null yapılabilir bir bağlamda, `ReviewComment` `get` erişimci varsayılan değerini döndürebilir `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="1b981-174">Derleyici, erişim öncesinde denetlenmesi gerektiğini uyarır.</span><span class="sxs-lookup"><span data-stu-id="1b981-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="1b981-175">Buna ek olarak, arayanlara açıkça ayarlanmaması durumunda bile arayanlara uyarır `null` `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="1b981-176">`DisallowNull`Öznitelik bir *ön koşul*da belirtir, `get` erişimciyi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="1b981-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="1b981-177">`DisallowNull`Aşağıdaki özellikleri gözlemlediğiniz zaman özniteliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="1b981-178">Değişken `null` , genellikle ilk örneği oluşturulduğunda temel senaryolarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="1b981-179">Değişken açıkça olarak ayarlanmamalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="1b981-180">Bu durumlar, başlangıçta *null yükümlülüğü*oluşturulan kodda ortaktır.</span><span class="sxs-lookup"><span data-stu-id="1b981-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="1b981-181">Nesne özelliklerinin iki ayrı başlatma işlemi olarak ayarlanmış olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="1b981-182">Bazı özelliklerin bazı zaman uyumsuz çalışma tamamlandıktan sonra ayarlanmış olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="1b981-183">`AllowNull`Ve `DisallowNull` öznitelikleri, değişkenlerde önkoşulların Bu değişkenlerde null yapılabilir ek açıklamalarıyla eşleşmeyebilir belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1b981-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="1b981-184">Bunlar, API 'nizin özellikleri hakkında daha ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b981-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="1b981-185">Bu ek bilgiler, arayanların API 'nizi doğru şekilde kullanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1b981-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="1b981-186">Aşağıdaki öznitelikleri kullanarak önkoşulları belirtdüğünü unutmayın:</span><span class="sxs-lookup"><span data-stu-id="1b981-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="1b981-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="1b981-188">[Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b981-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="1b981-189">Son koşulları belirtin: `MaybeNull` ve `NotNull`</span><span class="sxs-lookup"><span data-stu-id="1b981-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="1b981-190">Aşağıdaki imzaya sahip bir yönteminiz olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="1b981-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="1b981-191">Aranan ad bulunamadığı zaman döndürmek için bunun gibi bir yöntem yazmış oluk `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="1b981-192">`null`Açıkça kaydın bulunamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b981-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="1b981-193">Bu örnekte, büyük olasılıkla ' dan ' a dönüş türünü değiştirirsiniz `Customer` `Customer?` .</span><span class="sxs-lookup"><span data-stu-id="1b981-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="1b981-194">Dönüş değerinin null yapılabilir bir başvuru türü olarak bildirilmesi, bu API 'nin amacını açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b981-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="1b981-195">[Genel tanımlar ve null değer verilebilme](../../nullable-migration-strategies.md#generic-definitions-and-nullability) kapsamında, tekniği genel yöntemlerle çalışmayan nedenler için.</span><span class="sxs-lookup"><span data-stu-id="1b981-195">For reasons covered under [Generic definitions and nullability](../../nullable-migration-strategies.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="1b981-196">Benzer bir kalıbı izleyen genel bir yönteminiz olabilir:</span><span class="sxs-lookup"><span data-stu-id="1b981-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

<span data-ttu-id="1b981-197">Dönüş değerinin olduğunu belirtemezsiniz `T?` .</span><span class="sxs-lookup"><span data-stu-id="1b981-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="1b981-198">Yöntemi, `null` Aranan öğe bulunamadığında döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b981-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="1b981-199">Bir dönüş türü bildirebileceğinizden `T?` , `MaybeNull` ek açıklamayı Yöntem döndürecek şekilde eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

<span data-ttu-id="1b981-200">Yukarıdaki kod, arayanlara sözleşmenin null yapılamayan bir tür gösterdiği anlamına gelir, ancak *dönüş değeri gerçekten null olabilir.*</span><span class="sxs-lookup"><span data-stu-id="1b981-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="1b981-201">`MaybeNull`API 'niz null yapılamayan bir tür olması gerektiği zaman, genellikle genel bir tür parametresi olması durumunda özniteliği kullanın, ancak döndürülecek örnekler olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="1b981-202">Bir dönüş değeri veya `out` ya da `ref` bağımsız değişkenin tür, null değer atanabilir bir başvuru türü olmasına rağmen null olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b981-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="1b981-203">Bir dizinin birçok öğe tutabilecek kadar büyük olmasını sağlayan bir yöntemi düşünün.</span><span class="sxs-lookup"><span data-stu-id="1b981-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="1b981-204">Giriş bağımsız değişkeninin kapasitesi yoksa, yordam yeni bir dizi ayırır ve var olan tüm öğeleri buna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="1b981-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="1b981-205">Giriş bağımsız değişkeni ise `null` , yordam yeni depolama alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="1b981-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="1b981-206">Yeterli kapasite varsa, yordam hiçbir şey yapmaz:</span><span class="sxs-lookup"><span data-stu-id="1b981-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="1b981-207">Bu yordamı aşağıdaki şekilde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="1b981-208">Null başvuru türlerini etkinleştirdikten sonra, önceki kodun uyarı olmadan derlendiğinden emin olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="1b981-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="1b981-209">Yöntemi döndürüldüğünde `storage` bağımsız değişkenin null olmaması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="1b981-210">Ancak, `EnsureCapacity` bir null başvurusuyla çağırmak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="1b981-211">`storage`Null yapılabilir bir başvuru türü yapabilir ve `NotNull` parametre bildirimine son koşulu ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull] ref T[]? storage, int size)
```

<span data-ttu-id="1b981-212">Yukarıdaki kod, mevcut sözleşmeyi açık bir şekilde ifade eder: çağıranlar değer ile bir değişken geçirebilir `null` , ancak dönüş değeri hiçbir şekilde null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b981-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="1b981-213">`NotNull`Özniteliği ve bağımsız değişken olarak geçirilebilecek bağımsız değişkenler için en yararlı seçenektir `ref` `out` `null` , ancak yöntemin döndürdüğü zaman değişkenin null olmaması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="1b981-214">Aşağıdaki öznitelikleri kullanarak koşulsuz Sonkoşulları belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="1b981-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="1b981-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.</span><span class="sxs-lookup"><span data-stu-id="1b981-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="1b981-217">Koşullu koşulları belirtin: `NotNullWhen` , `MaybeNullWhen` , ve `NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="1b981-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="1b981-218">Büyük olasılıkla yöntemiyle ilgili bilgi sahibisiniz `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1b981-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="1b981-219">Bu yöntem `true` , bağımsız değişken null veya boş bir dize olduğunda döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b981-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="1b981-220">Bu bir null denetim biçimidir: çağıranların null olması gerekmez; yöntemin döndürdüğü bağımsız değişkeni kontrol edin `false` .</span><span class="sxs-lookup"><span data-stu-id="1b981-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="1b981-221">Bu null yapılabilir bir yöntemi gibi bir yöntem oluşturmak için bağımsız değişkenini null atanabilir bir başvuru türüne ayarlarsınız ve `NotNullWhen` özniteliği ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)] string? value);
```

<span data-ttu-id="1b981-222">Bu, derleyicinin dönüş değerinin null denetimli olması gereken herhangi bir kod olduğunu bildirir `false` .</span><span class="sxs-lookup"><span data-stu-id="1b981-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="1b981-223">Özniteliğin eklenmesi, derleyicinin statik analizini, `IsNullOrEmpty` gerekli null denetimini yerine getiren bildirir: döndüğünde `false` , giriş bağımsız değişkeni değildir `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="1b981-224"><xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>Yöntemi, .NET Core 3,0 için yukarıda gösterildiği gibi açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="1b981-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="1b981-225">Kod tabanınızda, null değerler için nesnelerin durumunu kontrol eden benzer yöntemlere sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b981-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="1b981-226">Derleyici özel null denetim yöntemlerini tanımaz ve ek açıklamaları kendiniz eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b981-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="1b981-227">Özniteliğini eklediğinizde, derleyicinin statik analizi, sınanan değişkenin null olarak işaretli olduğunu bilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="1b981-228">Bu öznitelikler için başka bir kullanım de modeldir `Try*` .</span><span class="sxs-lookup"><span data-stu-id="1b981-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="1b981-229">Ve değişkenleri için Sonkoşulları, `ref` `out` dönüş değeri üzerinden iletilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="1b981-230">Daha önce gösterilen bu yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1b981-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="1b981-231">Yukarıdaki yöntem tipik bir .NET deyimidir OM: dönüş değeri, `message` bulunan değer olarak ayarlanmış olup olmadığını veya hiçbir ileti bulunamazsa varsayılan değere ayarlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b981-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="1b981-232">Yöntemi döndürürse `true` , değeri `message` null değildir; Aksi takdirde, yöntemi `message` null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1b981-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="1b981-233">Özniteliği kullanarak bu deyimden iletişim kurabilirsiniz `NotNullWhen` .</span><span class="sxs-lookup"><span data-stu-id="1b981-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="1b981-234">Null yapılabilir başvuru türleri için imzayı güncelleştirdiğinizde `message` bir `string?` özniteliği oluşturun ve ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1b981-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="1b981-235">Önceki örnekte, değeri `message` döndüğünde null değil olarak bilinir `TryGetMessage` `true` .</span><span class="sxs-lookup"><span data-stu-id="1b981-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="1b981-236">Kod tabanınızda benzer yöntemlere aynı şekilde açıklama eklenmelidir: bağımsız değişkenler olabilir `null` ve yöntem döndürüldüğünde null olmadığı bilinmektedir `true` .</span><span class="sxs-lookup"><span data-stu-id="1b981-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="1b981-237">Ayrıca ihtiyacınız olabilecek bir son öznitelik vardır.</span><span class="sxs-lookup"><span data-stu-id="1b981-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="1b981-238">Bazen bir dönüş değerinin null durumu, bir veya daha fazla giriş bağımsız değişkenlerinin null durumuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1b981-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="1b981-239">Bu yöntemler, belirli giriş bağımsız değişkenleri olmadığında null olmayan bir değer döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="1b981-240">Bu yöntemlere doğru şekilde açıklama eklemek için özniteliğini kullanırsınız `NotNullIfNotNull` .</span><span class="sxs-lookup"><span data-stu-id="1b981-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="1b981-241">Aşağıdaki yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1b981-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="1b981-242">`url`Bağımsız değişken null değilse, çıktı değildir `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="1b981-243">Null yapılabilir başvurular etkinleştirildikten sonra, bu imza doğru şekilde çalışarak API 'niz hiçbir şekilde null girişi kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="1b981-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="1b981-244">Ancak, giriş null ise, dönüş değeri de null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="1b981-245">Bu nedenle, imzayı aşağıdaki kodla değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="1b981-246">Bu da çalışır, ancak arayanlara çok fazla denetim uygulamak için zorlayacaktır `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="1b981-247">Sözleşmenin dönüş değeri `null` yalnızca giriş bağımsız değişkeni olduğunda olacaktır `url` `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="1b981-248">Bu sözleşmeyi ifade etmek için, aşağıdaki kodda gösterildiği gibi bu yönteme açıklama ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="1b981-249">Dönüş değerine ve bağımsız değişkenine, her iki durumda da olabilecek şekilde açıklama eklenmiş `?` `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="1b981-250">Özniteliği, bağımsız değişken olmadığında dönüş değerinin null olmaması gerektiğini açıklığa kavuşturulur `url` `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="1b981-251">Şu öznitelikleri kullanarak koşullu Sonkoşulları belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="1b981-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir `bool` .</span><span class="sxs-lookup"><span data-stu-id="1b981-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="1b981-253">[Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılabilir giriş bağımsız değişkeni null olmaz `bool` .</span><span class="sxs-lookup"><span data-stu-id="1b981-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="1b981-254">[Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.</span><span class="sxs-lookup"><span data-stu-id="1b981-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="1b981-255">Erişilemeyen kodu doğrula</span><span class="sxs-lookup"><span data-stu-id="1b981-255">Verify unreachable code</span></span>

<span data-ttu-id="1b981-256">Bazı yöntemler, genellikle özel durum yardımcıları veya diğer yardımcı yöntemler, her zaman bir özel durum oluşturarak çıkış yapılır.</span><span class="sxs-lookup"><span data-stu-id="1b981-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="1b981-257">Ya da bir yardımcı, Boole bağımsız değişkeninin değerine göre bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="1b981-258">İlk durumda, `DoesNotReturn` metot bildirimine özniteliğini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b981-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="1b981-259">Derleyici üç şekilde size yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1b981-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="1b981-260">İlk olarak, yöntemin bir özel durum oluşturmadan çıkabileceği bir yol varsa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="1b981-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="1b981-261">İkinci olarak, derleyici ilgili yönteme bir çağrıdan sonra, uygun bir yan tümcesine *ulaşılana*kadar herhangi bir kodu işaretler `catch` .</span><span class="sxs-lookup"><span data-stu-id="1b981-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="1b981-262">Üçüncü olarak, erişilemeyen kod hiçbir null durumu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="1b981-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="1b981-263">Şu yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1b981-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
    throw new InvalidOperationException();
}

public void SetState(object containedField)
{
    if (!isInitialized)
    {
        FailFast();
    }

    // unreachable code:
    _field = containedField;
}
```

<span data-ttu-id="1b981-264">İkinci durumda, `DoesNotReturnIf` özniteliğini yönteminin bir Boolean parametresine eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="1b981-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="1b981-265">Önceki örneği aşağıdaki gibi değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b981-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)] bool isValid)
{
    if (!isValid)
    {
        throw new InvalidOperationException();
    }
}

public void SetState(object containedField)
{
    FailFast(isInitialized);

    // unreachable code when "isInitialized" is false:
    _field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="1b981-266">Özet</span><span class="sxs-lookup"><span data-stu-id="1b981-266">Summary</span></span>

[!INCLUDE [C# version alert](../../includes/csharp-version-alert.md)]

<span data-ttu-id="1b981-267">Null yapılabilir başvuru türleri eklemek, olabilecek değişkenlere yönelik API beklentilerinizi tanımlayan bir başlangıç sözlüğü sağlar `null` .</span><span class="sxs-lookup"><span data-stu-id="1b981-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="1b981-268">Ek öznitelikler, değişkenlerin null durumunu ön koşullar ve Postconditions olarak tanımlamaya yönelik daha zengin bir sözlük sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b981-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="1b981-269">Bu öznitelikler beklentilerinizi daha net bir şekilde anlatır ve API 'lerinizi kullanan geliştiriciler için daha iyi bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b981-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="1b981-270">Bir null yapılabilir bağlam için kitaplıkları güncelleştirdiğinizde, API 'lerinizi kullanıcılarına doğru kullanım için bu öznitelikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1b981-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="1b981-271">Bu öznitelikler, giriş bağımsız değişkenlerinin ve dönüş değerlerinin Null durumunu tam olarak açıklamanıza yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="1b981-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="1b981-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="1b981-273">[Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b981-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="1b981-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b981-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="1b981-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.</span><span class="sxs-lookup"><span data-stu-id="1b981-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="1b981-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir `bool` .</span><span class="sxs-lookup"><span data-stu-id="1b981-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="1b981-277">[Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılabilir giriş bağımsız değişkeni null olmaz `bool` .</span><span class="sxs-lookup"><span data-stu-id="1b981-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="1b981-278">[Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.</span><span class="sxs-lookup"><span data-stu-id="1b981-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="1b981-279">Hayır: bir yöntem hiçbir [şekilde döndürmez.](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)</span><span class="sxs-lookup"><span data-stu-id="1b981-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="1b981-280">Diğer bir deyişle, her zaman bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b981-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="1b981-281">Yok [: ilişkili](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute) `bool` parametre belirtilen değere sahipse, bu yöntem hiçbir şekilde döndürmez.</span><span class="sxs-lookup"><span data-stu-id="1b981-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
