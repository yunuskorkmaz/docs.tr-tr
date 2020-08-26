---
title: Etkileşimli Seçenekler
description: F# Etkileşimli, fsi.exe tarafından desteklenen komut satırı seçenekleri hakkında bilgi edinin.
ms.date: 08/15/2020
ms.openlocfilehash: adc8dc86f14366720e1acbf35115d4e318a76aef
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810539"
---
# <a name="f-interactive-options"></a>F# Etkileşimli seçenekleri

Bu makalede, F# Etkileşimli tarafından desteklenen komut satırı seçenekleri açıklanmaktadır `fsi.exe` . F# Etkileşimli, F # derleyicisi ile aynı komut satırı seçeneklerinin birçoğunu kabul eder, ancak aynı zamanda bazı ek seçenekleri de kabul eder.

## <a name="use-f-interactive-for-scripting"></a>Betik için F# Etkileşimli kullanma

F# Etkileşimli, `dotnet fsi` etkileşimli olarak başlatılabilir veya bir betiği çalıştırmak için komut satırından başlatılabilir. Komut satırı söz dizimi

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

F # betik dosyaları için dosya uzantısı `.fsx` .

## <a name="table-of-f-interactive-options"></a>F# Etkileşimli seçenekleri tablosu

Aşağıdaki tablo F# Etkileşimli tarafından desteklenen seçenekleri özetler. Bu seçenekleri komut satırında veya Visual Studio IDE aracılığıyla ayarlayabilirsiniz. Visual Studio IDE 'de bu seçenekleri ayarlamak için, **Araçlar** menüsünü açın, **Seçenekler**' i seçin, **F # araçlar** düğümünü genişletin ve ardından **F# Etkileşimli**' yi seçin.

Listelerin F# Etkileşimli seçenek bağımsız değişkenlerinde göründüğü, liste öğeleri noktalı virgülle ( `;` ) ayrılır.

|Seçenek|Açıklama|
|------|-----------|
|**--**|F# Etkileşimli, diğer bağımsız değişkenleri F # programı veya betiğine komut satırı bağımsız değişkenleri olarak değerlendirmek için kullanılır. Bu, **fsi. Commandbir**listesini kullanarak koda erişebilirsiniz.|
|**--Checked**[ **+**&#124;**-** ]|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--CodePage: &lt; int&gt;**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--consolecolors**[ **+**&#124;**-** ]|Uyarı ve hata iletilerini renkli olarak verir.|
|**--çapraz iyileştirme**[ **+**&#124;**-** ]|Modüller arası iyileştirmeleri etkinleştirin veya devre dışı bırakın.|
|**--Debug**[ **+**&#124;**-** ]<br /><br />**--Debug:**[**Full**&#124;**pdbonly**&#124;**Taşınabilir**&#124;**Embedded**]<br /><br />**-g**[ **+**&#124;**-** ]<br /><br />**-g:**[**Full**&#124;**pdbonly**&#124;**Taşınabilir**&#124;**Embedded**]|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--tanımla: &lt; dize&gt;**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--belirleyici**[ **+**&#124;**-** ]|Belirleyici derleme üretir (Modül sürümü GUID 'i ve zaman damgası dahil).|
|**--Exec**|Dosyaları yükledikten veya komut satırında verilen betik dosyasını çalıştırdıktan sonra F # Interactive 'e yöneltir.|
|**--fullpaths**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--GUI**[ **+**&#124;**-** ]|Windows Forms olay döngüsünü etkinleştirilir veya devre dışı bırakır. Varsayılan değer etkindir.|
|**--yardım**<br /><br />**-?**|Komut satırı söz dizimini ve her seçeneğin kısa bir açıklamasını göstermek için kullanılır.|
|**--lib: &lt; Klasör-Listele&gt;**<br /><br />**-I: &lt; Klasör-liste&gt;**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--Yükle: &lt; dosya adı&gt;**|Başlangıçta verilen kaynak kodu derler ve derlenmiş F # yapılarını oturuma yükler.|
|**--mlcompatibility**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--noframework**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md)|
|**--nologo**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--nowarn: &lt; uyarı-liste&gt;**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--optimize**[ **+**&#124;**-** ]|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--preferreduilang: &lt; lang&gt;**| Tercih edilen çıkış dili kültür adını belirtir (örneğin, ES-ES, ja-JP). |
|**--quiet**|F# Etkileşimli **stdout** akışına çıktıyı gizleyin.|
|**--alıntılar-hata ayıkla**|F # teklif değişmez değerleri ve yansıtılan tanımlardan türetilmiş ifadeler için ek hata ayıklama bilgilerinin yayınlanmasının gerektiğini belirtir. Hata ayıklama bilgileri bir F # ifade ağacı düğümünün özel özniteliklerine eklenir. Bkz. [kod teklifleri](code-quotations.md) ve [Expr. CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes).|
|**--ReadLine**[ **+**&#124;**-** ]|Etkileşimli modda sekme tamamlamayı etkinleştirin veya devre dışı bırakın.|
|**--Başvuru: &lt; dosya adı&gt;**<br /><br />**-r: &lt; dosya adı&gt;**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--edilecek çağrılar**[ **+**&#124;**-** ]|Tail Özyinelemeli işlevler için yığın çerçevesinin yeniden kullanılmasını sağlayan tail Il yönergesinin kullanımını etkinleştirin veya devre dışı bırakın. Bu seçenek varsayılan olarak etkindir.|
|**--targetprofile: &lt; dize&gt;**|Bu derlemenin hedef çerçeve profilini belirtir. Geçerli değerler `mscorlib` , `netcore` , veya `netstandard` . Varsayılan değer: `mscorlib`.|
|**--şunu kullanın: &lt; dosya adı&gt;**|Yorumlayıcıya ilk girdi olarak başlangıçta verilen dosyayı kullanmasını söyler.|
|**--utf8output**|fsc.exe derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--warn: &lt; Uyarı düzeyi&gt;**|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[ **+**&#124;**-** ]|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[ **+**&#124;**-** ]:** &lt; int-List &gt; **|**fsc.exe** derleyici seçeneği ile aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|

## <a name="f-interactive-structured-printing"></a>Yapılandırılmış yazdırma F# Etkileşimli

F# Etkileşimli ( `dotnet fsi` ), değerleri raporlamak için [yapılandırılmış düz metin biçimlendirmesinin](plaintext-formatting.md) genişletilmiş bir sürümünü kullanır.

1. `%A`Düz metin biçimlendirmesinin tüm özellikleri desteklenir ve bazıları ek olarak özelleştirilebilir.

2. Renkler çıkış Konsolu tarafından destekleniyorsa, yazdırma işlemi renklendirilir.

3. Bu dizeyi açıkça değerlendirmediğiniz takdirde, gösterilen dizelerin uzunluğuna bir sınır konur.

4. Kullanıcı tanımlı bir ayarlar kümesi nesne aracılığıyla kullanılabilir `fsi` .

Bildirilen değerler için düz metin yazdırmayı özelleştirmek için kullanılabilir ayarlar şunlardır:

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a>Ve ile özelleştirin `AddPrinter``AddPrintTransformer`

F# Etkileşimli çıktılarında yazdırma, ve kullanılarak özelleştirilebilir `fsi.AddPrinter` `fsi.AddPrintTransformer` .
İlk işlev, bir nesnenin yazdırılmasını değiştirecek metin verir. İkinci işlev bunun yerine görüntülenecek bir vekil nesne döndürür. Örneğin, aşağıdaki F # kodunu göz önünde bulundurun:

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

Örneği F# Etkileşimli ' de çalıştırırsanız, biçimlendirme seçenek kümesine göre çıkış yapılır. Bu durumda, tarih ve saat biçimlendirmesini etkiler:

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

`fsi.AddPrintTransformer` , yazdırma için bir yedek nesne vermek üzere kullanılabilir:

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

Bu çıktılar:

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

Transformatör işlevi geçirildiğinde `fsi.AddPrintTransformer` `null` , yazdırma transformatörü yok sayılır.
Bu, tür ile başlayarak herhangi bir giriş değerini filtrelemek için kullanılabilir `obj` .  Örnek:

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

Bu çıktılar:

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----|-----------|
|[Derleyici seçenekleri](compiler-options.md)|F # derleyicisi için kullanılabilen komut satırı seçeneklerini açıklar, **fsc.exe**.|
