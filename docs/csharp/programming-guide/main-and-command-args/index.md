---
title: Ana() ve komut satırı bağımsız değişkenleri (C# programlama Kılavuzu)
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
ms.openlocfilehash: 144d03edf28464717430bd0ae83db637578d8296
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698597"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="82365-102">Ana() ve komut satırı bağımsız değişkenleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="82365-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="82365-103">`Main` Bir C# uygulaması giriş noktası bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="82365-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="82365-104">(Kitaplıkları ve Hizmetleri gerektirmez bir `Main` yöntemi olarak bir giriş noktası.) Uygulama başlatıldığında `Main` çağrılan ilk yöntem yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="82365-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="82365-105">Yalnızca bir C# programında bir giriş noktası olabilir.</span><span class="sxs-lookup"><span data-stu-id="82365-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="82365-106">Birden fazla sınıf varsa bir `Main` yöntemi programınızla birlikte derleme gerekir **/main** belirtmek için derleyici seçeneği `Main` giriş noktası olarak kullanmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="82365-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="82365-107">Daha fazla bilgi için [/Main (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="82365-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a><span data-ttu-id="82365-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="82365-108">Overview</span></span>

- <span data-ttu-id="82365-109">`Main` Yöntemdir giriş noktası yürütülebilir bir program; Burada, program denetimi başlar ve biter.</span><span class="sxs-lookup"><span data-stu-id="82365-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="82365-110">`Main` bir sınıf veya yapı içinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="82365-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="82365-111">`Main` olmalıdır [statik](../../../csharp/language-reference/keywords/static.md) ve olmaması [genel](../../../csharp/language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="82365-111">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="82365-112">(Önceki örnekte, varsayılan erişim aldığı [özel](../../../csharp/language-reference/keywords/private.md).) Kapsayan sınıfın veya yapının statik olması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="82365-112">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="82365-113">`Main` yalnızca birine sahip olabilir bir `void`, `int`, ya da C# 7.1 ile başlangıç `Task`, veya `Task<int>` dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="82365-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="82365-114">Ve yalnızca, `Main` döndürür bir `Task` veya `Task<int>`, bildirimi `Main` içerebilir [ `async` ](../../language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="82365-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="82365-115">Bu özellikle hariç Not bir `async void Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="82365-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="82365-116">`Main` Yöntemi ile veya olmadan bildirilebilir bir `string[]` komut satırı bağımsız değişkenleri içeren bir parametre.</span><span class="sxs-lookup"><span data-stu-id="82365-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="82365-117">Visual Studio, Windows uygulamaları oluşturmak için kullanılırken, parametresi el ile ekleyin Aksi takdirde kullanmak <xref:System.Environment> komut satırı bağımsız değişkenlerini almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="82365-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="82365-118">Parametre sıfır dizinli komut satırı bağımsız değişkenleri okunur.</span><span class="sxs-lookup"><span data-stu-id="82365-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="82365-119">C ve C++'ın aksine, programın adı, ilk komut satırı bağımsız değişkeni işlenmez.</span><span class="sxs-lookup"><span data-stu-id="82365-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="82365-120">Ek `async` ve `Task`, `Task<int>` dönüş türleri, konsol uygulamaları başlatmak gerektiğinde program kodu basitleştirir ve `await` zaman uyumsuz işlemler `Main`.</span><span class="sxs-lookup"><span data-stu-id="82365-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="82365-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="82365-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="82365-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82365-122">See Also</span></span>

- [<span data-ttu-id="82365-123">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="82365-123">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="82365-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="82365-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="82365-125">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="82365-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [<span data-ttu-id="82365-126">C# Programı İçinde</span><span class="sxs-lookup"><span data-stu-id="82365-126">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
