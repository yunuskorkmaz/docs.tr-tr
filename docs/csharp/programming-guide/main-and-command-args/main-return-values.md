---
title: Ana() dönüş değerleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: ea6f93e52ade91e61bdfcbc35aeb56de9101e80f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878925"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="c0d23-102">Ana() dönüş değerleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c0d23-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="c0d23-103">`Main` Yöntemi döndürebilir `void`:</span><span class="sxs-lookup"><span data-stu-id="c0d23-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="c0d23-104">Ayrıca döndürebilir bir `int`:</span><span class="sxs-lookup"><span data-stu-id="c0d23-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="c0d23-105">Döndürülen değeri `Main` döndüren kullanılmıyor `void` için biraz daha basit kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0d23-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="c0d23-106">Ancak, bir tamsayı döndüren diğer programları veya yürütülebilir dosya çağırma betikleri için durum bilgisi iletişim kurmak programın sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0d23-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="c0d23-107">Dönüş değeri `Main` işlemi için çıkış kodu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c0d23-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="c0d23-108">Varsa `void` öğesinden döndürülen `Main` çıkış kodu örtük olarak olacaktır `0`.</span><span class="sxs-lookup"><span data-stu-id="c0d23-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="c0d23-109">Aşağıdaki örnek, dönüş değeri nasıl gösterir `Main` erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c0d23-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="c0d23-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0d23-110">Example</span></span>

<span data-ttu-id="c0d23-111">Bu örnekte [.NET Core](../../../core/index.md) komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="c0d23-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="c0d23-112">.NET Core komut satırı araçlarıyla alışkın değilseniz, bunlarla ilgili bu öğrenebilirsiniz [Get başlatılan konu](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="c0d23-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="c0d23-113">Değiştirme `Main` yönteminde *program.cs* gibi:</span><span class="sxs-lookup"><span data-stu-id="c0d23-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="c0d23-114">Herhangi bir değer Windows programı yürütüldüğünde, döndürülen `Main` işlevi, bir ortam değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="c0d23-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="c0d23-115">Bu ortam değişkeni kullanılarak alınabilir `ERRORLEVEL` bir toplu iş dosyasından veya `$LastExitCode` powershell'den.</span><span class="sxs-lookup"><span data-stu-id="c0d23-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="c0d23-116">Kullanarak uygulama derleme [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` komutu.</span><span class="sxs-lookup"><span data-stu-id="c0d23-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="c0d23-117">Ardından, uygulamayı çalıştırmak ve sonucu görüntülemek için bir Powershell betiği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0d23-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="c0d23-118">Aşağıdaki kodu bir metin dosyasına yapıştırın ve kaydedileceği `test.ps1` projeyi içeren klasörü içinde.</span><span class="sxs-lookup"><span data-stu-id="c0d23-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="c0d23-119">Yazarak powershell betiğini çalıştırma `test.ps1` powershell komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="c0d23-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="c0d23-120">Toplu iş dosyası, kod sıfır döndürdüğünden, başarı rapor eder.</span><span class="sxs-lookup"><span data-stu-id="c0d23-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="c0d23-121">Ancak, sıfır olmayan bir değer döndürmez ve ardından programı yeniden derlemek için MainReturnValTest.cs değiştirirseniz, powershell betiğinin sonraki yürütme hata rapor eder.</span><span class="sxs-lookup"><span data-stu-id="c0d23-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="c0d23-122">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="c0d23-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="c0d23-123">Async Main dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="c0d23-123">Async Main return values</span></span>

<span data-ttu-id="c0d23-124">Async Main dönüş değerleri taşımak için zaman uyumsuz yöntemleri çağırma gerekli ortak kod `Main` derleyici tarafından üretilen kod.</span><span class="sxs-lookup"><span data-stu-id="c0d23-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="c0d23-125">Daha önce zaman uyumsuz kod arama ve zaman uyumsuz işlem tamamlanana kadar programınızı çalıştırdınız emin olmak için bu yapıyı yazma gerekir:</span><span class="sxs-lookup"><span data-stu-id="c0d23-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="c0d23-126">Şimdi bu tarafından değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="c0d23-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="c0d23-127">Yeni sözdizimi avantajı, derleyici her zaman doğru kodu oluşturur ' dir.</span><span class="sxs-lookup"><span data-stu-id="c0d23-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="c0d23-128">Derleyicinin ürettiği kodu</span><span class="sxs-lookup"><span data-stu-id="c0d23-128">Compiler generated code</span></span>

<span data-ttu-id="c0d23-129">Uygulama giriş noktası döndürdüğünde bir `Task` veya `Task<int>`, derleyici uygulama kodunda bildirilen girdi noktası yöntemini çağıran yeni bir giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c0d23-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="c0d23-130">Bu giriş noktası çağrıldı varsayarak `$GeneratedMain`, derleyici bu giriş noktaları için şu kodu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c0d23-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="c0d23-131">`static Task Main()` denk yayan derleme sonuçları `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c0d23-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c0d23-132">`static Task Main(string[])` denk yayan derleme sonuçları `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c0d23-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c0d23-133">`static Task<int> Main()` denk yayan derleme sonuçları `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c0d23-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c0d23-134">`static Task<int> Main(string[])` denk yayan derleme sonuçları `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c0d23-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="c0d23-135">Örnekleri kullandıysanız `async` değiştiricisi `Main` yöntemi, derleyici aynı kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="c0d23-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0d23-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0d23-136">See also</span></span>

- [<span data-ttu-id="c0d23-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c0d23-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c0d23-138">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c0d23-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c0d23-139">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c0d23-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="c0d23-140">Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c0d23-140">How to: Display Command Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
