---
title: Ana() Dönüş Değerleri (C# Programlama Kılavuzu)
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 8ac0d70458d7c3762ae9dc5fc90058f0caafc4ab
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071368"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="e8dc5-102">Ana() dönüş değerleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e8dc5-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="e8dc5-103">`Main` Yöntemi döndürebilir `void`:</span><span class="sxs-lookup"><span data-stu-id="e8dc5-103">The `Main` method can return `void`:</span></span>

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

<span data-ttu-id="e8dc5-104">Ayrıca döndürebilir bir `int`:</span><span class="sxs-lookup"><span data-stu-id="e8dc5-104">It can also return an `int`:</span></span>

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

<span data-ttu-id="e8dc5-105">Döndürülen değeri `Main` döndüren kullanılmıyor `void` için biraz daha basit kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="e8dc5-106">Ancak, bir tamsayı döndüren diğer programları veya yürütülebilir dosya çağırma betikleri için durum bilgisi iletişim kurmak programın sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="e8dc5-107">Dönüş değeri `Main` işlemi için çıkış kodu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="e8dc5-108">Aşağıdaki örnek, dönüş değeri nasıl gösterir `Main` erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="e8dc5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8dc5-109">Example</span></span>

<span data-ttu-id="e8dc5-110">Bu örnekte [.NET Core](../../../core/index.md) komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="e8dc5-111">.NET Core komut satırı araçlarıyla unfamilar varsa, bunlarla ilgili bu öğrenebilirsiniz [Get başlatılan konu](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="e8dc5-111">If you are unfamilar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="e8dc5-112">Değiştirme `Main` yönteminde *program.cs* gibi:</span><span class="sxs-lookup"><span data-stu-id="e8dc5-112">Modify the `Main` method in *program.cs* as follows:</span></span>

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

<span data-ttu-id="e8dc5-113">Herhangi bir değer Windows programı yürütüldüğünde, döndürülen `Main` işlevi, bir ortam değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="e8dc5-114">Bu ortam değişkeni kullanılarak alınabilir `ERRORLEVEL` bir toplu iş dosyasından veya `$LastExitCode` powershell'den.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="e8dc5-115">Kullanarak uygulama derleme [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` komutu.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="e8dc5-116">Ardından, uygulamayı çalıştırmak ve sonucu görüntülemek için bir Powershell betiği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="e8dc5-117">Aşağıdaki kodu bir metin dosyasına yapıştırın ve kaydedileceği `test.ps1` projeyi içeren klasörü içinde.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="e8dc5-118">Yazarak powershell betiğini çalıştırma `test.ps1` powershell komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="e8dc5-119">Toplu iş dosyası, kod sıfır döndürdüğünden, başarı rapor eder.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="e8dc5-120">Ancak, sıfır olmayan bir değer döndürmez ve ardından programı yeniden derlemek için MainReturnValTest.cs değiştirirseniz, powershell betiğinin sonraki yürütme hata rapor eder.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="e8dc5-121">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="e8dc5-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="e8dc5-122">Async Main dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="e8dc5-122">Async Main return values</span></span>

<span data-ttu-id="e8dc5-123">Async Main dönüş değerleri taşımak için zaman uyumsuz yöntemleri çağırma gerekli ortak kod `Main` derleyici tarafından üretilen kod.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="e8dc5-124">Daha önce zaman uyumsuz kod arama ve zaman uyumsuz işlem tamamlanana kadar programınızı çalıştırdınız emin olmak için bu yapıyı yazma gerekir:</span><span class="sxs-lookup"><span data-stu-id="e8dc5-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="e8dc5-125">Şimdi bu tarafından değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="e8dc5-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="e8dc5-126">Yeni sözdizimi avantajı, derleyici her zaman doğru kodu oluşturur ' dir.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="e8dc5-127">Derleyicinin ürettiği kodu</span><span class="sxs-lookup"><span data-stu-id="e8dc5-127">Compiler generated code</span></span>

<span data-ttu-id="e8dc5-128">Uygulama giriş noktası döndürdüğünde bir `Task` veya `Task<int>`, derleyici uygulama kodunda bildirilen girdi noktası yöntemini çağıran yeni bir giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="e8dc5-129">Bu giriş noktası çağrıldı varsayarak `$GeneratedMain`, derleyici bu giriş noktaları için şu kodu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e8dc5-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="e8dc5-130">`static Task Main()` denk yayan derleme sonuçları `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="e8dc5-130">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="e8dc5-131">`static Task Main(string[])` denk yayan derleme sonuçları `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="e8dc5-131">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="e8dc5-132">`static Task<int> Main()` denk yayan derleme sonuçları `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="e8dc5-132">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="e8dc5-133">`static Task<int> Main(string[])` denk yayan derleme sonuçları `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="e8dc5-133">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="e8dc5-134">Örnekleri kullandıysanız `async` değiştiricisi `Main` yöntemi, derleyici aynı kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8dc5-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-135">See Also</span></span>
- [<span data-ttu-id="e8dc5-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e8dc5-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e8dc5-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e8dc5-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e8dc5-138">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e8dc5-138">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="e8dc5-139">Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e8dc5-139">How to: Display Command Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="e8dc5-140">Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="e8dc5-140">How to: Access Command-Line Arguments Using foreach</span></span>](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
