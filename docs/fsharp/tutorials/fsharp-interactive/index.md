---
title: F# Etkileşimli (DotNet) başvurusu
description: 'F # kodunu konsolda etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için F# Etkileşimli (DotNet fsi) nasıl kullanılacağını öğrenin.'
ms.date: 10/31/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 770ac24feababcfc840ae26196ba8b6180d378a0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282019"
---
# <a name="interactive-programming-with-f"></a>F ile etkileşimli programlama\#

F# Etkileşimli (DotNet fsi), konsolda F # kodunu etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için kullanılır. Diğer bir deyişle, F # Interactive F # dili için bir REPL (okuma, değerlendirme, yazdırma döngüsü) yürütür.

Konsolundan F# Etkileşimli çalıştırmak için, öğesini çalıştırın `dotnet fsi` . `dotnet fsi`Herhangi bir .NET SDK 'sında bulabilirsiniz.

Kullanılabilen komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [F# etkileşimli seçenekleri](../../language-reference/fsharp-interactive-options.md).

## <a name="executing-code-directly-in-f-interactive"></a>Kodu doğrudan F# Etkileşimli yürütme

F# Etkileşimli bir REPL (Read-eval-PRINT döngüsü) olduğundan, kodu etkileşimli bir şekilde yürütebilirsiniz. Komut satırından yürüttükten sonra etkileşimli bir oturum örneği aşağıda verilmiştir `dotnet fsi` :

```console
Microsoft (R) F# Interactive version 11.0.0.0 for F# 5.0
Copyright (c) Microsoft Corporation. All Rights Reserved.

For help type #help;;

> let square x = x *  x;;
val square : x:int -> int

> square 12;;
val it : int = 144

> printfn "Hello, FSI!"
- ;;
Hello, FSI!
val it : unit = ()
```

İki ana şey fark edersiniz:

1. Değerlendirilecek bir çift noktalı virgül () ile tüm kod sonlandırılmalıdır `;;`
2. Kod değerlendirilir ve bir değer olarak depolanır `it` . Etkileşimli olarak başvurabilirsiniz `it` .

F# Etkileşimli, çok satırlı girişi de destekler. Gönderiminizi bir çift noktalı virgül () ile sonlandırın `;;` . F# Etkileşimli tarafından yapıştırılmış ve değerlendirilen aşağıdaki kod parçacığını göz önünde bulundurun:

```console
> let getOddSquares xs =
-     xs
-     |> List.filter (fun x -> x % 2 <> 0)
-     |> List.map (fun x -> x * x)
-
- printfn "%A" (getOddSquares [1..10]);;
[1; 9; 25; 49; 81]
val getOddSquares : xs:int list -> int list
val it : unit = ()

>
```

Kodun biçimlendirmesi korunur ve girdiyi sonlandıran bir Double semiclon ( `;;` ) vardır. F# Etkileşimli daha sonra kodu değerlendirdi ve sonuçları yazdırılmıştır!

## <a name="scripting-with-f"></a>F ile betik oluşturma\#

F# Etkileşimli, kodu etkileşimli olarak değerlendirmek harika bir öğrenme aracı olabilir, ancak normal bir düzenleyicide kod yazmak kadar üretken olduğunu hızlıca bulabilirsiniz. Normal kod düzenlemesini desteklemek için F # betikleri yazabilirsiniz.

Betikler **. FSX** dosya uzantısını kullanır. Kaynak kodu derlemek ve daha sonra derlenen derlemeyi çalıştırmak yerine **DotNet fsi** 'yi çalıştırabilir ve f # Kaynak Kodu betiğinin dosya adını belirtebilir ve f # Interactive kodu okur ve gerçek zamanlı olarak yürütür. Örneğin, aşağıdaki betiği göz önünde bulundurun `Script.fsx` :

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

getOddSquares [1..10]
```

Makinenizde bu dosya oluşturulduğunda, ile çalıştırabilir `dotnet fsi` ve doğrudan Terminal pencerenizde çıktıyı görebilirsiniz:

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

F # Scripting, [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio Code](../../get-started/get-started-vscode.md)ve [Mac için Visual Studio](../../get-started/get-started-visual-studio-for-mac.md)yerel olarak desteklenir.

## <a name="referencing-packages-in-f-interactive"></a>F# Etkileşimli gelen paketlere başvurma

> [!NOTE] Paket yönetimi bir F # 5 özelliğidir ve şu anda en son .NET 5 SDK kullanılarak kullanılabilir.

F# Etkileşimli, `#r "nuget:"` söz dizimi ve isteğe bağlı bir sürümle NuGet paketlerine başvurmayı destekler:

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

Bir sürüm belirtilmemişse, en yüksek önizleme dışı paket alınır. Belirli bir sürüme başvurmak için sürümü bir virgül ile tanıtın. Bu, bir paketin önizleme sürümüne başvururken yararlı olabilir. Örneğin, [Diffsharp](https://diffsharp.github.io/)'un önizleme sürümünü kullanarak bu betiği göz önünde bulundurun:

```fsharp
#r "nuget: DiffSharp-lite,1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn "%A" (f (dsharp.tensor 1.2))
```

Bir komut dosyasında istediğiniz sayıda paket başvurusu belirtebilirsiniz.

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a>F # Interactive ile disk üzerindeki derlemelere başvurma

Alternatif olarak, disk üzerinde bir derlemeniz varsa ve bir betikte başvurmak istiyorsanız, `#r` bir derleme belirtmek için söz dizimini kullanabilirsiniz. Aşağıdaki kodu, içinde derlenmiş bir projede göz önünde bulundurun `MyAssembly.dll` :

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

Derlenmiş bir şekilde, buna benzer şekilde adlandırılan bir dosyada başvurabilirsiniz `Script.fsx` :

```fsharp
#r "path/to/MyAssembly.dll"

printfn "%A" (MyAssembly.myFunction 10 40)
```

Çıktı aşağıdaki şekilde olacaktır:

```console
dotnet fsi Script.fsx
90
```

Bir komut dosyasında istediğiniz sayıda derleme başvurusu belirtebilirsiniz.

## <a name="loading-other-scripts"></a>Diğer betikleri yükleme

Komut dosyası oluştururken, farklı görevler için farklı betikler kullanılması genellikle faydalı olabilir. Bazen koddaki kodu başka bir kodla yeniden kullanmak isteyebilirsiniz. İçeriğini dosyanıza kopyalamak-yapıştırmak yerine, ile basit yükleme ve değerlendirme yapabilirsiniz `#load` .

Aşağıdakileri göz önünde bulundurun `Script1.fsx` :

```fsharp
let square x = x * x
```

Ve kullanan dosya `Script2.fsx` :

```fsharp
#load "Script1.fsx"
open Script1

printfn "%d" (square 12)
```

`open Script1`Bildirimin gerekli olduğunu unutmayın. Bunun nedeni, bir F # betiğindeki yapıların içinde bulunduğu komut dosyasının adı olan en üst düzey bir modüle derlenmesinden kaynaklanır.

`Script2.fsx`Şöyle değerlendirebilirsiniz:

```console
dotnet fsi Script2.fsx
144
```

`#load`Bir komut dosyasında istediğiniz kadar çok yönergesi belirtebilirsiniz.

## <a name="using-the-fsi-object-in-f-code"></a>`fsi`F # kodundaki nesneyi kullanma

F # betikleri `fsi` , F# Etkileşimli oturumunu temsil eden özel bir nesneye erişebilir. Çıktı biçimlendirme gibi şeyleri özelleştirmenizi sağlar. Komut satırı bağımsız değişkenlerine de erişebilirsiniz.

Aşağıdaki örnek, komut satırı bağımsız değişkenlerinin nasıl alınacağını ve kullanılacağını göstermektedir:

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn "%s" arg
```

Değerlendirildiğinde, tüm bağımsız değişkenleri yazdırır. İlk bağımsız değişken her zaman değerlendirilen betiğin adıdır:

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

`System.Environment.GetCommandLineArgs()`Aynı bağımsız değişkenlere erişmek için de kullanabileceğinizi unutmayın.

## <a name="f-interactive-directive-reference"></a>F# Etkileşimli yönerge başvurusu

`#r` `#load` Daha önce görülen ve yönergeleri yalnızca F# etkileşimli kullanılabilir. Yalnızca F# Etkileşimli kullanılabilen çeşitli yönergeler vardır:

|Deki|Açıklama|
|---------|-----------|
|`#r "nuget:..."`|NuGet 'ten bir pakete başvurur|
|`#r "assembly-name.dll"`|Diskteki bir derlemeye başvurur|
|`#load "file-name.fsx"`|Bir kaynak dosyayı okur, derler ve çalıştırır.|
|`#help`|Kullanılabilir yönergeler hakkındaki bilgileri görüntüler.|
|`#I`|Bir derleme arama yolunu tırnak işaretleri halinde belirtir.|
|`#quit`|F# Etkileşimli oturumunu sonlandırır.|
|`#time "on"` veya `#time "off"`|, `#time` Performans bilgilerinin görüntülenip görüntülenmeyeceğini gösterir. `"on"`F# Etkileşimli, yorumlanan ve yürütülen kodun her bölümü için gerçek zamanlı, CPU süresini ve çöp toplama bilgilerini ölçer.|

F# Etkileşimli dosya veya yolları belirttiğinizde, bir dize sabit değeri beklenmektedir. Bu nedenle, dosyalar ve yollar tırnak işaretleri içinde olmalı ve normal kaçış karakterleri de geçerlidir. `@`Karakteri, bir yolu içeren dizeyi tam bir dize olarak yorumlamasını F# Etkileşimli neden olması için kullanabilirsiniz. Bu, F# Etkileşimli kaçış karakterlerini yoksaymasına neden olur.

## <a name="interactive-and-compiled-preprocessor-directives"></a>Etkileşimli ve derlenmiş Önişlemci yönergeleri

Etkileşimli olarak çalıştırdığınız veya bir betiği çalıştırdığınıza bakılmaksızın F# Etkileşimli kod derlerken **etkileşimli** sembol tanımlanmıştır. Derleyicide kod derlerken, **derlenen** sembol tanımlanmıştır. Bu nedenle, kodun derlenmiş ve etkileşimli modlarda farklı olması gerekiyorsa, bu ön işlemci yönergelerini koşullu derleme için kullanabilirsiniz. Örneğin:

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a>Visual Studio 'da F# Etkileşimli kullanma

Visual Studio aracılığıyla F# Etkileşimli çalıştırmak için **F# Etkileşimli** etiketli uygun araç çubuğu düğmesine tıklayabilir veya **Ctrl + Alt + F** tuşlarına basın. Bunu yapmak, F# Etkileşimli oturum çalıştıran bir araç penceresi olan etkileşimli pencereyi açar. Ayrıca etkileşimli pencerede çalıştırmak istediğiniz kod ve **Alt + Enter** tuş birleşimine basabilirsiniz. F# Etkileşimli, **F# Etkileşimli** etiketli bir araç penceresinde başlatılır. Bu tuş birleşimini kullandığınızda, düzenleyici penceresinin odağa sahip olduğundan emin olun.

Konsolunu veya Visual Studio 'Yu kullanıp kullanmayacağınızı bir komut istemi belirir ve yorumlayıcı, girişinizi bekler. Kodu, kod dosyasında olduğu gibi girebilirsiniz. Kodu derlemek ve yürütmek için, bir satırı veya birkaç giriş satırını sonlandırmak üzere iki noktalı virgül ( **;;** ) girin.

F# Etkileşimli kodu derlemeye çalışır ve başarılı olursa, kodu yürütür ve derlenen türlerin ve değerlerin imzasını yazdırır. Hata oluşursa yorumlayıcı hata iletilerini yazdırır.

Aynı oturumda girilen kod, daha önce girilmiş olan her türlü yapıya erişebilir, böylece programları oluşturabilirsiniz. Araç penceresindeki kapsamlı bir arabellek, gerekirse kodu bir dosyaya kopyalamanızı sağlar.

Visual Studio 'da çalıştırıldığında F# Etkileşimli projenizden bağımsız olarak çalışır. bu nedenle, örneğin, işlev için kodu etkileşimli pencereye kopyalamadıkça, projenizde tanımlanan yapıları F# Etkileşimli kullanamazsınız.

Ayarları ayarlayarak F# Etkileşimli komut satırı bağımsız değişkenlerini (Seçenekler) kontrol edebilirsiniz. **Araçlar** menüsünde **Seçenekler...** ' i seçin ve ardından **F # araçları** ' nı genişletin. Değiştirebileceğiniz iki ayar F# Etkileşimli seçenekleridir ve **64 bit F# Etkileşimli** ayarıdır ve bu, yalnızca 64 bit makinede F# Etkileşimli çalıştırıyorsanız geçerlidir. Bu ayar, 32 bit veya 64 bit işlem olarak çalıştırılıp çalıştırılmadığını belirleyen **fsi.exe** veya **fsianycpu.exe** adanmış 64 bitlik sürümünü çalıştırmak isteyip istemediğinizi belirler.

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----|-----------|
|[F# Etkileşimli Seçenekleri](../../language-reference/fsharp-interactive-options.md)|F# Etkileşimli fsi.exe için komut satırı sözdizimini ve seçeneklerini açıklar.|
