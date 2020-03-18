---
title: Yerleşik başvuru türleri - C# başvurusu
description: Bunları bildirmek için kullanabileceğiniz C# anahtar kelimeleri olan başvuru türleri hakkında bilgi edinin.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399646"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="25035-103">Yerleşik başvuru türleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="25035-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="25035-104">C# bir dizi yerleşik başvuru türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="25035-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="25035-105">.NET kitaplığında bir türle eş anlamlı anahtar sözcükleri veya işleçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="25035-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span>

## <a name="the-object-type"></a><span data-ttu-id="25035-106">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="25035-106">The object type</span></span>

<span data-ttu-id="25035-107">Türü `object` .NET'te <xref:System.Object?displayProperty=nameWithType> bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="25035-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="25035-108">C#'ın birleşik tip sisteminde, önceden tanımlanmış ve kullanıcı tarafından tanımlanan tüm türler, referans <xref:System.Object?displayProperty=nameWithType>türleri ve değer türleri, doğrudan veya dolaylı olarak .</span><span class="sxs-lookup"><span data-stu-id="25035-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25035-109">Herhangi bir türdeki değerleri türün `object`değişkenlerine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25035-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="25035-110">Herhangi `object` bir değişken, gerçek değeri `null`kullanılarak varsayılan değerine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="25035-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="25035-111">Değer türünden bir değişken nesneye dönüştürüldüğünde *kutulu*olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="25035-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="25035-112">Tür `object` değişkeni bir değer türüne dönüştürüldüğünde, *kutusunun açılmış*olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="25035-112">When a variable of type `object` is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="25035-113">Daha fazla bilgi [için, Kutulama ve Unboxing](../../programming-guide/types/boxing-and-unboxing.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="25035-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="the-string-type"></a><span data-ttu-id="25035-114">Dize türü</span><span class="sxs-lookup"><span data-stu-id="25035-114">The string type</span></span>

<span data-ttu-id="25035-115">Tür, `string` sıfır veya daha fazla Unicode karakter dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="25035-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="25035-116">`string`.NET'te <xref:System.String?displayProperty=nameWithType> bir takma addır.</span><span class="sxs-lookup"><span data-stu-id="25035-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="25035-117">Bir `string` başvuru türü olmasına rağmen, [eşitlik işleçleri `==` ve `!=` ](../operators/equality-operators.md#string-equality) başvurular değil `string` nesnelerin değerlerini karşılaştırmak için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="25035-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="25035-118">Bu dize eşitliği için sınama daha sezgisel hale getirir.</span><span class="sxs-lookup"><span data-stu-id="25035-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="25035-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="25035-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="25035-120">Bu, dizelerin içeriği eşdeğer olduğundan "True" ve sonra `a` "False" gösterir, ancak aynı dize örneğine `b` başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="25035-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="25035-121">[+ işleç](../operators/addition-operator.md#string-concatenation) dizeleri birleştirir:</span><span class="sxs-lookup"><span data-stu-id="25035-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="25035-122">Bu, "günaydın" içeren bir dize nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25035-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="25035-123">Dizeleri *değişmez*-bir dize nesnesinin içeriği nesne oluşturulduktan sonra değiştirilemez, ancak sözdizimi bunu yapabilirmişsiniz gibi görünmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="25035-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="25035-124">Örneğin, bu kodu yazarken, derleyici aslında yeni karakter dizisini tutmak için yeni bir dize nesnesi oluşturur ve bu yeni nesne `b`.</span><span class="sxs-lookup"><span data-stu-id="25035-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="25035-125">("h" dizesini `b` içerdiğinde) ayrılan bellek daha sonra çöp toplama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="25035-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="25035-126">`[]` [İşleç,](../operators/member-access-operators.md#indexer-operator-) bir dizedeki tek tek karakterlere yalnızca erişim için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25035-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a string.</span></span> <span data-ttu-id="25035-127">Geçerli dizin `0` değerleri dize uzunluğundan daha az olarak başlar ve olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="25035-127">Valid index values start at `0` and must be less than the length of the string:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="25035-128">Benzer şekilde, `[]` işleç de bir dize her karakter üzerinde yineleme için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="25035-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a string:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

<span data-ttu-id="25035-129">String literals türü `string` ndedir ve alıntı ve `@`-alıntı olmak üzere iki şekilde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="25035-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="25035-130">Alıntı dize literals çift tırnak işaretleri ("):</span><span class="sxs-lookup"><span data-stu-id="25035-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="25035-131">String literals herhangi bir karakter literal içerebilir.</span><span class="sxs-lookup"><span data-stu-id="25035-131">String literals can contain any character literal.</span></span> <span data-ttu-id="25035-132">Kaçış sekansları dahildir.</span><span class="sxs-lookup"><span data-stu-id="25035-132">Escape sequences are included.</span></span> <span data-ttu-id="25035-133">Aşağıdaki örnekte, `\\` ters eğik `\u0066` çizgi, f `\n` harfi ve yeni satır için kaçış sırası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25035-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> <span data-ttu-id="25035-134">Kaçış kodu `\udddd` (dört basamaklı bir sayı nın olduğu yer) `dddd` `dddd`Unicode karakteri U+ temsil eder.</span><span class="sxs-lookup"><span data-stu-id="25035-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="25035-135">Sekiz basamaklı Unicode kaçış kodları `\Udddddddd`da tanınır: .</span><span class="sxs-lookup"><span data-stu-id="25035-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="25035-136">[Verbatim string literals](../tokens/verbatim.md) ile `@` başlar ve aynı zamanda çift tırnak işaretleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="25035-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="25035-137">Örnek:</span><span class="sxs-lookup"><span data-stu-id="25035-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="25035-138">Kelimenin tam anlamıyla dizeleri avantajı kaçış dizileri *işlenmez,* bu da kolay yazmayı kolaylaştırır, örneğin, tam nitelikli Windows dosya adı:</span><span class="sxs-lookup"><span data-stu-id="25035-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="25035-139">Bir @-quoted dize çift tırnak işareti eklemek için, iki katına:</span><span class="sxs-lookup"><span data-stu-id="25035-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="25035-140">Temsilci türü</span><span class="sxs-lookup"><span data-stu-id="25035-140">The delegate type</span></span>

<span data-ttu-id="25035-141">Temsilci türü bildirimi yöntem imzasına benzer.</span><span class="sxs-lookup"><span data-stu-id="25035-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="25035-142">Bir iade değeri ve herhangi bir türde parametrelerin herhangi bir sayı vardır:</span><span class="sxs-lookup"><span data-stu-id="25035-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="25035-143">.NET'te `System.Action` `System.Func` ve türleri birçok ortak temsilci için genel tanımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="25035-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="25035-144">Büyük olasılıkla yeni özel temsilci türleri tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="25035-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="25035-145">Bunun yerine, sağlanan genel türlerin anlık oluşturmalarını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25035-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="25035-146">A, `delegate` adlandırılmış veya anonim bir yöntemi kapsüllemek için kullanılabilecek bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="25035-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="25035-147">Temsilciler C++'daki işlev işaretçilerine benzer; ancak, temsilciler tür güvenli ve güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="25035-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="25035-148">Temsilcilerin başvuruları [için, bkz.](../../programming-guide/delegates/index.md) [Generic Delegates](../../programming-guide/generics/generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="25035-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="25035-149">Temsilciler, [Etkinliklerin](../../programming-guide/events/index.md)temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25035-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="25035-150">Bir temsilci, adlandırılmış veya anonim bir yöntemle ilişkilendirilerek anında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25035-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="25035-151">Temsilci, uyumlu bir dönüş türü ne de giriş parametrelerine sahip bir yöntem veya lambda ifadesi ile anında alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25035-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="25035-152">Yöntem imzasında izin verilen varyans derecesi hakkında daha fazla bilgi [için, Temsilciler'deki Varyans'a](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="25035-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="25035-153">Anonim yöntemlerle kullanılmak üzere, temsilci ve onunla ilişkili kod birlikte bildirilir.</span><span class="sxs-lookup"><span data-stu-id="25035-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span>

## <a name="the-dynamic-type"></a><span data-ttu-id="25035-154">Dinamik tür</span><span class="sxs-lookup"><span data-stu-id="25035-154">The dynamic type</span></span>

<span data-ttu-id="25035-155">Tür, `dynamic` değişkenin kullanımının ve üyelerine yapılan başvuruların derleme zamanı türü denetimi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="25035-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="25035-156">Bunun yerine, bu işlemler çalışma zamanında çözülür.</span><span class="sxs-lookup"><span data-stu-id="25035-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="25035-157">Bu `dynamic` tür, Office Automation API'leri gibi COM API'lerine, IronPython kitaplıkları gibi dinamik API'lere ve HTML Belge Nesnesi Modeli'ne (DOM) erişimi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="25035-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="25035-158">Tür `dynamic` çoğu durumda `object` türü gibi olur.</span><span class="sxs-lookup"><span data-stu-id="25035-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="25035-159">Özellikle, herhangi bir null olmayan ifade `dynamic` türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="25035-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="25035-160">Tür, `dynamic` tür `object` `dynamic` ifadeleri içeren çözülmemiş veya derleyici tarafından denetlenen tür lerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="25035-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="25035-161">Derleyici, işlemle ilgili bilgileri bir araya getirir ve bu bilgiler daha sonra çalışma zamanında işlemi değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25035-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="25035-162">İşlemin bir parçası olarak, `dynamic` tür değişkenleri tür `object`değişkenleri halinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="25035-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="25035-163">Bu nedenle, tür `dynamic` yalnızca derleme zamanda değil, çalışma zamanında var.</span><span class="sxs-lookup"><span data-stu-id="25035-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="25035-164">Aşağıdaki örnek, bir tür `dynamic` değişkeni ile `object`tür değişkeni ile tezat oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="25035-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="25035-165">Her değişkenin türünü derleme zamanında doğrulamak için fare `dyn` `obj` işaretçisini `WriteLine` ifadelerin üzerine veya ifadelerine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="25035-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="25035-166">Aşağıdaki kodu IntelliSense'in kullanılabildiği bir düzenleyiciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="25035-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="25035-167">IntelliSense **dynamic** için `dyn` dinamik ve `obj` **nesne** gösterir.</span><span class="sxs-lookup"><span data-stu-id="25035-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="25035-168"><xref:System.Console.WriteLine%2A> İfadeler çalışma zamanı türlerini `dyn` `obj`görüntüler ve.</span><span class="sxs-lookup"><span data-stu-id="25035-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="25035-169">Bu noktada, her ikisi de aynı tür, tamsayı var.</span><span class="sxs-lookup"><span data-stu-id="25035-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="25035-170">Aşağıdaki çıktı üretilir:</span><span class="sxs-lookup"><span data-stu-id="25035-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="25035-171">Derleme zamanı ile `dyn` `obj` arasındaki farkı görmek için, önceki örnekteki bildirimler `WriteLine` ve deyimler arasındaki aşağıdaki iki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="25035-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="25035-172">Bir tamsede ve ifadedeki `obj + 3`bir nesnenin ekleme denemesi için derleyici hatası bildirilir.</span><span class="sxs-lookup"><span data-stu-id="25035-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="25035-173">Ancak, hiçbir hata `dyn + 3`için bildirilir .</span><span class="sxs-lookup"><span data-stu-id="25035-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="25035-174">`dyn` Türü `dyn` . `dynamic`</span><span class="sxs-lookup"><span data-stu-id="25035-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="25035-175">Aşağıdaki örnek, `dynamic` çeşitli bildirimlerde kullanır.</span><span class="sxs-lookup"><span data-stu-id="25035-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="25035-176">Yöntem `Main` ayrıca derleme zamanı türü denetimi ile çalışma zamanı türü denetimiyle tezat oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="25035-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="25035-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25035-177">See also</span></span>

- [<span data-ttu-id="25035-178">C# Referans</span><span class="sxs-lookup"><span data-stu-id="25035-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="25035-179">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="25035-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="25035-180">Olaylar</span><span class="sxs-lookup"><span data-stu-id="25035-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="25035-181">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="25035-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="25035-182">Dizeleri Kullanmak için En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="25035-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="25035-183">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="25035-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="25035-184">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="25035-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="25035-185">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="25035-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="25035-186">Desen eşleştirme ve as ve operatörler kullanarak güvenli bir şekilde döküm nasıl</span><span class="sxs-lookup"><span data-stu-id="25035-186">How to safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="25035-187">Walkthrough: dinamik nesneler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="25035-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
