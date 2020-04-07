---
title: Ana() İade Değerleri - C# Programlama Kılavuzu
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 7061b6c1988da9f6dfac115ee555a914531df863
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805932"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="53337-102">Ana() iade değerleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="53337-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="53337-103">Yöntem `Main` döndürebilir: `void`</span><span class="sxs-lookup"><span data-stu-id="53337-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="53337-104">Ayrıca bir `int`döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="53337-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="53337-105">İade `Main` değeri kullanılmazsa, geri `void` döndürme biraz daha basit bir kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="53337-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="53337-106">Ancak, bir arayıcı döndürülen program, durum bilgilerini yürütülebilir dosyayı çağıran diğer programlara veya komut dosyalarına iletilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="53337-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="53337-107">Gelen `Main` iade değeri, işlemin çıkış kodu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="53337-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="53337-108">Döndürülürse, `void` `Main`çıkış kodu örtülü `0`olarak .</span><span class="sxs-lookup"><span data-stu-id="53337-108">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="53337-109">Aşağıdaki örnek, geri `Main` dönüş değerinin nasıl erişilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="53337-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="53337-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="53337-110">Example</span></span>

<span data-ttu-id="53337-111">Bu örnekte [.NET Core](../../../core/index.yml) komut satırı araçları kullanır.</span><span class="sxs-lookup"><span data-stu-id="53337-111">This example uses [.NET Core](../../../core/index.yml) command-line tools.</span></span> <span data-ttu-id="53337-112">.NET Core komut satırı araçlarını bilmiyorsanız, bu [başlangıç makalesinde](../../../core/tutorials/cli-create-console-app.md)bunlar hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53337-112">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/cli-create-console-app.md).</span></span>

<span data-ttu-id="53337-113">Yöntemi `Main` aşağıdaki *gibi program.cs* değiştirin:</span><span class="sxs-lookup"><span data-stu-id="53337-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="53337-114">Bir program Windows'da yürütüldüğünde, `Main` işlevden döndürülen herhangi bir değer bir ortam değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="53337-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="53337-115">Bu ortam değişkeni bir `ERRORLEVEL` toplu iş dosyasından veya `$LastExitCode` powershell'den alınabilir.</span><span class="sxs-lookup"><span data-stu-id="53337-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="53337-116">Uygulamayı [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` komutunu kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53337-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="53337-117">Ardından, uygulamayı çalıştırmak ve sonucu görüntülemek için bir Powershell komut dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="53337-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="53337-118">Aşağıdaki kodu bir metin dosyasına yapıştırın `test.ps1` ve projeyi içeren klasörde olduğu gibi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="53337-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="53337-119">Powershell komut isteminde `test.ps1` yazarak powershell komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="53337-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="53337-120">Kod sıfır döndürüldüğünden, toplu işdosyası başlıcayı bildirir.</span><span class="sxs-lookup"><span data-stu-id="53337-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="53337-121">Ancak, sıfır olmayan bir değer döndürmek ve sonra programı yeniden derlemek için MainReturnValTest.cs değiştirirseniz, powershell komut dosyasının sonraki yürütülmesi hatası bildirir.</span><span class="sxs-lookup"><span data-stu-id="53337-121">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="53337-122">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="53337-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="53337-123">Async Ana iade değerleri</span><span class="sxs-lookup"><span data-stu-id="53337-123">Async Main return values</span></span>

<span data-ttu-id="53337-124">Async Main return değerleri, derleyici tarafından oluşturulan `Main` koda eşzamanlı yöntemleri çağırmak için gerekli olan ortak kodu taşır.</span><span class="sxs-lookup"><span data-stu-id="53337-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="53337-125">Daha önce, eşzamanlı kodu çağırmak ve programınızın eşzamanlı işlem tamamlanana kadar çalıştırdığından emin olmak için bu yapıyı yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="53337-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="53337-126">Şimdi, bu değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="53337-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="53337-127">Yeni sözdiziminin avantajı, derleyicinin her zaman doğru kodu oluşturmasıdır.</span><span class="sxs-lookup"><span data-stu-id="53337-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="53337-128">Derleyici tarafından oluşturulan kod</span><span class="sxs-lookup"><span data-stu-id="53337-128">Compiler-generated code</span></span>

<span data-ttu-id="53337-129">Uygulama giriş noktası a `Task` `Task<int>`veya , derleyici döndürdüğünde, uygulama kodunda bildirilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53337-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="53337-130">Bu giriş noktasının `$GeneratedMain`çağrıldığını varsayarsak, derleyici bu giriş noktaları için aşağıdaki kodu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="53337-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="53337-131">`static Task Main()`eşdeğeri yayan derleyici sonuçları`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="53337-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="53337-132">`static Task Main(string[])`eşdeğeri yayan derleyici sonuçları`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="53337-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="53337-133">`static Task<int> Main()`eşdeğeri yayan derleyici sonuçları`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="53337-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="53337-134">`static Task<int> Main(string[])`eşdeğeri yayan derleyici sonuçları`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="53337-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="53337-135">Örnekler `Main` yöntemde `async` değiştirici kullanılırsa, derleyici aynı kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53337-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="53337-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53337-136">See also</span></span>

- [<span data-ttu-id="53337-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="53337-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="53337-138">C# Referans</span><span class="sxs-lookup"><span data-stu-id="53337-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="53337-139">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="53337-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="53337-140">Komut satırı bağımsız değişkenleri nasıl görüntülenir?</span><span class="sxs-lookup"><span data-stu-id="53337-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
