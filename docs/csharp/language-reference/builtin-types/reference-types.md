---
title: Yerleşik başvuru türlerini - C# başvurusu
description: Başvuru türleri hakkında bilgi edinin C# bunları bildirmek için kullanabileceğiniz anahtar sözcükleri.
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
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877197"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="3f977-103">Yerleşik başvuru türlerini (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3f977-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="3f977-104">C#bir dizi yerleşik başvuru türlerini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f977-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="3f977-105">Anahtar sözcük ya da .NET Kitaplığı'nda bir tür için eş anlamlı sözcükler olan işleçleri sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="3f977-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="3f977-106">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="3f977-106">The object type</span></span>

<span data-ttu-id="3f977-107">`object` Türü için bir diğer ad, <xref:System.Object?displayProperty=nameWithType> .NET içinde.</span><span class="sxs-lookup"><span data-stu-id="3f977-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="3f977-108">C#, tüm türlerin, önceden tanımlanmış ve kullanıcı tanımlı başvuru türleri ve değer türleri birleşik tür sisteminde doğrudan veya dolaylı olarak devralınacak <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f977-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f977-109">Her türden değer türü değişkenler için atayabilirsiniz `object`.</span><span class="sxs-lookup"><span data-stu-id="3f977-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="3f977-110">Tüm `object` değişkeni değişmez değer kullanılarak varsayılan değerine atanabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="3f977-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="3f977-111">Ne zaman bir değer türü bir değişkene dönüştürülür nesnesi için kabul edilecek *Kutulu*.</span><span class="sxs-lookup"><span data-stu-id="3f977-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="3f977-112">Türündeki bir değişkene bir değer türüne dönüştürülür, onu olduğu söylenir *kutulanmamış*.</span><span class="sxs-lookup"><span data-stu-id="3f977-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="3f977-113">Daha fazla bilgi için [kutulama ve kutudan çıkarma](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="3f977-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="3f977-114">Dize türü</span><span class="sxs-lookup"><span data-stu-id="3f977-114">The string type</span></span>

<span data-ttu-id="3f977-115">`string` Türü bir dizi sıfır veya daha fazla Unicode karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3f977-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="3f977-116">`string` için bir diğer addır <xref:System.String?displayProperty=nameWithType> .NET içinde.</span><span class="sxs-lookup"><span data-stu-id="3f977-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="3f977-117">Ancak `string` bir başvuru türüdür [eşitlik işleçleri `==` ve `!=` ](../operators/equality-operators.md#string-equality) değerlerini karşılaştırmak için tanımlanan `string` nesnelerine, başvuruda değil.</span><span class="sxs-lookup"><span data-stu-id="3f977-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="3f977-118">Bu, daha sezgisel dizeyi eşitlik için sınama yapar.</span><span class="sxs-lookup"><span data-stu-id="3f977-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="3f977-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3f977-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="3f977-120">Bu "True" görüntüler ve ardından "False" eşdeğer dizeler içeriğini çünkü ancak `a` ve `b` aynı dize örneğine işaret etmiyor.</span><span class="sxs-lookup"><span data-stu-id="3f977-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="3f977-121">[+ İşleci](../operators/addition-operator.md#string-concatenation) dizeyi art arda ekler:</span><span class="sxs-lookup"><span data-stu-id="3f977-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="3f977-122">Bu, "Günaydın" içeren bir dize nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f977-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="3f977-123">Dizelerdir *değişmez*--bir dize nesnesi, içeriğini nesne oluşturulduktan sonra değiştirilemez, söz dizimi sağlar ancak görünür Bunu yapmak gibi.</span><span class="sxs-lookup"><span data-stu-id="3f977-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="3f977-124">Örneğin, bu kod yazdığınızda, derleyici, gerçekte yeni dizi karakteri tutmak için yeni bir dize nesnesi oluşturur ve yeni nesne atandığı `b`.</span><span class="sxs-lookup"><span data-stu-id="3f977-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="3f977-125">İçin ayrılan bellek `b` (ne zaman "h" dizesini içerdiği) sonra çöp toplama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="3f977-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="3f977-126">`[]` [İşleci](../operators/member-access-operators.md#indexer-operator-) karakterlerin tek tek salt okunur erişim için kullanılan bir `string`.</span><span class="sxs-lookup"><span data-stu-id="3f977-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="3f977-127">Geçerli değerler başlar `0` uzunluğundan daha küçük olması gerekir `string`:</span><span class="sxs-lookup"><span data-stu-id="3f977-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="3f977-128">Benzer bir biçimde `[]` işleci de kullanılabilir her bir karakteri üzerinde yineleme için bir `string`:</span><span class="sxs-lookup"><span data-stu-id="3f977-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="3f977-129">Dize değişmez değerleri, tür `string` ve teklif iki biçimde yazılır ve `@`-teklif.</span><span class="sxs-lookup"><span data-stu-id="3f977-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="3f977-130">Dize değişmez değerleri çift tırnak işaretleri (") içine alınan Teklif:</span><span class="sxs-lookup"><span data-stu-id="3f977-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="3f977-131">Dize değişmez değerleri, sabit değer herhangi bir karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3f977-131">String literals can contain any character literal.</span></span> <span data-ttu-id="3f977-132">Kaçış dizileri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="3f977-132">Escape sequences are included.</span></span> <span data-ttu-id="3f977-133">Aşağıdaki örnekte çıkış dizisi `\\` eğik için `\u0066` harfi f, için ve `\n` için yeni satır.</span><span class="sxs-lookup"><span data-stu-id="3f977-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="3f977-134">Çıkış kodu `\udddd` (burada `dddd` bir dört basamaklı sayıdır) U + Unicode karakteri temsil eden`dddd`.</span><span class="sxs-lookup"><span data-stu-id="3f977-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="3f977-135">Sekiz basamağı Unicode atlatma kodları da tanınan: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="3f977-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="3f977-136">[Verbatim dize değişmez değerleri](../tokens/verbatim.md) başlayın `@` ve ayrıca çift tırnak işaretleri içine alınır.</span><span class="sxs-lookup"><span data-stu-id="3f977-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="3f977-137">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3f977-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="3f977-138">Kaçış dizileri: avantajlarındandır harfi harfine dizeler *değil* işlendiğinde, yazma, örneğin, tam bir Windows dosya adı yapmayı kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="3f977-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="3f977-139">Çift tırnak işareti eklemek için bir @-quoted , çift, dize:</span><span class="sxs-lookup"><span data-stu-id="3f977-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="3f977-140">Temsilci türü</span><span class="sxs-lookup"><span data-stu-id="3f977-140">The delegate type</span></span>

<span data-ttu-id="3f977-141">Bir temsilci türü bildirimi için bir yöntem imzası benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3f977-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="3f977-142">Bu, dönüş değeri ve herhangi bir sayıda herhangi bir türde parametreleri vardır:</span><span class="sxs-lookup"><span data-stu-id="3f977-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="3f977-143">. NET'te, `System.Action` ve `System.Func` genel tanımları birçok genel temsilcileri için türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f977-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="3f977-144">Yeni özel temsilci türleri tanımlamak büyük olasılıkla gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3f977-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="3f977-145">Bunun yerine, belirtilen genel türlerin örneklemeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f977-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="3f977-146">A `delegate` adlandırılmış kapsüllemek için kullanılabilecek bir başvuru türü veya anonim yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f977-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="3f977-147">Temsilciler c++ işlev işaretçilerine benzer; Ancak, temsilciler, tür kullanımı uyumlu ve güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="3f977-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="3f977-148">Temsilciler uygulamalar için bkz [Temsilciler](../../programming-guide/delegates/index.md) ve [genel temsilciler](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3f977-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="3f977-149">Temsilcileri, bir temel [olayları](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f977-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="3f977-150">Temsilci adlandırılmış ve anonim bir yöntem ile ilişkilendirerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3f977-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="3f977-151">Uyumlu bir dönüş türü ve giriş parametrelerini içeren bir yöntem veya lambda ifadesiyle, temsilci örneği gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f977-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="3f977-152">Yöntem imzası izin verilen fark derecesi hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3f977-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="3f977-153">Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir.</span><span class="sxs-lookup"><span data-stu-id="3f977-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="3f977-154">Dinamik tür</span><span class="sxs-lookup"><span data-stu-id="3f977-154">The dynamic type</span></span>

<span data-ttu-id="3f977-155">`dynamic` Türü kullanan bir değişkeni gösterir ve başvuruları, üyeleri derleme zamanı tür denetimini atla için.</span><span class="sxs-lookup"><span data-stu-id="3f977-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="3f977-156">Bunun yerine, bu işlemlerin çalışma zamanında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="3f977-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="3f977-157">`dynamic` Tür COM API Office Otomasyon API'leri gibi IronPython kitaplıkları gibi dinamik API'lerine ve HTML belge nesne modeli (DOM) erişim basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="3f977-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="3f977-158">Tür `dynamic` türü gibi davranır `object` çoğu durumda.</span><span class="sxs-lookup"><span data-stu-id="3f977-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="3f977-159">Özellikle, herhangi bir null olmayan ifade olarak dönüştürülebilir `dynamic` türü.</span><span class="sxs-lookup"><span data-stu-id="3f977-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="3f977-160">`dynamic` Türü farklıdır `object` türündeki ifadeler içeren bu işlemlerde `dynamic` değil çözümlenir veya derleyici tarafından teslim türü.</span><span class="sxs-lookup"><span data-stu-id="3f977-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="3f977-161">Çalışma zamanı derleyici paketleri birlikte bilgi işlemi ve bu bilgileri daha sonra işlemi değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f977-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="3f977-162">Türü değişkenlerindeki işleminin bir parçası olarak `dynamic` türündeki değişkenler derlenmiş `object`.</span><span class="sxs-lookup"><span data-stu-id="3f977-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="3f977-163">Bu nedenle, yazın `dynamic` yalnızca çalışma zamanında değil derleme zamanında var.</span><span class="sxs-lookup"><span data-stu-id="3f977-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="3f977-164">Aşağıdaki örnek türünün değişkenini karşılaştırır `dynamic` türünde bir değişkene `object`.</span><span class="sxs-lookup"><span data-stu-id="3f977-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="3f977-165">Derleme zamanında her bir değişken türünü doğrulamak için üzerine fare işaretçisini getirin `dyn` veya `obj` içinde `WriteLine` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3f977-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="3f977-166">Aşağıdaki kod, IntelliSense kullanılabildiği bir düzenleyiciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3f977-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="3f977-167">IntelliSense gösterir **dinamik** için `dyn` ve **nesne** için `obj`.</span><span class="sxs-lookup"><span data-stu-id="3f977-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="3f977-168"><xref:System.Console.WriteLine%2A> Deyimleri çalışma zamanı türlerini görüntüler `dyn` ve `obj`.</span><span class="sxs-lookup"><span data-stu-id="3f977-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="3f977-169">Bu noktada, her ikisi de aynı türde olan tamsayı.</span><span class="sxs-lookup"><span data-stu-id="3f977-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="3f977-170">Aşağıdaki çıkış üretilir:</span><span class="sxs-lookup"><span data-stu-id="3f977-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="3f977-171">Arasındaki farkı görmek için `dyn` ve `obj` derleme zamanında bildirimler arasında aşağıdaki iki satırı ekleyin ve `WriteLine` önceki örnekte deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3f977-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="3f977-172">Derleyici Hatası tamsayı ve bir nesne ifadesinde denenen eklenmesi için bildirilen `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="3f977-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="3f977-173">Ancak, herhangi bir hata için bildirilen `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="3f977-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="3f977-174">İçeren ifade `dyn` çünkü derleme zamanında işaretlenmediği türünü `dyn` olduğu `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3f977-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="3f977-175">Aşağıdaki örnekte `dynamic` birkaç bildirimlerinde.</span><span class="sxs-lookup"><span data-stu-id="3f977-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="3f977-176">`Main` Yöntemi de derleme zamanı tür denetimini çalışma zamanı tür denetimi ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="3f977-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="3f977-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f977-177">See also</span></span>

- [<span data-ttu-id="3f977-178">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f977-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f977-179">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3f977-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="3f977-180">Olaylar</span><span class="sxs-lookup"><span data-stu-id="3f977-180">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="3f977-181">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="3f977-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="3f977-182">Dizeleri Kullanmak için En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="3f977-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="3f977-183">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="3f977-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="3f977-184">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f977-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="3f977-185">Tür test etme ve dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="3f977-185">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
- [<span data-ttu-id="3f977-186">Nasıl yapılır: güvenli bir şekilde desen eşleştirme ve olarak kullanarak AS ve is işleçlerini</span><span class="sxs-lookup"><span data-stu-id="3f977-186">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="3f977-187">İzlenecek yol: nesneler oluşturma ve dinamik kullanma</span><span class="sxs-lookup"><span data-stu-id="3f977-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
