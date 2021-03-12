---
title: Main () dönüş değerleri-C# Programlama Kılavuzu
description: Main () dönüş değerleri hakkında bilgi edinin. Bkz. kod örnekleri, derleyici tarafından oluşturulan kod ve kullanılabilir ek kaynakları görüntüleme.
ms.date: 03/11/2021
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 6f4001ecd490d5627d3a1ec74ecf7d593451e104
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190365"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="9d8ee-104">Main () dönüş değerleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9d8ee-104">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="9d8ee-105">Yöntemini `int` `Main` aşağıdaki yöntemlerden biriyle tanımlayarak yönteminden dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d8ee-105">You can return an `int` from the `Main` method by defining the method in one of the following ways:</span></span>

| <span data-ttu-id="9d8ee-106">`Main` Yöntem kodu</span><span class="sxs-lookup"><span data-stu-id="9d8ee-106">`Main` method code</span></span>             | <span data-ttu-id="9d8ee-107">`Main` imza</span><span class="sxs-lookup"><span data-stu-id="9d8ee-107">`Main` signature</span></span>                             |
|--------------------------------|----------------------------------------------|
| <span data-ttu-id="9d8ee-108">`args`Veya kullanımı`await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-108">No use of `args` or `await`</span></span>    | `static int Main()`                          |
| <span data-ttu-id="9d8ee-109">`args`, Kullanımları`await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-109">Uses `args`, no use of `await`</span></span> | `static int Main(string[] args)`             |
| <span data-ttu-id="9d8ee-110">Kullanım yok `args` , kullanımları `await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-110">No use of `args`, uses `await`</span></span> | `static async Task<int> Main()`              |
| <span data-ttu-id="9d8ee-111">`args`Ve kullanır`await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-111">Uses `args` and `await`</span></span>        | `static async Task<int> Main(string[] args)` |

<span data-ttu-id="9d8ee-112">Dönüş değeri `Main` kullanılmazsa, `void` `Task` biraz daha basit bir kod döndürülmesi veya bu kodun kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-112">If the return value from `Main` is not used, returning `void` or `Task` allows for slightly simpler code.</span></span>

| <span data-ttu-id="9d8ee-113">`Main` Yöntem kodu</span><span class="sxs-lookup"><span data-stu-id="9d8ee-113">`Main` method code</span></span>             | <span data-ttu-id="9d8ee-114">`Main` imza</span><span class="sxs-lookup"><span data-stu-id="9d8ee-114">`Main` signature</span></span>                        |
|--------------------------------|-----------------------------------------|
| <span data-ttu-id="9d8ee-115">`args`Veya kullanımı`await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-115">No use of `args` or `await`</span></span>    | `static void Main()`                    |
| <span data-ttu-id="9d8ee-116">`args`, Kullanımları`await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-116">Uses `args`, no use of `await`</span></span> | `static void Main(string[] args)`       |
| <span data-ttu-id="9d8ee-117">Kullanım yok `args` , kullanımları `await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-117">No use of `args`, uses `await`</span></span> | `static async Task Main()`              |
| <span data-ttu-id="9d8ee-118">`args`Ve kullanır`await`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-118">Uses `args` and `await`</span></span>        | `static async Task Main(string[] args)` |

<span data-ttu-id="9d8ee-119">Ancak, `int` `Task<int>` programın durum bilgilerini yürütülebilir dosyayı çağıran diğer programlarla veya betiklerine iletmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-119">However, returning `int` or `Task<int>` enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span>

<span data-ttu-id="9d8ee-120">Aşağıdaki örnek, işlem için çıkış kodunun nasıl erişilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-120">The following example shows how the exit code for the process can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="9d8ee-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d8ee-121">Example</span></span>

<span data-ttu-id="9d8ee-122">Bu örnek [.NET Core](../../../core/introduction.md) komut satırı araçlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-122">This example uses [.NET Core](../../../core/introduction.md) command-line tools.</span></span> <span data-ttu-id="9d8ee-123">.NET Core komut satırı araçları hakkında bilginiz yoksa, bu [Get-Started makalesinde](../../../core/tutorials/with-visual-studio-code.md)hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-123">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="9d8ee-124">`Main` *Program.cs* içindeki yöntemi aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9d8ee-124">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="9d8ee-125">Bir program Windows 'da yürütüldüğünde, işlevden döndürülen herhangi bir değer `Main` bir ortam değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-125">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="9d8ee-126">Bu ortam değişkeni `ERRORLEVEL` , bir toplu iş dosyasından veya PowerShell 'den kullanılarak alınabilir `$LastExitCode` .</span><span class="sxs-lookup"><span data-stu-id="9d8ee-126">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from PowerShell.</span></span>

<span data-ttu-id="9d8ee-127">[DotNet CLI](../../../core/tools/dotnet.md) komutunu kullanarak uygulamayı oluşturabilirsiniz `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="9d8ee-127">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="9d8ee-128">Sonra, uygulamayı çalıştırmak için bir PowerShell betiği oluşturun ve sonucu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-128">Next, create a PowerShell script to run the application and display the result.</span></span> <span data-ttu-id="9d8ee-129">Aşağıdaki kodu bir metin dosyasına yapıştırın ve `test.ps1` projeyi içeren klasöre kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-129">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="9d8ee-130">PowerShell komut istemine yazarak PowerShell betiğini çalıştırın `test.ps1` .</span><span class="sxs-lookup"><span data-stu-id="9d8ee-130">Run the PowerShell script by typing `test.ps1` at the PowerShell prompt.</span></span>

<span data-ttu-id="9d8ee-131">Kod sıfır döndürdüğünden, toplu iş dosyası başarıyı bildirir.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-131">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="9d8ee-132">Ancak, MainReturnValTest.cs değerini sıfır olmayan bir değer döndürecek şekilde değiştirirseniz ve sonra programı yeniden derleytiğinizde, PowerShell betiğinin sonraki yürütülmesi hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-132">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the PowerShell script will report failure.</span></span>

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="9d8ee-133">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="9d8ee-133">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="9d8ee-134">Zaman uyumsuz ana dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="9d8ee-134">Async Main return values</span></span>

<span data-ttu-id="9d8ee-135">Zaman uyumsuz ana dönüş değerleri, içinde zaman uyumsuz yöntemleri çağırmak için gereken ortak kodu `Main` derleyici tarafından oluşturulan koda taşır.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-135">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="9d8ee-136">Daha önce, zaman uyumsuz kodu çağırmak ve programınızın zaman uyumsuz işlem tamamlanana kadar çalıştığından emin olmak için bu yapıyı yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="9d8ee-136">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="9d8ee-137">Şimdi bu, şu şekilde değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="9d8ee-137">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="9d8ee-138">Yeni sözdiziminin avantajı, derleyicinin her zaman doğru kodu üretmesinin avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-138">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="9d8ee-139">Derleyici tarafından üretilen kod</span><span class="sxs-lookup"><span data-stu-id="9d8ee-139">Compiler-generated code</span></span>

<span data-ttu-id="9d8ee-140">Uygulama giriş noktası bir `Task` veya döndürdüğünde `Task<int>` , derleyici uygulama kodunda belirtilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-140">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="9d8ee-141">Bu giriş noktasının çağrıldığı kabul edildiğinde `$GeneratedMain` , derleyici bu giriş noktaları için aşağıdaki kodu üretir:</span><span class="sxs-lookup"><span data-stu-id="9d8ee-141">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="9d8ee-142">`static Task Main()` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-142">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="9d8ee-143">`static Task Main(string[])` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-143">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="9d8ee-144">`static Task<int> Main()` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-144">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="9d8ee-145">`static Task<int> Main(string[])` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="9d8ee-145">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="9d8ee-146">Örnekler `async` yöntemde değiştirici kullandıysanız `Main` , derleyici aynı kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-146">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d8ee-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d8ee-147">See also</span></span>

- [<span data-ttu-id="9d8ee-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9d8ee-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9d8ee-149">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9d8ee-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9d8ee-150">Main () ve Command-Line bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9d8ee-150">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="9d8ee-151">Komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="9d8ee-151">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
