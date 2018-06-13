---
title: Ana() Dönüş Değerleri (C# Programlama Kılavuzu)
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 51a7d821b5705c0ddda96a34663ba0288e0f1da9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339962"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="3e182-102">Ana() dönüş değerleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3e182-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="3e182-103">`Main` Yöntemi dönebilirsiniz `void`:</span><span class="sxs-lookup"><span data-stu-id="3e182-103">The `Main` method can return `void`:</span></span>

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

<span data-ttu-id="3e182-104">Ayrıca dönebilirsiniz bir `int`:</span><span class="sxs-lookup"><span data-stu-id="3e182-104">It can also return an `int`:</span></span>

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

<span data-ttu-id="3e182-105">Dönüş değeri, `Main` , döndürme kullanılmaz `void` için biraz daha basit kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e182-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="3e182-106">Ancak, bir tamsayı döndürme diğer programları veya yürütülebilir dosyanın çağırma betikleri durum bilgilerini iletmek program sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e182-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="3e182-107">Dönüş değerini `Main` işlem çıkış kodu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3e182-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="3e182-108">Aşağıdaki örnek, dönüş nasıl değeri gösterir `Main` erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e182-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="3e182-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e182-109">Example</span></span>

<span data-ttu-id="3e182-110">Bu örnekte [.NET Core](../../../core/index.md) komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="3e182-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="3e182-111">.NET Core komut satırı araçları ile unfamilar varsa, bunları bu öğrenebilir [Get başlatılan konu](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="3e182-111">If you are unfamilar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="3e182-112">Değiştirme `Main` yönteminde *program.cs* gibi:</span><span class="sxs-lookup"><span data-stu-id="3e182-112">Modify the `Main` method in *program.cs* as follows:</span></span>

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

<span data-ttu-id="3e182-113">Windows'da bir program çalıştırıldığında, herhangi bir değer döndürülen `Main` işlevi bir ortam değişkeni depolanır.</span><span class="sxs-lookup"><span data-stu-id="3e182-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="3e182-114">Bu ortam değişkenini kullanarak alınabilir `ERRORLEVEL` bir toplu iş dosyasından veya `$LastExitCode` powershell'den.</span><span class="sxs-lookup"><span data-stu-id="3e182-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="3e182-115">Kullanarak uygulama oluşturabilir [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` komutu.</span><span class="sxs-lookup"><span data-stu-id="3e182-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="3e182-116">Ardından, uygulamayı çalıştırın ve sonucu görüntülemek için bir Powershell betiği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e182-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="3e182-117">Bir metin dosyasına aşağıdaki kodu yapıştırın ve kaydedileceği `test.ps1` projeyi içeren klasörün içinde.</span><span class="sxs-lookup"><span data-stu-id="3e182-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="3e182-118">Powershell betiği yazarak çalıştırırsınız `test.ps1` powershell komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="3e182-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="3e182-119">Kodu sıfır döndürdüğünden, toplu iş dosyasını başarı rapor eder.</span><span class="sxs-lookup"><span data-stu-id="3e182-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="3e182-120">Ancak, sıfır olmayan bir değer dönün ve ardından programı yeniden derleyin MainReturnValTest.cs değiştirirseniz, powershell betiği sonraki yürütülmesi hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e182-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="3e182-121">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="3e182-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="3e182-122">Zaman uyumsuz ana dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="3e182-122">Async Main return values</span></span>

<span data-ttu-id="3e182-123">Zaman uyumsuz ana dönüş değerleri taşımak için zaman uyumsuz yöntemleri çağırma gerekli Demirbaş kod `Main` derleyici tarafından üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="3e182-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="3e182-124">Daha önce zaman uyumsuz kod çağırmak ve zaman uyumsuz işlemi tamamlanana kadar programı çalıştıran sağlamak için bu yapıyı yazma gerekir:</span><span class="sxs-lookup"><span data-stu-id="3e182-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="3e182-125">Şimdi, bu tarafından değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="3e182-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="3e182-126">Yeni sözdizimini avantajlarından derleyici her zaman doğru kod oluşturur birisidir.</span><span class="sxs-lookup"><span data-stu-id="3e182-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="3e182-127">Oluşturulan derleyici kodu</span><span class="sxs-lookup"><span data-stu-id="3e182-127">Compiler generated code</span></span>

<span data-ttu-id="3e182-128">Uygulama giriş noktası döndüğünde bir `Task` veya `Task<int>`, derleyici uygulama kodunda bildirilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e182-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="3e182-129">Bu giriş noktası çağrıldı varsayılarak `$GeneratedMain`, bu giriş noktaları için aşağıdaki kod derleyici oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3e182-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="3e182-130">`static Task Main()` denk yayma derleyici sonuçları `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="3e182-130">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="3e182-131">`static Task Main(string[])` denk yayma derleyici sonuçları `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="3e182-131">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="3e182-132">`static Task<int> Main()` denk yayma derleyici sonuçları `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="3e182-132">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="3e182-133">`static Task<int> Main(string[])` denk yayma derleyici sonuçları `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="3e182-133">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="3e182-134">Örnekler kullandıysanız `async` değiştirici `Main` yöntemi derleyici aynı kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e182-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e182-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e182-135">See also</span></span>
<span data-ttu-id="3e182-136">[C# programlama kılavuzu](../../programming-guide/index.md)
[C# başvurusu](../index.md)
[ana() ve komut satırı bağımsız değişkenleri](index.md)
[nasıl yapılır: komut satırı görüntüleme Bağımsız değişkenler](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[nasıl yapılır: foreach kullanarak komut satırı bağımsız değişkenlerine erişme](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span><span class="sxs-lookup"><span data-stu-id="3e182-136">[C# Programming Guide](../../programming-guide/index.md)
[C# Reference](../index.md)
[Main() and Command-Line Arguments](index.md)
[How to: Display Command Line Arguments](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[How to: Access Command-Line Arguments Using foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span></span>
