---
title: F# Etkileşimli (DotNet) başvurusu
description: 'F # kodunu konsolda etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için F# Etkileşimli (DotNet fsi) nasıl kullanılacağını öğrenin.'
ms.date: 11/29/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 92177c41dc6b31d9186bae8176f85787e2fb89e0
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438049"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="d0858-103">F ile etkileşimli programlama\#</span><span class="sxs-lookup"><span data-stu-id="d0858-103">Interactive programming with F\#</span></span>

<span data-ttu-id="d0858-104">F# Etkileşimli (DotNet fsi), konsolda F # kodunu etkileşimli olarak çalıştırmak veya F # betiklerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0858-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="d0858-105">Diğer bir deyişle, F # Interactive F # dili için bir REPL (okuma, değerlendirme, yazdırma döngüsü) yürütür.</span><span class="sxs-lookup"><span data-stu-id="d0858-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="d0858-106">Konsolundan F# Etkileşimli çalıştırmak için, öğesini çalıştırın `dotnet fsi` .</span><span class="sxs-lookup"><span data-stu-id="d0858-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="d0858-107">`dotnet fsi`Herhangi bir .NET SDK 'sında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="d0858-108">Kullanılabilir komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [F# etkileşimli seçenekleri](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="d0858-108">For information about available command-line options, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

## <a name="executing-code-directly-in-f-interactive"></a><span data-ttu-id="d0858-109">Kodu doğrudan F# Etkileşimli yürütme</span><span class="sxs-lookup"><span data-stu-id="d0858-109">Executing code directly in F# Interactive</span></span>

<span data-ttu-id="d0858-110">F# Etkileşimli bir REPL (Read-eval-PRINT döngüsü) olduğundan, kodu etkileşimli bir şekilde yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-110">Because F# Interactive is a REPL (read-eval-print loop), you can execute code interactively in it.</span></span> <span data-ttu-id="d0858-111">Komut satırından yürüttükten sonra etkileşimli bir oturum örneği aşağıda verilmiştir `dotnet fsi` :</span><span class="sxs-lookup"><span data-stu-id="d0858-111">Here is an example of an interactive session after executing `dotnet fsi` from the command line:</span></span>

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

<span data-ttu-id="d0858-112">İki ana şey fark edersiniz:</span><span class="sxs-lookup"><span data-stu-id="d0858-112">You'll notice two main things:</span></span>

1. <span data-ttu-id="d0858-113">Değerlendirilecek bir çift noktalı virgül () ile tüm kod sonlandırılmalıdır `;;`</span><span class="sxs-lookup"><span data-stu-id="d0858-113">All code must be terminated with a double semicolon (`;;`) to be evaluated</span></span>
2. <span data-ttu-id="d0858-114">Kod değerlendirilir ve bir değer olarak depolanır `it` .</span><span class="sxs-lookup"><span data-stu-id="d0858-114">Code is evaluated and stored in an `it` value.</span></span> <span data-ttu-id="d0858-115">Etkileşimli olarak başvurabilirsiniz `it` .</span><span class="sxs-lookup"><span data-stu-id="d0858-115">You can reference `it` interactively.</span></span>

<span data-ttu-id="d0858-116">F# Etkileşimli, çok satırlı girişi de destekler.</span><span class="sxs-lookup"><span data-stu-id="d0858-116">F# Interactive also supports multi-line input.</span></span> <span data-ttu-id="d0858-117">Gönderiminizi bir çift noktalı virgül () ile sonlandırın `;;` .</span><span class="sxs-lookup"><span data-stu-id="d0858-117">You just need to terminate your submission with a double semicolon (`;;`).</span></span> <span data-ttu-id="d0858-118">F# Etkileşimli tarafından yapıştırılmış ve değerlendirilen aşağıdaki kod parçacığını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d0858-118">Consider the following snippet that has been pasted into and evaluated by F# Interactive:</span></span>

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

<span data-ttu-id="d0858-119">Kodun biçimlendirmesi korunur ve girişi sonlandıran çift noktalı virgül ( `;;` ) vardır.</span><span class="sxs-lookup"><span data-stu-id="d0858-119">The code's formatting is preserved, and there is a double semicolon (`;;`) terminating the input.</span></span> <span data-ttu-id="d0858-120">F# Etkileşimli daha sonra kodu değerlendirdi ve sonuçları yazdırılmıştır!</span><span class="sxs-lookup"><span data-stu-id="d0858-120">F# Interactive then evaluated the code and printed the results!</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="d0858-121">F ile betik oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="d0858-121">Scripting with F\#</span></span>

<span data-ttu-id="d0858-122">F# Etkileşimli, kodu etkileşimli olarak değerlendirmek harika bir öğrenme aracı olabilir, ancak normal bir düzenleyicide kod yazmak kadar üretken olduğunu hızlıca bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-122">Evaluating code interactively in F# Interactive can be a great learning tool, but you'll quickly find that it's not as productive as writing code in a normal editor.</span></span> <span data-ttu-id="d0858-123">Normal kod düzenlemesini desteklemek için F # betikleri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-123">To support normal code editing, you can write F# scripts.</span></span>

<span data-ttu-id="d0858-124">Betikler **. FSX** dosya uzantısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0858-124">Scripts use the file extension **.fsx**.</span></span> <span data-ttu-id="d0858-125">Kaynak kodu derlemek ve daha sonra derlenen derlemeyi çalıştırmak yerine **DotNet fsi** 'yi çalıştırabilir ve f # Kaynak Kodu betiğinin dosya adını belirtebilir ve f # Interactive kodu okur ve gerçek zamanlı olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="d0858-125">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span> <span data-ttu-id="d0858-126">Örneğin, aşağıdaki betiği göz önünde bulundurun `Script.fsx` :</span><span class="sxs-lookup"><span data-stu-id="d0858-126">For example, consider the following script called `Script.fsx`:</span></span>

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

printfn "%A" (getOddSquares [1..10])
```

<span data-ttu-id="d0858-127">Makinenizde bu dosya oluşturulduğunda, ile çalıştırabilir `dotnet fsi` ve doğrudan Terminal pencerenizde çıktıyı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0858-127">When this file is created in your machine, you can run it with `dotnet fsi` and see the output directly in your terminal window:</span></span>

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

<span data-ttu-id="d0858-128">F # Scripting, [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio Code](../../get-started/get-started-vscode.md)ve [Mac için Visual Studio](../../get-started/get-started-with-visual-studio-for-mac.md)yerel olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d0858-128">F# scripting is natively supported in [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio Code](../../get-started/get-started-vscode.md), and [Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md).</span></span>

## <a name="referencing-packages-in-f-interactive"></a><span data-ttu-id="d0858-129">F# Etkileşimli gelen paketlere başvurma</span><span class="sxs-lookup"><span data-stu-id="d0858-129">Referencing packages in F# Interactive</span></span>

<span data-ttu-id="d0858-130">F# Etkileşimli, `#r "nuget:"` söz dizimi ve isteğe bağlı bir sürümle NuGet paketlerine başvurmayı destekler:</span><span class="sxs-lookup"><span data-stu-id="d0858-130">F# Interactive supports referencing NuGet packages with the `#r "nuget:"` syntax and an optional version:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

<span data-ttu-id="d0858-131">Bir sürüm belirtilmemişse, en yüksek önizleme dışı paket alınır.</span><span class="sxs-lookup"><span data-stu-id="d0858-131">If a version is not specified, the highest available non-preview package is taken.</span></span> <span data-ttu-id="d0858-132">Belirli bir sürüme başvurmak için sürümü bir virgül ile tanıtın.</span><span class="sxs-lookup"><span data-stu-id="d0858-132">To reference a specific version, introduce the version via a comma.</span></span> <span data-ttu-id="d0858-133">Bu, bir paketin önizleme sürümüne başvururken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0858-133">This can be handy when referencing a preview version of a package.</span></span> <span data-ttu-id="d0858-134">Örneğin, [Diffsharp](https://diffsharp.github.io/)'un önizleme sürümünü kullanarak bu betiği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d0858-134">For example, consider this script using a preview version of [DiffSharp](https://diffsharp.github.io/):</span></span>

```fsharp
#r "nuget: DiffSharp-lite, 1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn "%A" (f (dsharp.tensor 1.2))
```

### <a name="specifying-a-package-source"></a><span data-ttu-id="d0858-135">Paket kaynağı belirtme</span><span class="sxs-lookup"><span data-stu-id="d0858-135">Specifying a package source</span></span>

<span data-ttu-id="d0858-136">Ayrıca, komutuyla bir paket kaynağı belirtebilirsiniz `#i` .</span><span class="sxs-lookup"><span data-stu-id="d0858-136">You can also specify a package source with the `#i` command.</span></span> <span data-ttu-id="d0858-137">Aşağıdaki örnek, uzak ve yerel bir kaynağı belirtir:</span><span class="sxs-lookup"><span data-stu-id="d0858-137">The following example specifies a remote and a local source:</span></span>

```fsharp
#i "nuget:https://my-remote-package-source/index.json
#i @"path-to-my-local-source"
```

<span data-ttu-id="d0858-138">Bu, Ayrıca, bir betiğe eklenen uzak ve/veya yerel kaynakları hesaba katan, bu çözüm motoruna ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="d0858-138">This will tell the resolution engine under the covers to also take into account the remote and/or local sources added to a script.</span></span>

<span data-ttu-id="d0858-139">Bir komut dosyasında istediğiniz sayıda paket başvurusu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-139">You can specify as many package references as you like in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="d0858-140">Şu anda çerçeve başvuruları kullanan betikler için bir sınırlama vardır (ör. `Microsoft.NET.Sdk.Web` veya  `Microsoft.NET.Sdk.WindowsDesktop` ).</span><span class="sxs-lookup"><span data-stu-id="d0858-140">There's currently a limitation for scripts that use framework references (e.g.`Microsoft.NET.Sdk.Web` or  `Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="d0858-141">Sasırasıyla, Giraffe, WinForms gibi paketler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d0858-141">Packages like Saturn, Giraffe, WinForms are not available.</span></span> <span data-ttu-id="d0858-142">Bu sorun [#9417](https://github.com/dotnet/fsharp/issues/9417)izleniyor.</span><span class="sxs-lookup"><span data-stu-id="d0858-142">This is being tracked in issue [#9417](https://github.com/dotnet/fsharp/issues/9417).</span></span>

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a><span data-ttu-id="d0858-143">F # Interactive ile disk üzerindeki derlemelere başvurma</span><span class="sxs-lookup"><span data-stu-id="d0858-143">Referencing assemblies on disk with F# interactive</span></span>

<span data-ttu-id="d0858-144">Alternatif olarak, disk üzerinde bir derlemeniz varsa ve bir betikte başvurmak istiyorsanız, `#r` bir derleme belirtmek için söz dizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-144">Alternatively, if you have an assembly on disk and wish to reference that in a script, you can use the `#r` syntax to specify an assembly.</span></span> <span data-ttu-id="d0858-145">Aşağıdaki kodu, içinde derlenmiş bir projede göz önünde bulundurun `MyAssembly.dll` :</span><span class="sxs-lookup"><span data-stu-id="d0858-145">Consider the following code in a project compiled into `MyAssembly.dll`:</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

<span data-ttu-id="d0858-146">Derlenmiş bir şekilde, buna benzer şekilde adlandırılan bir dosyada başvurabilirsiniz `Script.fsx` :</span><span class="sxs-lookup"><span data-stu-id="d0858-146">One compiled, you can reference it in a file called `Script.fsx` like so:</span></span>

```fsharp
#r "path/to/MyAssembly.dll"

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="d0858-147">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d0858-147">The output is as follows:</span></span>

```console
dotnet fsi Script.fsx
90
```

<span data-ttu-id="d0858-148">Bir komut dosyasında istediğiniz sayıda derleme başvurusu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-148">You can specify as many assembly references as you like in a script.</span></span>

## <a name="loading-other-scripts"></a><span data-ttu-id="d0858-149">Diğer betikleri yükleme</span><span class="sxs-lookup"><span data-stu-id="d0858-149">Loading other scripts</span></span>

<span data-ttu-id="d0858-150">Komut dosyası oluştururken, farklı görevler için farklı betikler kullanılması genellikle faydalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0858-150">When scripting, it can often be helpful to use different scripts for different tasks.</span></span> <span data-ttu-id="d0858-151">Bazen koddaki kodu başka bir kodla yeniden kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-151">Sometimes you may want to reuse code from on script in another.</span></span> <span data-ttu-id="d0858-152">İçeriğini dosyanıza kopyalamak-yapıştırmak yerine, ile basit yükleme ve değerlendirme yapabilirsiniz `#load` .</span><span class="sxs-lookup"><span data-stu-id="d0858-152">Rather than copy-pasting its contents into your file, you can simple load and evaluate it with `#load`.</span></span>

<span data-ttu-id="d0858-153">Aşağıdakileri göz önünde bulundurun `Script1.fsx` :</span><span class="sxs-lookup"><span data-stu-id="d0858-153">Consider the following `Script1.fsx`:</span></span>

```fsharp
let square x = x * x
```

<span data-ttu-id="d0858-154">Ve kullanan dosya `Script2.fsx` :</span><span class="sxs-lookup"><span data-stu-id="d0858-154">And the consuming file, `Script2.fsx`:</span></span>

```fsharp
#load "Script1.fsx"
open Script1

printfn "%d" (square 12)
```

<span data-ttu-id="d0858-155">`open Script1`Bildirimin gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d0858-155">Note that the `open Script1` declaration is required.</span></span> <span data-ttu-id="d0858-156">Bunun nedeni, bir F # betiğindeki yapıların içinde bulunduğu komut dosyasının adı olan en üst düzey bir modüle derlenmesinden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="d0858-156">This is because constructs in an F# script are compiled into a top-level module that is the name of the script file it is in.</span></span>

<span data-ttu-id="d0858-157">`Script2.fsx`Şöyle değerlendirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0858-157">You can evaluate `Script2.fsx` like so:</span></span>

```console
dotnet fsi Script2.fsx
144
```

<span data-ttu-id="d0858-158">`#load`Bir komut dosyasında istediğiniz kadar çok yönergesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-158">You can specify as many `#load` directives as you like in a script.</span></span>

## <a name="using-the-fsi-object-in-f-code"></a><span data-ttu-id="d0858-159">`fsi`F # kodundaki nesneyi kullanma</span><span class="sxs-lookup"><span data-stu-id="d0858-159">Using the `fsi` object in F# code</span></span>

<span data-ttu-id="d0858-160">F # betikleri `fsi` , F# Etkileşimli oturumunu temsil eden özel bir nesneye erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d0858-160">F# scripts have access to a custom `fsi` object that represents the F# Interactive session.</span></span> <span data-ttu-id="d0858-161">Çıktı biçimlendirme gibi şeyleri özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0858-161">It allows you to customize things like output formatting.</span></span> <span data-ttu-id="d0858-162">Komut satırı bağımsız değişkenlerine de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-162">It is also how you can access command-line arguments.</span></span>

<span data-ttu-id="d0858-163">Aşağıdaki örnek, komut satırı bağımsız değişkenlerinin nasıl alınacağını ve kullanılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="d0858-163">The following example shows how to get and use command-line arguments:</span></span>

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn "%s" arg
```

<span data-ttu-id="d0858-164">Değerlendirildiğinde, tüm bağımsız değişkenleri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0858-164">When evaluated, it prints all arguments.</span></span> <span data-ttu-id="d0858-165">İlk bağımsız değişken her zaman değerlendirilen betiğin adıdır:</span><span class="sxs-lookup"><span data-stu-id="d0858-165">The first argument is always the name of the script that is evaluated:</span></span>

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

<span data-ttu-id="d0858-166">`System.Environment.GetCommandLineArgs()`Aynı bağımsız değişkenlere erişmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-166">You can also use `System.Environment.GetCommandLineArgs()` to access the same arguments.</span></span>

## <a name="f-interactive-directive-reference"></a><span data-ttu-id="d0858-167">F# Etkileşimli yönerge başvurusu</span><span class="sxs-lookup"><span data-stu-id="d0858-167">F# Interactive directive reference</span></span>

<span data-ttu-id="d0858-168">`#r` `#load` Daha önce görülen ve yönergeleri yalnızca F# etkileşimli kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0858-168">The `#r` and `#load` directives seen previously are only available in F# Interactive.</span></span> <span data-ttu-id="d0858-169">Yalnızca F# Etkileşimli kullanılabilen çeşitli yönergeler vardır:</span><span class="sxs-lookup"><span data-stu-id="d0858-169">There are several directives only available in F# Interactive:</span></span>

|<span data-ttu-id="d0858-170">Deki</span><span class="sxs-lookup"><span data-stu-id="d0858-170">Directive</span></span>|<span data-ttu-id="d0858-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0858-171">Description</span></span>|
|---------|-----------|
|`#r "nuget:..."`|<span data-ttu-id="d0858-172">NuGet 'ten bir pakete başvurur</span><span class="sxs-lookup"><span data-stu-id="d0858-172">References a package from NuGet</span></span>|
|`#r "assembly-name.dll"`|<span data-ttu-id="d0858-173">Diskteki bir derlemeye başvurur</span><span class="sxs-lookup"><span data-stu-id="d0858-173">References an assembly on disk</span></span>|
|`#load "file-name.fsx"`|<span data-ttu-id="d0858-174">Bir kaynak dosyayı okur, derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d0858-174">Reads a source file, compiles it, and runs it.</span></span>|
|`#help`|<span data-ttu-id="d0858-175">Kullanılabilir yönergeler hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0858-175">Displays information about available directives.</span></span>|
|`#I`|<span data-ttu-id="d0858-176">Bir derleme arama yolunu tırnak işaretleri halinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0858-176">Specifies an assembly search path in quotation marks.</span></span>|
|`#quit`|<span data-ttu-id="d0858-177">F# Etkileşimli oturumunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d0858-177">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="d0858-178">`#time "on"` veya `#time "off"`</span><span class="sxs-lookup"><span data-stu-id="d0858-178">`#time "on"` or `#time "off"`</span></span>|<span data-ttu-id="d0858-179">, `#time` Performans bilgilerinin görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0858-179">By itself, `#time` toggles whether to display performance information.</span></span> <span data-ttu-id="d0858-180">`"on"`F# Etkileşimli, yorumlanan ve yürütülen kodun her bölümü için gerçek zamanlı, CPU süresini ve çöp toplama bilgilerini ölçer.</span><span class="sxs-lookup"><span data-stu-id="d0858-180">When it is `"on"`, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="d0858-181">F# Etkileşimli dosya veya yolları belirttiğinizde, bir dize sabit değeri beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d0858-181">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="d0858-182">Bu nedenle, dosyalar ve yollar tırnak işaretleri içinde olmalı ve normal kaçış karakterleri de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d0858-182">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="d0858-183">`@`Karakteri, bir yolu içeren dizeyi tam bir dize olarak yorumlamasını F# Etkileşimli neden olması için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-183">You can use the `@` character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="d0858-184">Bu, F# Etkileşimli kaçış karakterlerini yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="d0858-184">This causes F# Interactive to ignore any escape characters.</span></span>

## <a name="interactive-and-compiled-preprocessor-directives"></a><span data-ttu-id="d0858-185">Etkileşimli ve derlenmiş Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d0858-185">Interactive and compiled preprocessor directives</span></span>

<span data-ttu-id="d0858-186">Etkileşimli olarak çalıştırdığınız veya bir betiği çalıştırdığınıza bakılmaksızın F# Etkileşimli kod derlerken **etkileşimli** sembol tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0858-186">When you compile code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="d0858-187">Derleyicide kod derlerken, **derlenen** sembol tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0858-187">When you compile code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="d0858-188">Bu nedenle, kodun derlenmiş ve etkileşimli modlarda farklı olması gerekiyorsa, bu ön işlemci yönergelerini koşullu derleme için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-188">Thus, if code needs to be different in compiled and interactive modes, you can use these preprocessor directives for conditional compilation to determine which to use.</span></span> <span data-ttu-id="d0858-189">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d0858-189">For example:</span></span>

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a><span data-ttu-id="d0858-190">Visual Studio 'da F# Etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="d0858-190">Using F# Interactive in Visual Studio</span></span>

<span data-ttu-id="d0858-191">Visual Studio aracılığıyla F# Etkileşimli çalıştırmak için **F# Etkileşimli** etiketli uygun araç çubuğu düğmesine tıklayabilir veya **Ctrl + Alt + F** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d0858-191">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="d0858-192">Bunu yapmak, F# Etkileşimli oturum çalıştıran bir araç penceresi olan etkileşimli pencereyi açar.</span><span class="sxs-lookup"><span data-stu-id="d0858-192">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="d0858-193">Ayrıca etkileşimli pencerede çalıştırmak istediğiniz kod ve **Alt + Enter** tuş birleşimine basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-193">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="d0858-194">F# Etkileşimli, **F# Etkileşimli** etiketli bir araç penceresinde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d0858-194">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="d0858-195">Bu tuş birleşimini kullandığınızda, düzenleyici penceresinin odağa sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d0858-195">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="d0858-196">Konsolunu veya Visual Studio 'Yu kullanıp kullanmayacağınızı bir komut istemi belirir ve yorumlayıcı, girişinizi bekler.</span><span class="sxs-lookup"><span data-stu-id="d0858-196">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="d0858-197">Kodu, kod dosyasında olduğu gibi girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-197">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="d0858-198">Kodu derlemek ve yürütmek için, bir satırı veya birkaç giriş satırını sonlandırmak üzere iki noktalı virgül (**;;**) girin.</span><span class="sxs-lookup"><span data-stu-id="d0858-198">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="d0858-199">F# Etkileşimli kodu derlemeye çalışır ve başarılı olursa, kodu yürütür ve derlenen türlerin ve değerlerin imzasını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0858-199">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="d0858-200">Hata oluşursa yorumlayıcı hata iletilerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0858-200">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="d0858-201">Aynı oturumda girilen kod, daha önce girilmiş olan her türlü yapıya erişebilir, böylece programları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-201">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="d0858-202">Araç penceresindeki kapsamlı bir arabellek, gerekirse kodu bir dosyaya kopyalamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0858-202">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="d0858-203">Visual Studio 'da çalıştırıldığında F# Etkileşimli projenizden bağımsız olarak çalışır. bu nedenle, örneğin, işlev için kodu etkileşimli pencereye kopyalamadıkça, projenizde tanımlanan yapıları F# Etkileşimli kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d0858-203">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="d0858-204">Ayarları ayarlayarak F# Etkileşimli komut satırı bağımsız değişkenlerini (Seçenekler) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0858-204">You can control the F# Interactive command-line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="d0858-205">**Araçlar** menüsünde **Seçenekler...**' i seçin ve ardından **F # araçları**' nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="d0858-205">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="d0858-206">Değiştirebileceğiniz iki ayar F# Etkileşimli seçenekleridir ve **64 bit F# Etkileşimli** ayarıdır ve bu, yalnızca 64 bit makinede F# Etkileşimli çalıştırıyorsanız geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d0858-206">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="d0858-207">Bu ayar, 32 bit veya 64 bit işlem olarak çalıştırılıp çalıştırılmadığını belirleyen **fsi.exe** veya **fsianycpu.exe** adanmış 64 bitlik sürümünü çalıştırmak isteyip istemediğinizi belirler.</span><span class="sxs-lookup"><span data-stu-id="d0858-207">This setting determines whether you want to run the dedicated 64-bit version of **fsi.exe** or **fsianycpu.exe**, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="related-articles"></a><span data-ttu-id="d0858-208">İlgili makaleler:</span><span class="sxs-lookup"><span data-stu-id="d0858-208">Related articles</span></span>

|<span data-ttu-id="d0858-209">Başlık</span><span class="sxs-lookup"><span data-stu-id="d0858-209">Title</span></span>|<span data-ttu-id="d0858-210">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0858-210">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="d0858-211">F# Etkileşimli Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d0858-211">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="d0858-212">F# Etkileşimli fsi.exe için komut satırı sözdizimini ve seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0858-212">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
