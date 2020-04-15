---
title: 'C# Ayrılmış öznitelikler: Nullable statik çözümleme'
ms.date: 04/14/2020
description: Bu öznitelikler, nullable ve nullable referans türleri için daha iyi statik çözümleme sağlamak için derleyici tarafından yorumlanır.
ms.openlocfilehash: 0315d78db7517541efe578d8675c0f2fe45f5aea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389865"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="96d6c-103">Ayrılmış öznitelikler derleyicinin null durum statik analizine katkıda bulunur</span><span class="sxs-lookup"><span data-stu-id="96d6c-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="96d6c-104">Nullable bağlamında, derleyici tüm başvuru türü değişkenlerinin null durumunu belirlemek için kodun statik çözümlemesi gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="96d6c-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="96d6c-105">*not null*: Değişkenin null olmayan bir değere atandığını belirleyen statik analiz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-105">*not null*: Static analysis determined that the variable is assigned to a non-null value.</span></span>
- <span data-ttu-id="96d6c-106">*belki null*: Statik çözümleme bir değişkene null olmayan bir değer atandığını belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="96d6c-107">API'lerinizin anlambilimi hakkında derleyiciye bilgi sağlayan bir dizi öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="96d6c-108">Bu bilgiler derleyicinin statik çözümleme yapmasına ve bir değişkenin null ne zaman olmadığını belirlemesi için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="96d6c-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="96d6c-109">Bu makalede, bu özniteliklerin her birinin kısa bir açıklamasını ve bunların nasıl kullanılacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="96d6c-110">Tüm örnekler C# 8.0 veya daha yeni varsayar ve kod nullable bağlamında.</span><span class="sxs-lookup"><span data-stu-id="96d6c-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="96d6c-111">Tanıdık bir örnekle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="96d6c-111">Let's start with a familiar example.</span></span> <span data-ttu-id="96d6c-112">Kitaplığınızın kaynak dizesini almak için aşağıdaki API'ye sahip olduğunu düşünün:</span><span class="sxs-lookup"><span data-stu-id="96d6c-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="96d6c-113">Önceki örnek .NET'teki tanıdık `Try*` deseni izler.</span><span class="sxs-lookup"><span data-stu-id="96d6c-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="96d6c-114">Bu API için iki başvuru `key` bağımsız `message` değişkeni vardır: ve parametre.</span><span class="sxs-lookup"><span data-stu-id="96d6c-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="96d6c-115">Bu API, bu bağımsız değişkenlerin nullness ile ilgili aşağıdaki kurallara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="96d6c-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="96d6c-116">Arayanlar için `key`argüman `null` olarak geçmemelidir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="96d6c-117">Arayanlar, değeri bağımsız değişken `null` olarak olan `message`bir değişkeni geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="96d6c-118">`TryGetMessage` Yöntem dönerse, `true`değeri null `message` değildir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="96d6c-119">İade değeri `false,` `message` (ve null durumu) değeri ise null.</span><span class="sxs-lookup"><span data-stu-id="96d6c-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="96d6c-120">Kural değişken `key` türü ile ifade edilebilir: `key` nullable olmayan bir başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="96d6c-121">Parametre `message` daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="96d6c-122">Bu `null` argüman olarak izin verir, ama garanti, `out` başarı, bu argüman null değildir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="96d6c-123">Bu senaryolar için, beklentileri açıklamak için daha zengin bir kelime gerekir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="96d6c-124">Değişkenlerin null durumu hakkında ek bilgi ifade etmek için çeşitli öznitelikler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="96d6c-125">C# 8'den önce yazdığınız tüm kodlar nullable referans türlerini tanıttı *null habersiz*oldu.</span><span class="sxs-lookup"><span data-stu-id="96d6c-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="96d6c-126">Bu, herhangi bir başvuru türü değişkeninin null olabileceği, ancak null denetimlerin gerekli olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="96d6c-127">Bir kez kodunuzu *farkında geçersiz*olduğunda, bu kurallar değişir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="96d6c-128">Referans türleri hiçbir `null` zaman değer olmamalıdır ve geçersiz başvuru `null` türleri referans gösterilmeden önce karşı denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="96d6c-129">API senaryoda gördüğünüz gibi, API'lerinizin `TryGetValue` kuralları büyük olasılıkla daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="96d6c-130">API'lerinizin çoğu, değişkenlerin ne zaman olabilir veya `null`olamaz için daha karmaşık kurallara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="96d6c-131">Bu gibi durumlarda, bu kuralları ifade etmek için aşağıdaki özniteliklerden birini kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="96d6c-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="96d6c-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Nullolmayan bir giriş bağımsız değişkeni null olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="96d6c-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Nullable giriş bağımsız değişkeni asla null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="96d6c-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Nullable olmayan bir iade değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="96d6c-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable iade değeri asla null olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="96d6c-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable olmayan bir giriş bağımsız değişkeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="96d6c-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable giriş bağımsız değişkeni null olmaz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="96d6c-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin bağımsız değişkeni null değilse, iade değeri null değildir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="96d6c-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Bir yöntem asla dönmez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="96d6c-140">Başka bir deyişle, her zaman bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="96d6c-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): İlişkili `bool` parametre belirtilen değere sahipse bu yöntem asla dönmez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="96d6c-142">Önceki açıklamalar, her öznitelik ne hızlı bir başvuru vardır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="96d6c-143">Aşağıdaki her bölümde davranış ve anlamı daha ayrıntılı olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="96d6c-144">Bu özniteliklerin eklenmesi derleyiciye API'nizin kuralları hakkında daha fazla bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="96d6c-145">Arama kodu boşetkinleştirilebilir bir bağlamda derlendiğinde, derleyici bu kuralları ihlal ettiklerinde arayanları uyarır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="96d6c-146">Bu öznitelikler, uygulamanız üzerinde ek denetimler etkinleştirmiyor.</span><span class="sxs-lookup"><span data-stu-id="96d6c-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="96d6c-147">Ön koşulları `AllowNull` belirtin: ve`DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="96d6c-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="96d6c-148">Makul bir varsayılan değere `null` sahip olduğu için asla geri dönmeyecek bir okuma/yazma özelliği düşünün.</span><span class="sxs-lookup"><span data-stu-id="96d6c-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="96d6c-149">Arayanlar, `null` bu varsayılan değere ayarlarken ayarlanan erişime geçer.</span><span class="sxs-lookup"><span data-stu-id="96d6c-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="96d6c-150">Örneğin, sohbet odasında ekran adı isteyen bir ileti sistemi düşünün.</span><span class="sxs-lookup"><span data-stu-id="96d6c-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="96d6c-151">Hiçbiri sağlanmazsa, sistem rasgele bir ad oluşturur:</span><span class="sxs-lookup"><span data-stu-id="96d6c-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="96d6c-152">Önceki kodu boş bir şekilde boş bir bağlamda derlediğinizde, her şey yolundadır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="96d6c-153">Nullable başvuru türlerini etkinleştirdikten sonra, `ScreenName` özellik nullable olmayan bir başvuru olur.</span><span class="sxs-lookup"><span data-stu-id="96d6c-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="96d6c-154">Bu `get` erişimci için doğru: asla `null`geri dönmez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="96d6c-155">Arayanların döndürülen özelliği kontrol etmeleri `null`gerekmez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="96d6c-156">Ama şimdi bir `null` uyarı oluşturmak için özellik ayarı.</span><span class="sxs-lookup"><span data-stu-id="96d6c-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="96d6c-157">Bu kod türünü desteklemeye devam etmek için, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi özelliğe özniteliği eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="96d6c-158">Bu ve bu `using` makalede <xref:System.Diagnostics.CodeAnalysis> tartışılan diğer öznitelikleri kullanmak için bir yönerge eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="96d6c-159">`set` Öznitelik, erişime erişime değil, özelliğe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="96d6c-160">Öznitelik `AllowNull` *ön koşulları*belirtir ve yalnızca girişler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="96d6c-161">Erişime erişimin `get` bir iade değeri vardır, ancak giriş bağımsız değişkeni yoktur.</span><span class="sxs-lookup"><span data-stu-id="96d6c-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="96d6c-162">Bu nedenle, `AllowNull` öznitelik yalnızca `set` erişimci için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="96d6c-163">Önceki örnek, bir bağımsız değişkene `AllowNull` öznitelik eklerken nelere bakMası gerektiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="96d6c-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="96d6c-164">Bu değişken için genel sözleşme olmamalıdır `null`, bu yüzden geçersiz bir başvuru türü istiyorum.</span><span class="sxs-lookup"><span data-stu-id="96d6c-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="96d6c-165">Giriş değişkeninin en yaygın kullanım `null`olmasa da olması için senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="96d6c-166">Çoğu zaman özellikleri veya `in`, , `out`ve `ref` bağımsız değişkenler için bu öznitelik gerekir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="96d6c-167">Öznitelik, `AllowNull` bir değişken genellikle null olmayan en iyi seçimdir, `null` ancak bir ön koşul olarak izin vermek gerekir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="96d6c-168">Kontrast bu kullanım `DisallowNull`senaryoları ile : Bu özniteliği, nullable başvuru türünden bir giriş `null`değişkeninin olmaması gerektiğini belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="96d6c-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="96d6c-169">Varsayılan değerin `null` olduğu bir özellik düşünün, ancak istemciler onu yalnızca null olmayan bir değere ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="96d6c-170">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="96d6c-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="96d6c-171">Önceki kod, tasarımınızı `ReviewComment` ifade etmenin en iyi `null`yoludur, ancak bu kod `null`.</span><span class="sxs-lookup"><span data-stu-id="96d6c-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="96d6c-172">Bu kod geçersiz kılınabilir farkında olduğunda, bu kavramı arayanlara <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>şu anlama gelenlere daha net bir şekilde ifade edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="96d6c-173">Nullable bağlamında, `ReviewComment` `get` erişimci varsayılan değerini `null`döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="96d6c-174">Derleyici, erişimden önce denetlemesi gerektiği konusunda uyarır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="96d6c-175">Ayrıca, arayanlar, olsa `null`bile, arayanlar açıkça ayarlamak gerektiğini uyarır . `null`</span><span class="sxs-lookup"><span data-stu-id="96d6c-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="96d6c-176">Öznitelik `DisallowNull` de bir *ön koşul*belirtir, bu `get` erişimci etkilemez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="96d6c-177">Aşağıdakiler `DisallowNull` hakkında şu özellikleri gözlemlediğinizde özniteliği kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="96d6c-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="96d6c-178">Değişken, genellikle `null` ilk instantiated çekirdek senaryolarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="96d6c-179">Değişken açıkça ' olarak `null`ayarlanamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="96d6c-180">Bu durumlar aslında *geçersiz*habersiz kod yaygındır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="96d6c-181">Nesne özellikleri iki farklı başlatma işlemlerinde ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="96d6c-182">Bazı özellikler yalnızca bazı eşzamanlı çalışma tamamlandıktan sonra ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="96d6c-183">Ve `AllowNull` `DisallowNull` öznitelikleri, değişkenler üzerindeki ön koşulların bu değişkenler üzerindeki geçersiz ek açıklamalarla eşleşmeyebileceğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="96d6c-184">Bunlar, API'nizin özellikleri hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="96d6c-185">Bu ek bilgiler, arayanların API'nizi doğru kullanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="96d6c-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="96d6c-186">Aşağıdaki öznitelikleri kullanarak ön koşulları belirttiğinizi unutmayın:</span><span class="sxs-lookup"><span data-stu-id="96d6c-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="96d6c-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Nullolmayan bir giriş bağımsız değişkeni null olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="96d6c-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Nullable giriş bağımsız değişkeni asla null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="96d6c-189">Aşağıdaki koşulları belirtin: `MaybeNull` ve`NotNull`</span><span class="sxs-lookup"><span data-stu-id="96d6c-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="96d6c-190">Aşağıdaki imzayı içeren bir yönteminiz olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="96d6c-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="96d6c-191">Aranan ad bulunamadında dönmek `null` için büyük olasılıkla böyle bir yöntem yazmışsınızdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="96d6c-192">Bu, `null` kaydın bulunamadıgini açıkça gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="96d6c-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="96d6c-193">Bu örnekte, büyük olasılıkla dönüş türünü `Customer` `Customer?`' den ' e değiştirirsiniz</span><span class="sxs-lookup"><span data-stu-id="96d6c-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="96d6c-194">İade değerini nullable bir başvuru türü olarak bildirmek, bu API'nin amacını açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="96d6c-195">Genel tanımlar [ve nullability](../../nullable-attributes.md#generic-definitions-and-nullability) kapsamındaki nedenlerden dolayı bu teknik genel yöntemlerle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-195">For reasons covered under [Generic definitions and nullability](../../nullable-attributes.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="96d6c-196">Benzer bir desen izleyen genel bir yöntem olabilir:</span><span class="sxs-lookup"><span data-stu-id="96d6c-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="96d6c-197">İade değerinin `T?`.</span><span class="sxs-lookup"><span data-stu-id="96d6c-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="96d6c-198">Aranan öğe `null` bulunamıyorsa yöntem döndürür.</span><span class="sxs-lookup"><span data-stu-id="96d6c-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="96d6c-199">`T?` İade türünü bildiremediğinizi, yöntem iadesine `MaybeNull` ek açıklama eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="96d6c-200">Önceki kod, arayanlara sözleşmenin geçersiz bir tür ima ettiğini, ancak iade değerinin aslında null *olabileceğini* bildirir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="96d6c-201">`MaybeNull` API'niz genellikle genel bir tür parametresi olan nullable olmayan bir tür olması gerektiğinde `null` özniteliği kullanın, ancak döndürülecek örnekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="96d6c-202">Tür geçersiz bir başvuru türü `out` olsa `ref` bile, iade değerinin veya bağımsız değişkenin null olmadığını da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="96d6c-203">Bir dizinin bir dizi öğeyi tutacak kadar büyük olmasını sağlayan bir yöntem düşünün.</span><span class="sxs-lookup"><span data-stu-id="96d6c-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="96d6c-204">Giriş bağımsız değişkeninin kapasitesi yoksa, yordam yeni bir dizi ayırır ve varolan tüm öğeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="96d6c-205">Giriş bağımsız değişkeni `null`ise, yordam yeni depolama ayırır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="96d6c-206">Yeterli kapasite varsa, rutin hiçbir şey yapmaz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="96d6c-207">Bu rutini aşağıdaki gibi adlandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="96d6c-208">Null başvuru türlerini etkinleştirdikten sonra, önceki kodun uyarı olmadan derlediğinden emin olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="96d6c-209">Yöntem döndüğünde, bağımsız `storage` değişkenin null olmaması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="96d6c-210">Ancak, null bir başvuru `EnsureCapacity` ile aramak için kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="96d6c-211">Geçersiz bir `storage` başvuru türü yapabilir ve `NotNull` parametre bildirimine post-koşul ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="96d6c-212">Önceki kod varolan sözleşmeyi açıkça ifade eder: Arayanlar `null` değeri olan bir değişkeni geçirebilir, ancak iade değerinin hiçbir zaman null olmadığı garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="96d6c-213">Öznitelik, `NotNull` bağımsız değişken `ref` `out` olarak `null` geçirilebileceği ve bağımsız değişkenler için en yararlı olan, ancak yöntem döndüğünde bu bağımsız değişkenin null olmaması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="96d6c-214">Aşağıdaki öznitelikleri kullanarak koşulsuz postconditions belirtin:</span><span class="sxs-lookup"><span data-stu-id="96d6c-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="96d6c-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Nullable olmayan bir iade değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="96d6c-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable iade değeri asla null olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="96d6c-217">Koşullu koşullar `NotNullWhen`belirtin: `MaybeNullWhen`, , ve`NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="96d6c-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="96d6c-218">Muhtemelen yönteme `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>aşinasınızdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="96d6c-219">Bağımsız değişken `true` null veya boş bir dize olduğunda bu yöntem döndürür.</span><span class="sxs-lookup"><span data-stu-id="96d6c-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="96d6c-220">Bu bir null-check şeklidir: Arayanların yöntem dönerse `false`bağımsız değişkeni geçersiz olarak denetlemelerine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="96d6c-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="96d6c-221">Bu gibi bir yöntemi kullanılabilir farkında yapmak için, bağımsız değişkeni boşolabilir başvuru `NotNullWhen` türüne ayarlar ve özniteliği eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="96d6c-222">Bu, derleyiciye, iade değerinin bulunduğu `false` herhangi bir kodun geçersiz olarak kontrol edilmesine gerek olmadığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="96d6c-223">Öznitelik eklenmesi gerekli null denetimi `IsNullOrEmpty` gerçekleştiren derleyicinin statik çözümlemesi bildirir: `false`döndürdüğünde, giriş `null`bağımsız değişkeni .</span><span class="sxs-lookup"><span data-stu-id="96d6c-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="96d6c-224">Yöntem <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> yukarıda .NET Core 3.0 için gösterildiği gibi açıklamalı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="96d6c-225">Kod tabanınızda, geçersiz değerler için nesnelerin durumunu denetleyen benzer yöntemler olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="96d6c-226">Derleyici özel null denetim yöntemlerini tanımaz ve ek açıklamaları kendiniz eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="96d6c-227">Öznitelik eklediğinizde, derleyicinin statik çözümlemesi test edilen değişkenin null denetlendiğini bilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="96d6c-228">Bu öznitelikler için `Try*` başka bir kullanım desendir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="96d6c-229">Postconditions ve `ref` `out` değişkenler iade değeri üzerinden iletilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="96d6c-230">Daha önce gösterilen bu yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="96d6c-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="96d6c-231">Önceki yöntem tipik bir .NET deyimini izler: döndürme `message` değeri, bulunan değere veya ileti bulunmazsa varsayılan değere ayarlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="96d6c-232">Yöntem dönerse, `true`değeri `message` null değildir; aksi takdirde, `message` yöntem null ayarlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="96d6c-233">Bu deyimi `NotNullWhen` özniteliği kullanarak iletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="96d6c-234">Geçersiz başvuru türleri için imzayı güncelleştirdiğinizde, bir `message` `string?` öznitelik yapın ve ekleyin:</span><span class="sxs-lookup"><span data-stu-id="96d6c-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="96d6c-235">Önceki örnekte, döndürdüğünde `message` `TryGetMessage` `true`değerinin null olmadığı bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="96d6c-236">Kod tabanınızdaki benzer yöntemlere aynı şekilde açıklama yapmalısınız: bağımsız `null`değişkenler yöntem döndüğünde `true`null olmayabilir ve bunlarla birlikte olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="96d6c-237">İhtiyaç duyabileceğiniz son bir özellik daha vardır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="96d6c-238">Bazen bir iade değerinin null durumu, bir veya daha fazla giriş bağımsız değişkeninin null durumuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="96d6c-239">Bu yöntemler, belirli giriş bağımsız değişkenleri olmadığında `null`null olmayan bir değer döndürecek.</span><span class="sxs-lookup"><span data-stu-id="96d6c-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="96d6c-240">Bu yöntemlere doğru açıklama ekinvermek `NotNullIfNotNull` için özniteliği kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="96d6c-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="96d6c-241">Aşağıdaki yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="96d6c-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="96d6c-242">`url` Bağımsız değişken null değilse, çıktı . `null`</span><span class="sxs-lookup"><span data-stu-id="96d6c-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="96d6c-243">Geçersiz başvurular etkinleştirildikten sonra, API'nizin hiçbir zaman null girişi kabul etmemesi koşuluyla, bu imza doğru çalışır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="96d6c-244">Ancak, giriş null olabilir, o zaman döndürme değeri de null olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="96d6c-245">Bu nedenle, imzayı aşağıdaki kodla değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="96d6c-246">Bu da çalışır, ancak genellikle arayanlar `null` ekstra denetimler uygulamak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="96d6c-247">Sözleşme, iade değerinin `null` yalnızca giriş bağımsız değişkeni `url` `null`.</span><span class="sxs-lookup"><span data-stu-id="96d6c-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="96d6c-248">Bu sözleşmeyi ifade etmek için, aşağıdaki kodda gösterildiği gibi bu yönteme açıklama lar ekine bilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="96d6c-249">İade değeri ve bağımsız değişken, her ikisi `?` de olabilir belirten `null`ile açıklamalı edilmiştir .</span><span class="sxs-lookup"><span data-stu-id="96d6c-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="96d6c-250">Öznitelik, `url` bağımsız değişken olmadığında geri dönüş değerinin null olmayacağını daha `null`da açıklar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="96d6c-251">Bu öznitelikleri kullanarak koşullu posta koşullarını belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="96d6c-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable olmayan bir giriş bağımsız değişkeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="96d6c-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable giriş bağımsız değişkeni null olmaz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="96d6c-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin giriş bağımsız değişkeni null değilse, iade değeri null değildir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="96d6c-255">Erişilemenebilen kodu doğrulama</span><span class="sxs-lookup"><span data-stu-id="96d6c-255">Verify unreachable code</span></span>

<span data-ttu-id="96d6c-256">Bazı yöntemler, genellikle özel durum yardımcıları veya diğer yardımcı yöntemleri, her zaman bir özel durum atarak çıkmak.</span><span class="sxs-lookup"><span data-stu-id="96d6c-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="96d6c-257">Veya, bir yardımcı Boolean bağımsız değişkeninin değerine dayalı bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="96d6c-258">İlk durumda, yöntem bildirimine `DoesNotReturn` öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="96d6c-259">Derleyici size üç şekilde yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="96d6c-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="96d6c-260">İlk olarak, derleyici, yöntemin özel durum atmadan çıkabileceği bir yol varsa bir uyarı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="96d6c-261">İkinci olarak, derleyici, uygun `catch` bir yan tümceyle karşılaşıncaya kadar, bu yönteme yapılan bir çağrıdan sonra herhangi bir kodu *erişilemez*olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="96d6c-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="96d6c-262">Üçüncü olarak, erişilebilen kod herhangi bir null durumları etkilemez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="96d6c-263">Bu yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="96d6c-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

<span data-ttu-id="96d6c-264">İkinci durumda, yöntemin `DoesNotReturnIf` Boolean parametreöze özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="96d6c-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="96d6c-265">Önceki örneği aşağıdaki gibi değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96d6c-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="96d6c-266">Özet</span><span class="sxs-lookup"><span data-stu-id="96d6c-266">Summary</span></span>

<span data-ttu-id="96d6c-267">Nullable başvuru türleri eklemek, API'ler'in değişkenler için `null`beklentilerini açıklamak için bir başlangıç sözcük dağarcığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="96d6c-268">Ek öznitelikler, değişkenlerin null durumunu ön koşul ve koşul olarak tanımlamak için daha zengin bir sözcük dağarcığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="96d6c-269">Bu öznitelikler, beklentilerinizi daha net bir şekilde açıklar ve API'lerinizi kullanan geliştiriciler için daha iyi bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="96d6c-270">Kitaplıkları boşbir bağlam için güncellerken, API'lerinizin kullanıcılarına doğru kullanıma rehberlik etmek için bu öznitelikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="96d6c-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="96d6c-271">Bu öznitelikler, giriş bağımsız değişkenlerinin ve döndürme değerlerinin null durumunu tam olarak açıklamanıza yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="96d6c-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="96d6c-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Nullolmayan bir giriş bağımsız değişkeni null olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="96d6c-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Nullable giriş bağımsız değişkeni asla null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="96d6c-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Nullable olmayan bir iade değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="96d6c-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable iade değeri asla null olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="96d6c-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="96d6c-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable olmayan bir giriş bağımsız değişkeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="96d6c-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable giriş bağımsız değişkeni null olmaz.</span><span class="sxs-lookup"><span data-stu-id="96d6c-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="96d6c-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin giriş bağımsız değişkeni null değilse, iade değeri null değildir.</span><span class="sxs-lookup"><span data-stu-id="96d6c-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="96d6c-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Bir yöntem asla dönmez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="96d6c-280">Başka bir deyişle, her zaman bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="96d6c-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="96d6c-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): İlişkili `bool` parametre belirtilen değere sahipse bu yöntem asla dönmez.</span><span class="sxs-lookup"><span data-stu-id="96d6c-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
