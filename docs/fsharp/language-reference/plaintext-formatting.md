---
title: Düz Metin Biçimlendirmesi
description: 'F # uygulamalarında ve betiklerinizde printf ve diğer düz metin biçimlendirmesini nasıl kullanacağınızı öğrenin.'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063789"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="09bb6-103">Düz metin biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="09bb6-103">Plain text formatting</span></span>

<span data-ttu-id="09bb6-104">F #,,, `printf` `printfn` ve ilgili işlevleri kullanılarak düz metnin tür denetimli biçimlendirmesini destekler `sprintf` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="09bb6-105">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="09bb6-106">çıktıyı verir</span><span class="sxs-lookup"><span data-stu-id="09bb6-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="09bb6-107">F # yapılandırılmış değerlerin düz metin olarak biçimlendirilmesini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="09bb6-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="09bb6-108">Örneğin, çıktıyı matris benzeri bir görünüm olarak biçimlendiren aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="09bb6-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="09bb6-109">`%A`Biçimlendirme dizelerinde biçimi kullandığınızda yapılandırılmış düz metin biçimlendirmesi etkinleştirilir `printf` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="09bb6-110">Ayrıca, çıktının ek bilgi içerdiği ve ek olarak özelleştirilebilen F # Interactive 'teki değerlerin çıktısı biçimlendirilirken de etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="09bb6-111">Düz metin biçimlendirme Ayrıca, `x.ToString()` hata ayıklama, günlüğe kaydetme ve diğer araç oluşturma ile ilgili olarak oluşan, F # UNION ve kayıt değerleri üzerinde yapılan çağrılar aracılığıyla da Observable ' dır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="09bb6-112">`printf`Biçimlendirme dizeleri denetleniyor</span><span class="sxs-lookup"><span data-stu-id="09bb6-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="09bb6-113">`printf`Biçim dizesindeki printf biçim belirticileriyle eşleşmeyen bir bağımsız değişkenle bir biçimlendirme işlevi kullanılıyorsa, derleme zamanı hatası bildirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="09bb6-114">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="09bb6-115">çıktıyı verir</span><span class="sxs-lookup"><span data-stu-id="09bb6-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="09bb6-116">Teknik olarak, `printf` ve diğer ilgili işlevleri kullanırken, F # derleyicisindeki özel bir kural, biçim dizesi olarak geçirilen dize değişmez değerini denetler ve sonraki bağımsız değişkenlerin, kullanılan biçim belirticileriyle eşleşecek şekilde doğru türde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="09bb6-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="09bb6-117">İçin biçim belirticileri`printf`</span><span class="sxs-lookup"><span data-stu-id="09bb6-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="09bb6-118">Biçimlerin biçim belirtimleri `printf` `%` biçimi gösteren işaretçilerle dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="09bb6-119">Biçim yer tutucuları `%[flags][width][.precision][type]` , türün şu şekilde yorumlanması durumunda oluşur:</span><span class="sxs-lookup"><span data-stu-id="09bb6-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="09bb6-120">Biçim belirteci</span><span class="sxs-lookup"><span data-stu-id="09bb6-120">Format specifier</span></span>   | <span data-ttu-id="09bb6-121">Tür (ler)</span><span class="sxs-lookup"><span data-stu-id="09bb6-121">Type(s)</span></span>        | <span data-ttu-id="09bb6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09bb6-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="09bb6-123">bool</span><span class="sxs-lookup"><span data-stu-id="09bb6-123">bool</span></span>      | <span data-ttu-id="09bb6-124">Veya olarak biçimlendirilir `true``false`</span><span class="sxs-lookup"><span data-stu-id="09bb6-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="09bb6-125">string</span><span class="sxs-lookup"><span data-stu-id="09bb6-125">string</span></span>    | <span data-ttu-id="09bb6-126">Kaçışsız içerikleri olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="09bb6-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="09bb6-127">char</span><span class="sxs-lookup"><span data-stu-id="09bb6-127">char</span></span>      | <span data-ttu-id="09bb6-128">Karakter sabiti olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="09bb6-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="09bb6-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="09bb6-129">`%d`, `%i`</span></span>         | <span data-ttu-id="09bb6-130">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="09bb6-130">a basic integer type</span></span> | <span data-ttu-id="09bb6-131">Temel tamsayı türü imzalanmışsa, bir ondalık tamsayı olarak biçimlendirilir, imzalandı</span><span class="sxs-lookup"><span data-stu-id="09bb6-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="09bb6-132">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="09bb6-132">a basic integer type</span></span> | <span data-ttu-id="09bb6-133">İşaretsiz ondalık tamsayı olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="09bb6-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="09bb6-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="09bb6-134">`%x`, `%X`</span></span>         | <span data-ttu-id="09bb6-135">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="09bb6-135">a basic integer type</span></span> | <span data-ttu-id="09bb6-136">İşaretsiz onaltılık sayı (sırasıyla onaltılık basamaklar için a-f veya A-F) olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="09bb6-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="09bb6-137">temel bir tamsayı türü</span><span class="sxs-lookup"><span data-stu-id="09bb6-137">a basic integer type</span></span> | <span data-ttu-id="09bb6-138">İşaretsiz sekizlik sayı olarak biçimlendirilir</span><span class="sxs-lookup"><span data-stu-id="09bb6-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="09bb6-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="09bb6-139">`%e`, `%E`</span></span>         | <span data-ttu-id="09bb6-140">temel kayan nokta türü</span><span class="sxs-lookup"><span data-stu-id="09bb6-140">a basic floating point type</span></span> | <span data-ttu-id="09bb6-141">`[-]d.dddde[sign]ddd`D 'nin tek bir ondalık basamak olduğu, yani gggg bir veya daha fazla ondalık basamak, DDD ise yalnızca üç ondalık basamak ve oturum açma `+` ya da`-`</span><span class="sxs-lookup"><span data-stu-id="09bb6-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="09bb6-142">temel kayan nokta türü</span><span class="sxs-lookup"><span data-stu-id="09bb6-142">a basic floating point type</span></span> | <span data-ttu-id="09bb6-143">`[-]dddd.dddd` `dddd` Bir veya daha fazla ondalık basamak olmak üzere, forma sahip imzalı bir değer olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="09bb6-144">Ondalık noktadan önceki basamak sayısı sayının büyüklüğüne ve ondalık ayırıcıdan sonraki basamak sayısı, istenen duyarlığa bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="09bb6-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="09bb6-145">`%g`, `%G`</span></span> | <span data-ttu-id="09bb6-146">temel kayan nokta türü</span><span class="sxs-lookup"><span data-stu-id="09bb6-146">a basic floating point type</span></span> |  <span data-ttu-id="09bb6-147">`%f` `%e` Belirtilen değer ve duyarlık için daha küçük olduğu için, veya biçiminde yazdırılmış bir imzalı değer olarak kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="09bb6-148">bir `System.Decimal` değer</span><span class="sxs-lookup"><span data-stu-id="09bb6-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="09bb6-149">`"G"`Biçim belirleyicisi kullanılarak biçimlendirilir`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="09bb6-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="09bb6-150">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="09bb6-150">any value</span></span>  |   <span data-ttu-id="09bb6-151">Nesnesi kutulama yaparak ve metodunu çağırarak biçimlendirilir `System.Object.ToString()`</span><span class="sxs-lookup"><span data-stu-id="09bb6-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="09bb6-152">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="09bb6-152">any value</span></span>  |   <span data-ttu-id="09bb6-153">Varsayılan düzen ayarlarıyla [yapılandırılmış düz metin biçimlendirme](plaintext-formatting.md) kullanılarak biçimlendirildi</span><span class="sxs-lookup"><span data-stu-id="09bb6-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="09bb6-154">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="09bb6-154">any value</span></span>  |   <span data-ttu-id="09bb6-155">İki bağımsız değişken gerektirir: bir bağlam parametresini ve değeri kabul eden bir biçimlendirme işlevi ve yazdırılacak belirli değer</span><span class="sxs-lookup"><span data-stu-id="09bb6-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="09bb6-156">herhangi bir değer</span><span class="sxs-lookup"><span data-stu-id="09bb6-156">any value</span></span>  |   <span data-ttu-id="09bb6-157">Bir bağımsız değişken gerektirir: bir bağlam parametresini kabul eden veya uygun metni döndüren bir biçimlendirme işlevi</span><span class="sxs-lookup"><span data-stu-id="09bb6-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |
| `%%` | <span data-ttu-id="09bb6-158">(yok)</span><span class="sxs-lookup"><span data-stu-id="09bb6-158">(none)</span></span>  |   <span data-ttu-id="09bb6-159">Bağımsız değişken gerektirmez ve bir salt yüzde işareti yazdırır:`%`</span><span class="sxs-lookup"><span data-stu-id="09bb6-159">Requires no arguments and prints a plain percent sign: `%`</span></span> |

<span data-ttu-id="09bb6-160">Temel tamsayı türleri `byte` ( `System.Byte` ), ( `sbyte` ) `System.SByte` , `int16` () `System.Int16` , `uint16` ( `System.UInt16` ), `int32` `System.Int32` `uint32` `System.UInt32` `int64` `System.Int64` `uint64` `System.UInt64` `nativeint` `System.IntPtr` `unativeint` `System.UIntPtr` (), (), ve ().</span><span class="sxs-lookup"><span data-stu-id="09bb6-160">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="09bb6-161">Temel kayan nokta türleri `float` ( `System.Double` ) ve `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="09bb6-161">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="09bb6-162">İsteğe bağlı genişlik, sonucun en az genişliğini gösteren bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-162">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="09bb6-163">Örneğin, `%6d` bir tamsayı yazdırır, en az altı karakteri dolduracak şekilde boşluk ile önek olarak.</span><span class="sxs-lookup"><span data-stu-id="09bb6-163">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="09bb6-164">Width ise `*` , karşılık gelen genişliği belirtmek için fazladan bir tamsayı bağımsız değişkeni alınır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-164">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="09bb6-165">Geçerli bayraklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="09bb6-165">Valid flags are:</span></span>

| <span data-ttu-id="09bb6-166">Bayrak</span><span class="sxs-lookup"><span data-stu-id="09bb6-166">Flag</span></span>   | <span data-ttu-id="09bb6-167">Etki</span><span class="sxs-lookup"><span data-stu-id="09bb6-167">Effect</span></span>        | <span data-ttu-id="09bb6-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09bb6-168">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="09bb6-169">Gerekli genişliği oluşturmak için boşluk yerine sıfır ekleyin</span><span class="sxs-lookup"><span data-stu-id="09bb6-169">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="09bb6-170">Sonucu belirtilen genişlik içinde Sola Yasla</span><span class="sxs-lookup"><span data-stu-id="09bb6-170">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="09bb6-171">`+`Sayı pozitifse ( `-` negatifler için bir işareti eşlemek için) bir karakter ekleyin</span><span class="sxs-lookup"><span data-stu-id="09bb6-171">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="09bb6-172">boşluk karakteri</span><span class="sxs-lookup"><span data-stu-id="09bb6-172">space character</span></span> | <span data-ttu-id="09bb6-173">Sayı pozitif ise (örneğin, negatifler için '-' işaretini eşlemek için) fazladan bir boşluk ekleyin</span><span class="sxs-lookup"><span data-stu-id="09bb6-173">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="09bb6-174">Printf `#` bayrağı geçersiz ve kullanılıyorsa bir derleme zamanı hatası bildirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-174">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="09bb6-175">Değerler, sabit kültür kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-175">Values are formatted using invariant culture.</span></span> <span data-ttu-id="09bb6-176">Kültür ayarları, `printf` ve biçimlendirme sonuçlarının etkilenmediği durumlar dışında biçimlendirme ile ilgisiz `%O` değildir `%A` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-176">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="09bb6-177">Daha fazla bilgi için bkz. [yapılandırılmış düz metin biçimlendirmesi](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="09bb6-177">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="09bb6-178">`%A`biçime</span><span class="sxs-lookup"><span data-stu-id="09bb6-178">`%A` formatting</span></span>

<span data-ttu-id="09bb6-179">`%A`Biçim Belirleyicisi, verileri insanlarca okunabilir bir şekilde biçimlendirmek için kullanılır ve ayrıca tanılama bilgilerini raporlamak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-179">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="09bb6-180">İlkel değerler</span><span class="sxs-lookup"><span data-stu-id="09bb6-180">Primitive values</span></span>

<span data-ttu-id="09bb6-181">Belirteci kullanarak düz metin biçimlendirilirken `%A` , F # sayısal değerleri, soneki ve sabit kültürüyle biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-181">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="09bb6-182">Kayan nokta değerleri, kayan nokta duyarlılığı 10 ' un kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-182">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="09bb6-183">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-183">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="09bb6-184">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-184">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="09bb6-185">`%A`Tanımlayıcı kullanılırken dizeler, tırnak işaretleri kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-185">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="09bb6-186">Kaçış kodları eklenmez ve bunun yerine ham karakterler yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-186">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="09bb6-187">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-187">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="09bb6-188">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-188">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="09bb6-189">.NET değerleri</span><span class="sxs-lookup"><span data-stu-id="09bb6-189">.NET values</span></span>

<span data-ttu-id="09bb6-190">Tanımlayıcı kullanılarak düz metin biçimlendirilirken `%A` , F # .NET nesneleri, `x.ToString()` ve tarafından verilen varsayılan .NET ayarları kullanılarak biçimlendirilir `System.Globalization.CultureInfo.CurrentCulture` `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-190">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="09bb6-191">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-191">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="09bb6-192">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-192">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="09bb6-193">Yapılandırılmış değerler</span><span class="sxs-lookup"><span data-stu-id="09bb6-193">Structured values</span></span>

<span data-ttu-id="09bb6-194">Belirteci kullanarak düz metin biçimlendirilirken `%A` , blok girintileme F # listeleri ve tanımlama grupları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-194">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="09bb6-195">Bu, önceki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-195">This shown in the previous example.</span></span>
<span data-ttu-id="09bb6-196">Birden çok boyutlu diziler de dahil olmak üzere dizilerin yapısı da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-196">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="09bb6-197">Tek boyutlu diziler sözdizimi ile gösterilir `[| ... |]` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-197">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="09bb6-198">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-198">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="09bb6-199">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-199">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="09bb6-200">Varsayılan yazdırma genişliği 80 ' dir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-200">The default print width is 80.</span></span>  <span data-ttu-id="09bb6-201">Bu genişlik, biçim tanımlayıcıda bir yazdırma genişliği kullanılarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-201">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="09bb6-202">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-202">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="09bb6-203">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-203">produces</span></span>

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

<span data-ttu-id="09bb6-204">0 yazdırma genişliğini belirtmek, hiçbir yazdırma genişliği kullanılmazsa sonuç olarak sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-204">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="09bb6-205">Çıktıda gömülü dizelerin satır sonları içermesi dışında, tek satırlık bir metin oluşur.</span><span class="sxs-lookup"><span data-stu-id="09bb6-205">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="09bb6-206">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="09bb6-206">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="09bb6-207">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-207">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="09bb6-208">İçinde gösterilen dizi () değerleri için 4 derinlik sınırı kullanılır `IEnumerable` `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-208">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="09bb6-209">Liste ve dizi değerleri için 100 derinlik sınırı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-209">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="09bb6-210">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-210">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="09bb6-211">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-211">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="09bb6-212">Blok girintileme, ortak kayıt ve birleşim değerlerinin yapısı için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-212">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="09bb6-213">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-213">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="09bb6-214">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-214">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="09bb6-215">Kullanılıyorsa `%+A` , kayıt ve birleşimlerin özel yapısı da yansıma kullanılarak da ortaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-215">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="09bb6-216">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="09bb6-216">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="09bb6-217">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-217">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="09bb6-218">Büyük, döngüsel veya derin iç içe geçmiş değerler</span><span class="sxs-lookup"><span data-stu-id="09bb6-218">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="09bb6-219">Büyük yapılandırılmış değerler 10000 genel nesne düğümü sayısı üst sınırına biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-219">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="09bb6-220">Derin iç içe geçmiş değerler 100 derinliğine biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-220">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="09bb6-221">Her iki durumda da `...` çıktının bir kısmını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-221">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="09bb6-222">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-222">For example,</span></span>

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

<span data-ttu-id="09bb6-223">bazı parçalar olmadan büyük bir çıkış üretir:</span><span class="sxs-lookup"><span data-stu-id="09bb6-223">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="09bb6-224">Döngü, nesne grafiklerde algılanır ve `...` döngülerin algılandığı yerlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-224">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="09bb6-225">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="09bb6-225">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="09bb6-226">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-226">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="09bb6-227">Lazy, null ve işlev değerleri</span><span class="sxs-lookup"><span data-stu-id="09bb6-227">Lazy, null, and function values</span></span>

<span data-ttu-id="09bb6-228">`Value is not created`Değer henüz değerlendirilmemişse, yavaş değerler veya eşit metin olarak yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-228">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="09bb6-229">`null`Değer statik türünün, `null` izin verilen bir temsil olduğu bir birleşim türü olarak belirlenmediği sürece null değerler yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-229">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="09bb6-230">F # işlev değerleri, dahili olarak oluşturulan kapanış adı olarak yazdırılır (örneğin,) `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-230">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="09bb6-231">Düz metin biçimlendirmesini özelleştirme`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="09bb6-231">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="09bb6-232">`%A`Tanımlayıcı kullanılırken, `StructuredFormatDisplay` tür bildirimlerinde özniteliği varlığını dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-232">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="09bb6-233">Bu, bir değeri göstermek için yedek metin ve özellik belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-233">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="09bb6-234">Örnek:</span><span class="sxs-lookup"><span data-stu-id="09bb6-234">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="09bb6-235">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-235">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="09bb6-236">Düz metin biçimlendirmesini geçersiz kılarak özelleştirin`ToString`</span><span class="sxs-lookup"><span data-stu-id="09bb6-236">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="09bb6-237">Varsayılan uygulama, `ToString` F # programlamasında Observable ' dır.</span><span class="sxs-lookup"><span data-stu-id="09bb6-237">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="09bb6-238">Genellikle, varsayılan sonuçlar programcı ile ilgili bilgi görüntüsü veya Kullanıcı çıktısında kullanım için uygun değildir ve sonuç olarak varsayılan uygulamayı geçersiz kılmak yaygın bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-238">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="09bb6-239">Varsayılan olarak, F # kayıt ve birleşim türleri tarafından `ToString` kullanılan bir uygulamayla uygulamasını geçersiz kılar `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="09bb6-239">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="09bb6-240">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-240">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="09bb6-241">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-241">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="09bb6-242">Sınıf türleri için, varsayılan bir uygulama `ToString` sağlanmaz ve .net varsayılanı kullanılır ve bu da türün adını bildirir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-242">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="09bb6-243">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="09bb6-243">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="09bb6-244">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-244">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="09bb6-245">İçin bir geçersiz kılma eklemek `ToString` daha iyi biçimlendirme sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-245">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="09bb6-246">üretmez</span><span class="sxs-lookup"><span data-stu-id="09bb6-246">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="09bb6-247">Yapılandırılmış yazdırma F# Etkileşimli</span><span class="sxs-lookup"><span data-stu-id="09bb6-247">F# Interactive structured printing</span></span>

<span data-ttu-id="09bb6-248">F# Etkileşimli ( `dotnet fsi` ), değerleri raporlamak için yapılandırılmış düz metin biçimlendirmesinin genişletilmiş bir sürümünü kullanır ve ek özelleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="09bb6-248">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="09bb6-249">Daha fazla bilgi için bkz. [F# Etkileşimli](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="09bb6-249">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="09bb6-250">Hata ayıklama ekranları Özelleştir</span><span class="sxs-lookup"><span data-stu-id="09bb6-250">Customize debug displays</span></span>

<span data-ttu-id="09bb6-251">.NET için hata ayıklayıcılar, ve gibi özniteliklerin kullanımına saygı `DebuggerDisplay` `DebuggerTypeProxy` gösterir ve bu, hata ayıklayıcı İnceleme penceresinde nesnelerin yapılandırılmış görüntüsünü etkiler.</span><span class="sxs-lookup"><span data-stu-id="09bb6-251">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="09bb6-252">F # derleyicisi ayırt edici birleşim ve kayıt türleri için bu öznitelikleri otomatik olarak oluşturdu, ancak sınıf, arabirim veya yapı türleri değil.</span><span class="sxs-lookup"><span data-stu-id="09bb6-252">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="09bb6-253">Bu öznitelikler F # düz metin biçimlendirmesinde yok sayılır, ancak F # türlerinde hata ayıklarken ekranları geliştirmek için bu yöntemleri uygulamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="09bb6-253">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="09bb6-254">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09bb6-254">See also</span></span>

- [<span data-ttu-id="09bb6-255">Dizeler</span><span class="sxs-lookup"><span data-stu-id="09bb6-255">Strings</span></span>](strings.md)
- [<span data-ttu-id="09bb6-256">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="09bb6-256">Records</span></span>](records.md)
- [<span data-ttu-id="09bb6-257">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="09bb6-257">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="09bb6-258">F# Etkileşimli</span><span class="sxs-lookup"><span data-stu-id="09bb6-258">F# Interactive</span></span>](fsharp-interactive-options.md)
