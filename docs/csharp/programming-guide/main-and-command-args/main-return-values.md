---
title: Main () dönüş değerleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 13d1eda178a4c2580af67ef5a7198e7f0884a7d6
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884403"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="753c3-102">Main () dönüş değerleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="753c3-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="753c3-103">`Main` yöntemi `void`döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="753c3-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="753c3-104">Ayrıca, bir `int`döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="753c3-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="753c3-105">`Main` dönüş değeri kullanılmazsa, `void` döndürme biraz daha basit bir koda izin verir.</span><span class="sxs-lookup"><span data-stu-id="753c3-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="753c3-106">Ancak, bir tamsayı döndürmek programın durum bilgilerini yürütülebilir dosyayı çağıran diğer programlarla veya betiklerine iletmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="753c3-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="753c3-107">`Main` dönüş değeri, işlem için çıkış kodu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="753c3-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="753c3-108">`Main` `void` döndürüldüğünde çıkış kodu örtük olarak `0`olur.</span><span class="sxs-lookup"><span data-stu-id="753c3-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="753c3-109">Aşağıdaki örnek, `Main` ' den dönüş değerine nasıl erişildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="753c3-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="753c3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="753c3-110">Example</span></span>

<span data-ttu-id="753c3-111">Bu örnek [.NET Core](../../../core/index.md) komut satırı araçlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="753c3-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="753c3-112">.NET Core komut satırı araçları hakkında bilginiz yoksa [, bu Başlarken konusunda bilgi](../../../core/tutorials/cli-create-console-app.md)edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="753c3-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/cli-create-console-app.md).</span></span>

<span data-ttu-id="753c3-113">*Program.cs* içinde `Main` yöntemini aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="753c3-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="753c3-114">Bir program Windows 'da yürütüldüğünde, `Main` işlevinden döndürülen herhangi bir değer bir ortam değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="753c3-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="753c3-115">Bu ortam değişkeni bir toplu iş dosyasından `ERRORLEVEL` veya PowerShell 'den `$LastExitCode` kullanılarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="753c3-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="753c3-116">[DotNet clı](../../../core/tools/dotnet.md) `dotnet build` komutunu kullanarak uygulamayı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="753c3-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="753c3-117">Sonra, uygulamayı çalıştırmak için bir PowerShell betiği oluşturun ve sonucu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="753c3-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="753c3-118">Aşağıdaki kodu bir metin dosyasına yapıştırın ve projeyi içeren klasöre `test.ps1` olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="753c3-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="753c3-119">PowerShell komut isteminde `test.ps1` yazarak PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="753c3-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="753c3-120">Kod sıfır döndürdüğünden, toplu iş dosyası başarıyı bildirir.</span><span class="sxs-lookup"><span data-stu-id="753c3-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="753c3-121">Ancak, MainReturnValTest.cs değerini sıfır olmayan bir değer döndürecek şekilde değiştirip programı yeniden derlerseniz, PowerShell betiğinin sonraki yürütmesi hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="753c3-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="753c3-122">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="753c3-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="753c3-123">Zaman uyumsuz ana dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="753c3-123">Async Main return values</span></span>

<span data-ttu-id="753c3-124">Zaman uyumsuz ana dönüş değerleri, derleyici tarafından oluşturulan koda `Main` zaman uyumsuz yöntemleri çağırmak için gereken ortak kodu taşır.</span><span class="sxs-lookup"><span data-stu-id="753c3-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="753c3-125">Daha önce, zaman uyumsuz kodu çağırmak ve programınızın zaman uyumsuz işlem tamamlanana kadar çalıştığından emin olmak için bu yapıyı yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="753c3-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="753c3-126">Şimdi bu, şu şekilde değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="753c3-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="753c3-127">Yeni sözdiziminin avantajı, derleyicinin her zaman doğru kodu üretmesinin avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="753c3-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="753c3-128">Derleyicinin ürettiği kod</span><span class="sxs-lookup"><span data-stu-id="753c3-128">Compiler generated code</span></span>

<span data-ttu-id="753c3-129">Uygulama giriş noktası bir `Task` veya `Task<int>`döndürdüğünde, derleyici uygulama kodunda belirtilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="753c3-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="753c3-130">Bu giriş noktasının `$GeneratedMain`çağrıldığı kabul edildiğinde, derleyici bu giriş noktaları için aşağıdaki kodu üretir:</span><span class="sxs-lookup"><span data-stu-id="753c3-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="753c3-131">`static Task Main()`, derleyicinin `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur</span><span class="sxs-lookup"><span data-stu-id="753c3-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="753c3-132">`static Task Main(string[])`, derleyicinin `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur</span><span class="sxs-lookup"><span data-stu-id="753c3-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="753c3-133">`static Task<int> Main()`, derleyicinin `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur</span><span class="sxs-lookup"><span data-stu-id="753c3-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="753c3-134">`static Task<int> Main(string[])`, derleyicinin `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur</span><span class="sxs-lookup"><span data-stu-id="753c3-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="753c3-135">Örnekler `Main` yönteminde `async` değiştirici kullandıysanız, derleyici aynı kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="753c3-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="753c3-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="753c3-136">See also</span></span>

- [<span data-ttu-id="753c3-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="753c3-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="753c3-138">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="753c3-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="753c3-139">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="753c3-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="753c3-140">Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="753c3-140">How to: Display Command Line Arguments</span></span>](./how-to-display-command-line-arguments.md)
