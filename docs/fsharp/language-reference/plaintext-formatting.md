---
title: Düz metin biçimlendirme
description: 'F # uygulamalarında ve betiklerinizde printf ve diğer düz metin biçimlendirmesini nasıl kullanacağınızı öğrenin.'
ms.date: 07/22/2020
ms.openlocfilehash: 6b14633e074961757d0f0cd258d1b1667f5fd8ee
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854925"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="9d448-103">Düz metin biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="9d448-103">Plain text formatting</span></span>

<span data-ttu-id="9d448-104">F #,,, `printf` `printfn` ve ilgili işlevleri kullanılarak düz metnin tür denetimli biçimlendirmesini destekler `sprintf` .</span><span class="sxs-lookup"><span data-stu-id="9d448-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="9d448-105">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="9d448-106">çıktıyı verir</span><span class="sxs-lookup"><span data-stu-id="9d448-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="9d448-107">F # yapılandırılmış değerlerin düz metin olarak biçimlendirilmesini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d448-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="9d448-108">Örneğin, çıktıyı matris benzeri bir görünüm olarak biçimlendiren aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9d448-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="9d448-109">`%A`Biçimlendirme dizelerinde biçimi kullandığınızda yapılandırılmış düz metin biçimlendirmesi etkinleştirilir `printf` .</span><span class="sxs-lookup"><span data-stu-id="9d448-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="9d448-110">Ayrıca, çıktının ek bilgi içerdiği ve ek olarak özelleştirilebilen F # Interactive 'teki değerlerin çıktısı biçimlendirilirken de etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="9d448-111">Düz metin biçimlendirme Ayrıca, `x.ToString()` hata ayıklama, günlüğe kaydetme ve diğer araç oluşturma ile ilgili olarak oluşan, F # UNION ve kayıt değerleri üzerinde yapılan çağrılar aracılığıyla da Observable ' dır.</span><span class="sxs-lookup"><span data-stu-id="9d448-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="9d448-112">`printf`Biçimlendirme dizeleri denetleniyor</span><span class="sxs-lookup"><span data-stu-id="9d448-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="9d448-113">`printf`Biçim dizesindeki printf biçim belirticileriyle eşleşmeyen bir bağımsız değişkenle bir biçimlendirme işlevi kullanılıyorsa, derleme zamanı hatası bildirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="9d448-114">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="9d448-115">çıktıyı verir</span><span class="sxs-lookup"><span data-stu-id="9d448-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="9d448-116">Teknik olarak, `printf` ve diğer ilgili işlevleri kullanırken, F # derleyicisindeki özel bir kural, biçim dizesi olarak geçirilen dize değişmez değerini denetler ve sonraki bağımsız değişkenlerin, kullanılan biçim belirticileriyle eşleşecek şekilde doğru türde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d448-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="9d448-117">İçin biçim belirticileri`printf`</span><span class="sxs-lookup"><span data-stu-id="9d448-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="9d448-118">Biçimlerin biçim belirtimleri `printf` `%` biçimi gösteren işaretçilerle dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="9d448-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="9d448-119">Biçim yer tutucuları `%[flags][width][.precision][type]` , türün şu şekilde yorumlanması durumunda oluşur:</span><span class="sxs-lookup"><span data-stu-id="9d448-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="9d448-120">Biçim belirteci</span><span class="sxs-lookup"><span data-stu-id="9d448-120">Format specifier</span></span>   | <span data-ttu-id="9d448-121">Tür (ler)</span><span class="sxs-lookup"><span data-stu-id="9d448-121">Type(s)</span></span>        | <span data-ttu-id="9d448-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d448-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="9d448-123">bool</span><span class="sxs-lookup"><span data-stu-id="9d448-123">bool</span></span>      | <span data-ttu-id="9d448-124">Veya olarak biçimlendirilir `true``false`</span><span class="sxs-lookup"><span data-stu-id="9d448-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="9d448-125">string</span><span class="sxs-lookup"><span data-stu-id="9d448-125">string</span></span>    | <span data-ttu-id="9d448-126">Kaçışsız içerikleri olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="9d448-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="9d448-127">char</span><span class="sxs-lookup"><span data-stu-id="9d448-127">char</span></span>      | <span data-ttu-id="9d448-128">Karakter sabiti olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="9d448-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="9d448-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="9d448-129">`%d`, `%i`</span></span>         | <span data-ttu-id="9d448-130">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="9d448-130">a basic integer type</span></span> | <span data-ttu-id="9d448-131">Temel tamsayı türü imzalanmışsa, bir ondalık tamsayı olarak biçimlendirilir, imzalandı</span><span class="sxs-lookup"><span data-stu-id="9d448-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="9d448-132">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="9d448-132">a basic integer type</span></span> | <span data-ttu-id="9d448-133">İşaretsiz ondalık tamsayı olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="9d448-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="9d448-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="9d448-134">`%x`, `%X`</span></span>         | <span data-ttu-id="9d448-135">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="9d448-135">a basic integer type</span></span> | <span data-ttu-id="9d448-136">İşaretsiz onaltılık sayı (sırasıyla onaltılık basamaklar için a-f veya A-F) olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="9d448-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="9d448-137">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="9d448-137">a basic integer type</span></span> | <span data-ttu-id="9d448-138">İşaretsiz sekizlik sayı olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="9d448-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="9d448-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="9d448-139">`%e`, `%E`</span></span>         | <span data-ttu-id="9d448-140">temel kayan nokta türü</span><span class="sxs-lookup"><span data-stu-id="9d448-140">a basic floating point type</span></span> | <span data-ttu-id="9d448-141">`[-]d.dddde[sign]ddd`D 'nin tek bir ondalık basamak olduğu, yani gggg bir veya daha fazla ondalık basamak, DDD ise yalnızca üç ondalık basamak ve oturum açma `+` ya da`-`</span><span class="sxs-lookup"><span data-stu-id="9d448-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="9d448-142">temel kayan nokta türü</span><span class="sxs-lookup"><span data-stu-id="9d448-142">a basic floating point type</span></span> | <span data-ttu-id="9d448-143">`[-]dddd.dddd` `dddd` Bir veya daha fazla ondalık basamak olmak üzere, forma sahip imzalı bir değer olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="9d448-144">Ondalık noktadan önceki basamak sayısı sayının büyüklüğüne ve ondalık ayırıcıdan sonraki basamak sayısı, istenen duyarlığa bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d448-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="9d448-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="9d448-145">`%g`, `%G`</span></span> | <span data-ttu-id="9d448-146">temel kayan nokta türü</span><span class="sxs-lookup"><span data-stu-id="9d448-146">a basic floating point type</span></span> |  <span data-ttu-id="9d448-147">`%f` `%e` Belirtilen değer ve duyarlık için daha küçük olduğu için, veya biçiminde yazdırılmış bir imzalı değer olarak kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="9d448-148">bir `System.Decimal` değer</span><span class="sxs-lookup"><span data-stu-id="9d448-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="9d448-149">`"G"`Biçim belirleyicisi kullanılarak biçimlendirilir`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="9d448-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="9d448-150">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="9d448-150">any value</span></span>  |   <span data-ttu-id="9d448-151">Nesnesi kutulama yaparak ve metodunu çağırarak biçimlendirilir `System.Object.ToString()`</span><span class="sxs-lookup"><span data-stu-id="9d448-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="9d448-152">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="9d448-152">any value</span></span>  |   <span data-ttu-id="9d448-153">Varsayılan düzen ayarlarıyla [yapılandırılmış düz metin biçimlendirme](plaintext-formatting.md) kullanılarak biçimlendirildi</span><span class="sxs-lookup"><span data-stu-id="9d448-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="9d448-154">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="9d448-154">any value</span></span>  |   <span data-ttu-id="9d448-155">İki bağımsız değişken gerektirir: bir bağlam parametresini ve değeri kabul eden bir biçimlendirme işlevi ve yazdırılacak belirli değer</span><span class="sxs-lookup"><span data-stu-id="9d448-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="9d448-156">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="9d448-156">any value</span></span>  |   <span data-ttu-id="9d448-157">Bir bağımsız değişken gerektirir: bir bağlam parametresini kabul eden veya uygun metni döndüren bir biçimlendirme işlevi</span><span class="sxs-lookup"><span data-stu-id="9d448-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |

<span data-ttu-id="9d448-158">Temel tamsayı türleri `byte` ( `System.Byte` ), ( `sbyte` ) `System.SByte` , `int16` () `System.Int16` , `uint16` ( `System.UInt16` ), `int32` `System.Int32` `uint32` `System.UInt32` `int64` `System.Int64` `uint64` `System.UInt64` `nativeint` `System.IntPtr` `unativeint` `System.UIntPtr` (), (), ve ().</span><span class="sxs-lookup"><span data-stu-id="9d448-158">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="9d448-159">Temel kayan nokta türleri `float` ( `System.Double` ) ve `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="9d448-159">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="9d448-160">İsteğe bağlı genişlik, sonucun en az genişliğini gösteren bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="9d448-160">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="9d448-161">Örneğin, `%6d` bir tamsayı yazdırır, en az altı karakteri dolduracak şekilde boşluk ile önek olarak.</span><span class="sxs-lookup"><span data-stu-id="9d448-161">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="9d448-162">Width ise `*` , karşılık gelen genişliği belirtmek için fazladan bir tamsayı bağımsız değişkeni alınır.</span><span class="sxs-lookup"><span data-stu-id="9d448-162">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="9d448-163">Geçerli bayraklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d448-163">Valid flags are:</span></span>

| <span data-ttu-id="9d448-164">Bayrak</span><span class="sxs-lookup"><span data-stu-id="9d448-164">Flag</span></span>   | <span data-ttu-id="9d448-165">Etki</span><span class="sxs-lookup"><span data-stu-id="9d448-165">Effect</span></span>        | <span data-ttu-id="9d448-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d448-166">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="9d448-167">Gerekli genişliği oluşturmak için boşluk yerine sıfır ekleyin</span><span class="sxs-lookup"><span data-stu-id="9d448-167">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="9d448-168">Sonucu belirtilen genişlik içinde Sola Yasla</span><span class="sxs-lookup"><span data-stu-id="9d448-168">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="9d448-169">`+`Sayı pozitifse ( `-` negatifler için bir işareti eşlemek için) bir karakter ekleyin</span><span class="sxs-lookup"><span data-stu-id="9d448-169">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="9d448-170">boşluk karakteri</span><span class="sxs-lookup"><span data-stu-id="9d448-170">space character</span></span> | <span data-ttu-id="9d448-171">Sayı pozitif ise (örneğin, negatifler için '-' işaretini eşlemek için) fazladan bir boşluk ekleyin</span><span class="sxs-lookup"><span data-stu-id="9d448-171">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="9d448-172">Printf `#` bayrağı geçersiz ve kullanılıyorsa bir derleme zamanı hatası bildirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-172">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="9d448-173">Değerler, sabit kültür kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-173">Values are formatted using invariant culture.</span></span> <span data-ttu-id="9d448-174">Kültür ayarları, `printf` ve biçimlendirme sonuçlarının etkilenmediği durumlar dışında biçimlendirme ile ilgisiz `%O` değildir `%A` .</span><span class="sxs-lookup"><span data-stu-id="9d448-174">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="9d448-175">Daha fazla bilgi için bkz. [yapılandırılmış düz metin biçimlendirmesi](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="9d448-175">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="9d448-176">`%A`biçime</span><span class="sxs-lookup"><span data-stu-id="9d448-176">`%A` formatting</span></span>

<span data-ttu-id="9d448-177">`%A`Biçim Belirleyicisi, verileri insanlarca okunabilir bir şekilde biçimlendirmek için kullanılır ve ayrıca tanılama bilgilerini raporlamak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-177">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="9d448-178">İlkel değerler</span><span class="sxs-lookup"><span data-stu-id="9d448-178">Primitive values</span></span>

<span data-ttu-id="9d448-179">Belirteci kullanarak düz metin biçimlendirilirken `%A` , F # sayısal değerleri, soneki ve sabit kültürüyle biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-179">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="9d448-180">Kayan nokta değerleri, kayan nokta duyarlılığı 10 ' un kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-180">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="9d448-181">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-181">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="9d448-182">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-182">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="9d448-183">`%A`Tanımlayıcı kullanılırken dizeler, tırnak işaretleri kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-183">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="9d448-184">Kaçış kodları eklenmez ve bunun yerine ham karakterler yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-184">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="9d448-185">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-185">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="9d448-186">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-186">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="9d448-187">.NET değerleri</span><span class="sxs-lookup"><span data-stu-id="9d448-187">.NET values</span></span>

<span data-ttu-id="9d448-188">Tanımlayıcı kullanılarak düz metin biçimlendirilirken `%A` , F # .NET nesneleri, `x.ToString()` ve tarafından verilen varsayılan .NET ayarları kullanılarak biçimlendirilir `System.Globalization.CultureInfo.CurrentCulture` `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="9d448-188">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="9d448-189">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-189">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="9d448-190">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-190">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="9d448-191">Yapılandırılmış değerler</span><span class="sxs-lookup"><span data-stu-id="9d448-191">Structured values</span></span>

<span data-ttu-id="9d448-192">Belirteci kullanarak düz metin biçimlendirilirken `%A` , blok girintileme F # listeleri ve tanımlama grupları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-192">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="9d448-193">Bu, önceki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9d448-193">This shown in the previous example.</span></span>
<span data-ttu-id="9d448-194">Birden çok boyutlu diziler de dahil olmak üzere dizilerin yapısı da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-194">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="9d448-195">Tek boyutlu diziler sözdizimi ile gösterilir `[| ... |]` .</span><span class="sxs-lookup"><span data-stu-id="9d448-195">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="9d448-196">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-196">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="9d448-197">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-197">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="9d448-198">Varsayılan yazdırma genişliği 80 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9d448-198">The default print width is 80.</span></span>  <span data-ttu-id="9d448-199">Bu genişlik, biçim tanımlayıcıda bir yazdırma genişliği kullanılarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-199">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="9d448-200">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-200">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="9d448-201">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-201">produces</span></span>

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

<span data-ttu-id="9d448-202">0 yazdırma genişliğini belirtmek, hiçbir yazdırma genişliği kullanılmazsa sonuç olarak sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="9d448-202">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="9d448-203">Çıktıda gömülü dizelerin satır sonları içermesi dışında, tek satırlık bir metin oluşur.</span><span class="sxs-lookup"><span data-stu-id="9d448-203">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="9d448-204">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9d448-204">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="9d448-205">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-205">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="9d448-206">İçinde gösterilen dizi () değerleri için 4 derinlik sınırı kullanılır `IEnumerable` `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="9d448-206">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="9d448-207">Liste ve dizi değerleri için 100 derinlik sınırı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-207">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="9d448-208">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-208">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="9d448-209">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-209">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="9d448-210">Blok girintileme, ortak kayıt ve birleşim değerlerinin yapısı için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-210">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="9d448-211">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-211">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="9d448-212">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-212">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="9d448-213">Kullanılıyorsa `%+A` , kayıt ve birleşimlerin özel yapısı da yansıma kullanılarak da ortaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-213">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="9d448-214">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9d448-214">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="9d448-215">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-215">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="9d448-216">Büyük, döngüsel veya derin iç içe geçmiş değerler</span><span class="sxs-lookup"><span data-stu-id="9d448-216">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="9d448-217">Büyük yapılandırılmış değerler 10000 genel nesne düğümü sayısı üst sınırına biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-217">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="9d448-218">Derin iç içe geçmiş değerler 100 derinliğine biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-218">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="9d448-219">Her iki durumda da `...` çıktının bir kısmını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-219">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="9d448-220">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-220">For example,</span></span>

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

<span data-ttu-id="9d448-221">bazı parçalar olmadan büyük bir çıkış üretir:</span><span class="sxs-lookup"><span data-stu-id="9d448-221">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="9d448-222">Döngü, nesne grafiklerde algılanır ve `...` döngülerin algılandığı yerlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-222">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="9d448-223">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9d448-223">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="9d448-224">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-224">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="9d448-225">Lazy, null ve işlev değerleri</span><span class="sxs-lookup"><span data-stu-id="9d448-225">Lazy, null, and function values</span></span>

<span data-ttu-id="9d448-226">`Value is not created`Değer henüz değerlendirilmemişse, yavaş değerler veya eşit metin olarak yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-226">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="9d448-227">`null`Değer statik türünün, `null` izin verilen bir temsil olduğu bir birleşim türü olarak belirlenmediği sürece null değerler yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="9d448-227">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="9d448-228">F # işlev değerleri, dahili olarak oluşturulan kapanış adı olarak yazdırılır (örneğin,) `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="9d448-228">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="9d448-229">Düz metin biçimlendirmesini özelleştirme`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="9d448-229">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="9d448-230">`%A`Tanımlayıcı kullanılırken, `StructuredFormatDisplay` tür bildirimlerinde özniteliği varlığını dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="9d448-230">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="9d448-231">Bu, bir değeri göstermek için yedek metin ve özellik belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-231">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="9d448-232">Örnek:</span><span class="sxs-lookup"><span data-stu-id="9d448-232">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="9d448-233">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-233">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="9d448-234">Düz metin biçimlendirmesini geçersiz kılarak özelleştirin`ToString`</span><span class="sxs-lookup"><span data-stu-id="9d448-234">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="9d448-235">Varsayılan uygulama, `ToString` F # programlamasında Observable ' dır.</span><span class="sxs-lookup"><span data-stu-id="9d448-235">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="9d448-236">Genellikle, varsayılan sonuçlar programcı ile ilgili bilgi görüntüsü veya Kullanıcı çıktısında kullanım için uygun değildir ve sonuç olarak varsayılan uygulamayı geçersiz kılmak yaygın bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="9d448-236">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="9d448-237">Varsayılan olarak, F # kayıt ve birleşim türleri tarafından `ToString` kullanılan bir uygulamayla uygulamasını geçersiz kılar `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="9d448-237">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="9d448-238">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-238">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="9d448-239">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-239">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="9d448-240">Sınıf türleri için, varsayılan bir uygulama `ToString` sağlanmaz ve .net varsayılanı kullanılır ve bu da türün adını bildirir.</span><span class="sxs-lookup"><span data-stu-id="9d448-240">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="9d448-241">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9d448-241">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="9d448-242">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-242">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="9d448-243">İçin bir geçersiz kılma eklemek `ToString` daha iyi biçimlendirme sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-243">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="9d448-244">üretmez</span><span class="sxs-lookup"><span data-stu-id="9d448-244">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="9d448-245">Yapılandırılmış yazdırma F# Etkileşimli</span><span class="sxs-lookup"><span data-stu-id="9d448-245">F# Interactive structured printing</span></span>

<span data-ttu-id="9d448-246">F# Etkileşimli ( `dotnet fsi` ), değerleri raporlamak için yapılandırılmış düz metin biçimlendirmesinin genişletilmiş bir sürümünü kullanır ve ek özelleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d448-246">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="9d448-247">Daha fazla bilgi için bkz. [F# Etkileşimli](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="9d448-247">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="9d448-248">Hata ayıklama ekranları Özelleştir</span><span class="sxs-lookup"><span data-stu-id="9d448-248">Customize debug displays</span></span>

<span data-ttu-id="9d448-249">.NET için hata ayıklayıcılar, ve gibi özniteliklerin kullanımına saygı `DebuggerDisplay` `DebuggerTypeProxy` gösterir ve bu, hata ayıklayıcı İnceleme penceresinde nesnelerin yapılandırılmış görüntüsünü etkiler.</span><span class="sxs-lookup"><span data-stu-id="9d448-249">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="9d448-250">F # derleyicisi ayırt edici birleşim ve kayıt türleri için bu öznitelikleri otomatik olarak oluşturdu, ancak sınıf, arabirim veya yapı türleri değil.</span><span class="sxs-lookup"><span data-stu-id="9d448-250">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="9d448-251">Bu öznitelikler F # düz metin biçimlendirmesinde yok sayılır, ancak F # türlerinde hata ayıklarken ekranları geliştirmek için bu yöntemleri uygulamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d448-251">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d448-252">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d448-252">See also</span></span>

- [<span data-ttu-id="9d448-253">Dizeler</span><span class="sxs-lookup"><span data-stu-id="9d448-253">Strings</span></span>](strings.md)
- [<span data-ttu-id="9d448-254">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="9d448-254">Records</span></span>](records.md)
- [<span data-ttu-id="9d448-255">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="9d448-255">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="9d448-256">F# Etkileşimli</span><span class="sxs-lookup"><span data-stu-id="9d448-256">F# Interactive</span></span>](fsharp-interactive-options.md)
