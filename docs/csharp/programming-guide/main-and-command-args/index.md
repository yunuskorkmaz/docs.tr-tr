---
title: Main () ve komut satırı bağımsız değişkenleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: a5707e8cfff11dd9d27fffc9deb41662fb2c4460
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281762"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="b9da4-102">Main () ve komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b9da4-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="b9da4-103">`Main` yöntemi, bir C# uygulamanın giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="b9da4-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="b9da4-104">(Kitaplıklar ve hizmetler, giriş noktası olarak bir `Main` yöntemi gerektirmez.) Uygulama başlatıldığında `Main` yöntemi çağrılan ilk yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="b9da4-105">Bir C# programda yalnızca bir giriş noktası olabilir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="b9da4-106">`Main` yöntemine sahip birden fazla sınıfınız varsa, giriş noktası olarak hangi `Main` yönteminin kullanılacağını belirtmek için programınızı **/Main** derleyici seçeneğiyle derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="b9da4-107">Daha fazla bilgi için bkz. [-MainC# (derleyici seçenekleri)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b9da4-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="b9da4-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b9da4-108">Overview</span></span>

- <span data-ttu-id="b9da4-109">`Main` yöntemi, çalıştırılabilir programın giriş noktasıdır; Program denetiminin başladığı ve bittiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="b9da4-110">`Main` bir sınıf veya yapı içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="b9da4-111">`Main` [statik](../../language-reference/keywords/static.md) olması ve [genel](../../language-reference/keywords/public.md)olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="b9da4-112">(Önceki örnekte, [Private](../../language-reference/keywords/private.md)'ın varsayılan erişimini alır.) Kapsayan sınıf veya yapının statik olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b9da4-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="b9da4-113">`Main`, C# 7,1, `Task`veya `Task<int>` dönüş türünden başlayarak `void`, `int`ya da olabilir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="b9da4-114">Yalnızca `Main` bir `Task` veya `Task<int>`döndürürse, `Main` bildirimi [`async`](../../language-reference/keywords/async.md) değiştiricisini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="b9da4-115">Bunun özellikle bir `async void Main` yöntemi dışladığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b9da4-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="b9da4-116">`Main` yöntemi komut satırı bağımsız değişkenleri içeren bir `string[]` parametresiyle veya bu parametre olmadan bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="b9da4-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="b9da4-117">Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametresini el ile ekleyebilir veya [komut satırı bağımsız değişkenlerini](command-line-arguments.md)almak için <xref:System.Environment.GetCommandLineArgs> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9da4-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="b9da4-118">Parametreler, sıfır dizinli komut satırı bağımsız değişkenleri olarak okunurdur.</span><span class="sxs-lookup"><span data-stu-id="b9da4-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="b9da4-119">C ve C++' nin aksine, programın adı `args` dizideki ilk komut satırı bağımsız değişkeni olarak değerlendirilmez, ancak <xref:System.Environment.GetCommandLineArgs> yönteminin ilk öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="b9da4-120">Geçerli `Main` imzalarının listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b9da4-120">The following is a list of valid `Main` signatures:</span></span>

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

<span data-ttu-id="b9da4-121">`async` ve `Task`ekleme `Task<int>` dönüş türleri, konsol uygulamalarının `Main`zaman uyumsuz işlemlere `await` başlaması gerektiğinde program kodunu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b9da4-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b9da4-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b9da4-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b9da4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9da4-123">See also</span></span>

- [<span data-ttu-id="b9da4-124">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="b9da4-124">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="b9da4-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b9da4-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b9da4-126">Methods</span><span class="sxs-lookup"><span data-stu-id="b9da4-126">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="b9da4-127">C# Programı İçinde</span><span class="sxs-lookup"><span data-stu-id="b9da4-127">Inside a C# Program</span></span>](../inside-a-program/index.md)
