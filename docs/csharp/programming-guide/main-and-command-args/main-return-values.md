---
title: Main () dönüş değerleri-C# Programlama Kılavuzu
description: Main () dönüş değerleri hakkında bilgi edinin. Bkz. kod örnekleri, derleyici tarafından oluşturulan kod ve kullanılabilir ek kaynakları görüntüleme.
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 4458f3cd7c8259c5725cfe5e853f826fe2ef61cc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382067"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="89c8a-104">Main () dönüş değerleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="89c8a-104">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="89c8a-105">`Main`Yöntemi şu şekilde dönebilir `void` :</span><span class="sxs-lookup"><span data-stu-id="89c8a-105">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="89c8a-106">Ayrıca, şunu döndürebilir `int` :</span><span class="sxs-lookup"><span data-stu-id="89c8a-106">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="89c8a-107">Dönüş değeri `Main` kullanılmazsa, döndürme `void` biraz daha basit bir koda izin verir.</span><span class="sxs-lookup"><span data-stu-id="89c8a-107">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="89c8a-108">Ancak, bir tamsayı döndürmek programın durum bilgilerini yürütülebilir dosyayı çağıran diğer programlarla veya betiklerine iletmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="89c8a-108">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="89c8a-109">Dönüş değeri, `Main` işlem için çıkış kodu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="89c8a-109">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="89c8a-110">`void`Öğesinden döndürülürse `Main` , çıkış kodu örtük olarak açılır `0` .</span><span class="sxs-lookup"><span data-stu-id="89c8a-110">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="89c8a-111">Aşağıdaki örnekte, ' den dönüş değerine nasıl `Main` erişilebileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89c8a-111">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="89c8a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="89c8a-112">Example</span></span>

<span data-ttu-id="89c8a-113">Bu örnek [.NET Core](../../../core/index.yml) komut satırı araçlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="89c8a-113">This example uses [.NET Core](../../../core/index.yml) command-line tools.</span></span> <span data-ttu-id="89c8a-114">.NET Core komut satırı araçları hakkında bilginiz yoksa, bu [Get-Started makalesinde](../../../core/tutorials/with-visual-studio-code.md)hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89c8a-114">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="89c8a-115">`Main` *Program.cs* içindeki yöntemi aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89c8a-115">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="89c8a-116">Bir program Windows 'da yürütüldüğünde, işlevden döndürülen herhangi bir değer `Main` bir ortam değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="89c8a-116">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="89c8a-117">Bu ortam değişkeni `ERRORLEVEL` , bir toplu iş dosyasından veya PowerShell 'den kullanılarak alınabilir `$LastExitCode` .</span><span class="sxs-lookup"><span data-stu-id="89c8a-117">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="89c8a-118">[DotNet CLI](../../../core/tools/dotnet.md) komutunu kullanarak uygulamayı oluşturabilirsiniz `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="89c8a-118">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="89c8a-119">Sonra, uygulamayı çalıştırmak için bir PowerShell betiği oluşturun ve sonucu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="89c8a-119">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="89c8a-120">Aşağıdaki kodu bir metin dosyasına yapıştırın ve `test.ps1` projeyi içeren klasöre kaydedin.</span><span class="sxs-lookup"><span data-stu-id="89c8a-120">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="89c8a-121">PowerShell komut istemine yazarak PowerShell betiğini çalıştırın `test.ps1` .</span><span class="sxs-lookup"><span data-stu-id="89c8a-121">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="89c8a-122">Kod sıfır döndürdüğünden, toplu iş dosyası başarıyı bildirir.</span><span class="sxs-lookup"><span data-stu-id="89c8a-122">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="89c8a-123">Ancak, MainReturnValTest.cs değerini sıfır olmayan bir değer döndürecek şekilde değiştirirseniz ve sonra programı yeniden derleytiğinizde, PowerShell betiğinin sonraki yürütülmesi hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="89c8a-123">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="89c8a-124">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="89c8a-124">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="89c8a-125">Zaman uyumsuz ana dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="89c8a-125">Async Main return values</span></span>

<span data-ttu-id="89c8a-126">Zaman uyumsuz ana dönüş değerleri, içinde zaman uyumsuz yöntemleri çağırmak için gereken ortak kodu `Main` derleyici tarafından oluşturulan koda taşır.</span><span class="sxs-lookup"><span data-stu-id="89c8a-126">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="89c8a-127">Daha önce, zaman uyumsuz kodu çağırmak ve programınızın zaman uyumsuz işlem tamamlanana kadar çalıştığından emin olmak için bu yapıyı yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="89c8a-127">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="89c8a-128">Şimdi bu, şu şekilde değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="89c8a-128">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="89c8a-129">Yeni sözdiziminin avantajı, derleyicinin her zaman doğru kodu üretmesinin avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="89c8a-129">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="89c8a-130">Derleyici tarafından üretilen kod</span><span class="sxs-lookup"><span data-stu-id="89c8a-130">Compiler-generated code</span></span>

<span data-ttu-id="89c8a-131">Uygulama giriş noktası bir `Task` veya döndürdüğünde `Task<int>` , derleyici uygulama kodunda belirtilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89c8a-131">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="89c8a-132">Bu giriş noktasının çağrıldığı kabul edildiğinde `$GeneratedMain` , derleyici bu giriş noktaları için aşağıdaki kodu üretir:</span><span class="sxs-lookup"><span data-stu-id="89c8a-132">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="89c8a-133">`static Task Main()`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="89c8a-133">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="89c8a-134">`static Task Main(string[])`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="89c8a-134">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="89c8a-135">`static Task<int> Main()`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="89c8a-135">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="89c8a-136">`static Task<int> Main(string[])`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="89c8a-136">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="89c8a-137">Örnekler `async` yöntemde değiştirici kullandıysanız `Main` , derleyici aynı kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89c8a-137">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="89c8a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89c8a-138">See also</span></span>

- [<span data-ttu-id="89c8a-139">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="89c8a-139">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="89c8a-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="89c8a-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="89c8a-141">Main () ve komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="89c8a-141">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="89c8a-142">Komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="89c8a-142">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
