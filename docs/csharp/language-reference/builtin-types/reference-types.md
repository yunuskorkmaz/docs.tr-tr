---
title: Yerleşik başvuru türleri- C# başvuru
description: Bunları bildirmek için kullanabileceğiniz anahtar sözcüklere C# sahip başvuru türleri hakkında bilgi edinin.
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
ms.openlocfilehash: a5a32fa0a98cda37d7f599b20ef2b507cadd730c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69604204"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="804fe-103">Yerleşik başvuru türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="804fe-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="804fe-104">C#, çeşitli yerleşik başvuru türlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="804fe-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="804fe-105">.NET kitaplığındaki bir tür için eş anlamlı anahtar sözcükler veya operatörler vardır.</span><span class="sxs-lookup"><span data-stu-id="804fe-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="804fe-106">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="804fe-106">The object type</span></span>

<span data-ttu-id="804fe-107">Türü .net 'teki için <xref:System.Object?displayProperty=nameWithType> bir diğer addır. `object`</span><span class="sxs-lookup"><span data-stu-id="804fe-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="804fe-108">Birleşik tür sisteminde C#, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, doğrudan veya dolaylı olarak öğesinden <xref:System.Object?displayProperty=nameWithType>devralınır.</span><span class="sxs-lookup"><span data-stu-id="804fe-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="804fe-109">Tür `object`değişkenlerine her türden değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="804fe-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="804fe-110">Herhangi `object` bir değişken varsayılan değeri değişmez `null`değer kullanılarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="804fe-111">Değer türünde bir değişken nesnesine dönüştürüldüğünde, *kutulanmış*olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="804fe-112">Nesne türündeki bir değişken bir değer türüne dönüştürüldüğünde, *kutulanmamış*olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="804fe-113">Daha fazla bilgi için bkz. [kutulama ve kutudan](../../programming-guide/types/boxing-and-unboxing.md)çıkarma.</span><span class="sxs-lookup"><span data-stu-id="804fe-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="804fe-114">Dize türü</span><span class="sxs-lookup"><span data-stu-id="804fe-114">The string type</span></span>

<span data-ttu-id="804fe-115">Tür `string` , sıfır veya daha fazla Unicode karakter dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="804fe-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="804fe-116">`string`, .NET içindeki için <xref:System.String?displayProperty=nameWithType> bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="804fe-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="804fe-117">, `string` Bir başvuru türü olsa da, [eşitlik işleçleri `==` ve `!=` ](../operators/equality-operators.md#string-equality) `string` nesneler, başvuruları değil, nesne değerlerini karşılaştırmak için tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="804fe-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="804fe-118">Bu, dize eşitlik sınamasını daha sezgisel hale getirir.</span><span class="sxs-lookup"><span data-stu-id="804fe-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="804fe-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="804fe-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="804fe-120">Bu, dizelerin içeriği eşdeğer olduğundan, ancak `a` `b` aynı dize örneğine başvurmadığından "true" ve ardından "false" değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="804fe-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="804fe-121">[+ İşleci](../operators/addition-operator.md#string-concatenation) dizeleri art arda ekler:</span><span class="sxs-lookup"><span data-stu-id="804fe-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="804fe-122">Bu, "iyi sabah" içeren bir dize nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="804fe-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="804fe-123">Dizeler *sabittir*--dize nesnesinin içeriği nesne oluşturulduktan sonra değiştirilemez, ancak söz konusu sözdizimi bunu yapabilse gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="804fe-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="804fe-124">Örneğin, bu kodu yazdığınızda, derleyici aslında yeni karakter dizisini tutmak için yeni bir dize nesnesi oluşturur ve yeni nesne ' ye `b`atanır.</span><span class="sxs-lookup"><span data-stu-id="804fe-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="804fe-125">İçin `b` ayrılan bellek ("h" dizesini içeriyorsa), daha sonra çöp toplama için uygun olur.</span><span class="sxs-lookup"><span data-stu-id="804fe-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="804fe-126">`[]` [İşleci](../operators/member-access-operators.md#indexer-operator-) ,`string`tek tek karakterleri için salt okunur erişim için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="804fe-127">Geçerli değerler başlangıç `0` ve uzunluğundan `string`küçük olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="804fe-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="804fe-128">Benzer şekilde, `[]` işleci, içindeki her bir `string`karakter üzerinde yineleme için de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="804fe-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="804fe-129">Dize sabit değerleri türündedir `string` ve tırnak içine alınmış ve `@`tırnak içine alınmış iki biçimde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="804fe-130">Tırnak işaretli dize sabit değerleri çift tırnak işareti (") içine alınır:</span><span class="sxs-lookup"><span data-stu-id="804fe-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="804fe-131">Dize sabit değerleri, herhangi bir karakter sabit değeri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-131">String literals can contain any character literal.</span></span> <span data-ttu-id="804fe-132">Kaçış dizileri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-132">Escape sequences are included.</span></span> <span data-ttu-id="804fe-133">Aşağıdaki örnek, f harfi ve `\\` `\n` yeni satır için `\u0066` ters eğik çizgi için kaçış sırası kullanır.</span><span class="sxs-lookup"><span data-stu-id="804fe-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="804fe-134">Kaçış kodu `\udddd` `dddd` (dört basamaklı bir sayı), U +`dddd`Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="804fe-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="804fe-135">Sekiz basamaklı Unicode kaçış kodları da tanınmış: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="804fe-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="804fe-136">Tam [dize değişmez değerleri](../tokens/verbatim.md) ile `@` başlar ve ayrıca çift tırnak işaretleri içine alınır.</span><span class="sxs-lookup"><span data-stu-id="804fe-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="804fe-137">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="804fe-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="804fe-138">Tam dizelerin avantajı, kaçış dizilerinin işlenmediği, örneğin tam nitelikli bir Windows dosya adını yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="804fe-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="804fe-139">Bir @-quoted dizeye çift tırnak işareti eklemek için, Double:</span><span class="sxs-lookup"><span data-stu-id="804fe-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="804fe-140">Temsilci türü</span><span class="sxs-lookup"><span data-stu-id="804fe-140">The delegate type</span></span>

<span data-ttu-id="804fe-141">Bir temsilci türünün bildirimi, yöntem imzasına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="804fe-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="804fe-142">Dönüş değerine ve herhangi bir türde parametreye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="804fe-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="804fe-143">.Net ' `System.Action` te ve `System.Func` türler birçok ortak temsilci için genel tanımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="804fe-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="804fe-144">Muhtemelen yeni özel temsilci türleri tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="804fe-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="804fe-145">Bunun yerine, belirtilen genel türlerin örneklemesini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="804fe-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="804fe-146">`delegate` , Adlandırılmış veya anonim bir yöntemi kapsüllemek için kullanılabilecek bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="804fe-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="804fe-147">Temsilciler, içindeki C++işlev işaretçilerine benzerdir; Ancak, temsilciler tür açısından güvenli ve güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="804fe-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="804fe-148">Temsilcilerin uygulamaları için bkz. [Temsilciler](../../programming-guide/delegates/index.md) ve [Genel Temsilciler](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="804fe-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="804fe-149">Temsilciler, [olayların](../../programming-guide/events/index.md)temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="804fe-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="804fe-150">Bir temsilci, adlandırılmış ya da anonim bir yöntemle ilişkilendirerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="804fe-151">Temsilci, uyumlu bir dönüş türü ve giriş parametrelerine sahip bir yöntem veya lambda ifadesiyle oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="804fe-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="804fe-152">Yöntem imzasında izin verilen varyans derecesi hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="804fe-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="804fe-153">Anonim yöntemlerle kullanılmak üzere, ile ilişkilendirilecek temsilci ve kod birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="804fe-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="804fe-154">Dinamik tür</span><span class="sxs-lookup"><span data-stu-id="804fe-154">The dynamic type</span></span>

<span data-ttu-id="804fe-155">`dynamic` Tür, değişkenin ve bunların üyelerine derleme zamanı tür denetimi atlama ' nin nasıl kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="804fe-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="804fe-156">Bunun yerine, bu işlemler çalışma zamanında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="804fe-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="804fe-157">Bu `dynamic` tür, Office Otomasyonu API 'leri, IronPython kitaplıkları gibi dinamik API 'ler ve HTML belge nesne modeli (DOM) gibi com API 'lerine erişimi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="804fe-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="804fe-158">Tür `dynamic` birçok durumda tür `object` gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="804fe-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="804fe-159">Özellikle, null olmayan herhangi bir ifade `dynamic` türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="804fe-160">Türü `dynamic` , türü ifadeler `object` `dynamic` içeren işlemlerdeki öğesinden farklıdır veya derleyici tarafından denetlenen tür.</span><span class="sxs-lookup"><span data-stu-id="804fe-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="804fe-161">Derleyici, işlem hakkındaki bilgileri birlikte paketler ve bu bilgiler daha sonra çalışma zamanında işlemi değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="804fe-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="804fe-162">İşlemin bir parçası olarak, türündeki `dynamic` değişkenler tür `object`değişkenlerine derlenir.</span><span class="sxs-lookup"><span data-stu-id="804fe-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="804fe-163">Bu nedenle, `dynamic` tür yalnızca derleme zamanında bulunur, çalışma zamanında değil.</span><span class="sxs-lookup"><span data-stu-id="804fe-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="804fe-164">Aşağıdaki örnek, türünde `dynamic` bir değişkenini türünde `object`bir değişkene karşıttır.</span><span class="sxs-lookup"><span data-stu-id="804fe-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="804fe-165">Derleme zamanında her değişkenin türünü doğrulamak için, fare işaretçisini `dyn` `WriteLine` deyimlere veya `obj` ifadelerine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="804fe-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="804fe-166">Aşağıdaki kodu IntelliSense 'in kullanılabildiği bir düzenleyiciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="804fe-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="804fe-167">`dyn` IntelliSense, için dinamikvenesnesini`obj`gösterir.</span><span class="sxs-lookup"><span data-stu-id="804fe-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="804fe-168"><xref:System.Console.WriteLine%2A> Deyimleri `dyn` ve çalışma`obj`zamanı türlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="804fe-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="804fe-169">Bu noktada, her ikisi de aynı tür, tamsayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="804fe-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="804fe-170">Aşağıdaki çıktı üretilir:</span><span class="sxs-lookup"><span data-stu-id="804fe-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="804fe-171">`WriteLine` Ve `dyn` derlemezamanıarasındakifarkıgörmekiçin,öncekiörnektekibildirimlervedeyimlerarasınaaşağıdakiikisatırıekleyin.`obj`</span><span class="sxs-lookup"><span data-stu-id="804fe-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="804fe-172">Bir tamsayı ve ifadedeki `obj + 3`bir nesne ekleme denemesi için bir derleyici hatası bildirilir.</span><span class="sxs-lookup"><span data-stu-id="804fe-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="804fe-173">Ancak, için `dyn + 3`bir hata raporlanmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="804fe-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="804fe-174">Türü olduğundan `dyn` ,`dynamic`içerenifade derleme sırasında denetlenmez. `dyn`</span><span class="sxs-lookup"><span data-stu-id="804fe-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="804fe-175">Aşağıdaki örnek, çeşitli `dynamic` bildirimlerde kullanır.</span><span class="sxs-lookup"><span data-stu-id="804fe-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="804fe-176">`Main` Yöntemi ayrıca derleme zamanı tür denetimini çalışma zamanı tür denetlemesi ile karşıtlıkları.</span><span class="sxs-lookup"><span data-stu-id="804fe-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="804fe-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="804fe-177">See also</span></span>

- [<span data-ttu-id="804fe-178">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="804fe-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="804fe-179">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="804fe-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="804fe-180">Olaylar</span><span class="sxs-lookup"><span data-stu-id="804fe-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="804fe-181">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="804fe-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="804fe-182">Dizeleri Kullanmak için En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="804fe-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="804fe-183">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="804fe-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="804fe-184">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="804fe-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="804fe-185">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="804fe-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="804fe-186">Nasıl yapılır: model eşleştirmeyi ve as ve işleç işleçlerini kullanarak güvenli bir şekilde atama</span><span class="sxs-lookup"><span data-stu-id="804fe-186">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="804fe-187">İzlenecek yol: dinamik nesneler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="804fe-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
