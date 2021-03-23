---
title: Üst düzey deyimler-C# Programlama Kılavuzu
description: C# 9 ve sonraki sürümlerinde en üst düzey deyimler hakkında bilgi edinin.
ms.date: 03/08/2021
helpviewer_keywords:
- C# language, top-level statements
- C# language, Main method
ms.openlocfilehash: 31a9d3bba302823015058d59ca79da45754b761f
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881060"
---
# <a name="top-level-statements-c-programming-guide"></a><span data-ttu-id="e7114-103">Üst düzey deyimler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e7114-103">Top-level statements (C# Programming Guide)</span></span>

<span data-ttu-id="e7114-104">C# 9 ' dan itibaren bir `Main` konsol uygulaması projesine bir yöntemi açıkça eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e7114-104">Starting in C# 9, you don't have to explicitly include a `Main` method in a console application project.</span></span> <span data-ttu-id="e7114-105">Bunun yerine, *en üst düzey deyimler* özelliğini kullanarak yazmanız gerektiğini kodun en aza indirmenize olanak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7114-105">Instead, you can use the *top-level statements* feature to minimize the code you have to write.</span></span> <span data-ttu-id="e7114-106">Bu durumda, derleyici uygulama için bir sınıf ve `Main` Yöntem giriş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e7114-106">In this case, the compiler generates a class and `Main` method entry point for the application.</span></span>

<span data-ttu-id="e7114-107">C# 9 ' da tüm C# programı olan bir *program. cs* dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e7114-107">Here's a *Program.cs* file that is a complete C# program in C# 9:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

<span data-ttu-id="e7114-108">Üst düzey deyimler, Azure Işlevleri ve GitHub eylemleri gibi küçük yardımcı programlara yönelik basit programlar yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7114-108">Top-level statements let you write simple programs for small utilities such as Azure Functions and GitHub Actions.</span></span> <span data-ttu-id="e7114-109">Ayrıca, yeni C# programcıları için kod öğrenmeye ve yazmaya başlamanıza da daha kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e7114-109">They also make it simpler for new C# programmers to get started learning and writing code.</span></span>

<span data-ttu-id="e7114-110">Aşağıdaki bölümlerde, en üst düzey deyimlerle yapabilecekleriniz ve yapabileceklerinize ilişkin kurallar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7114-110">The following sections explain the rules on what you can and can't do with top-level statements.</span></span>

## <a name="only-one-top-level-file"></a><span data-ttu-id="e7114-111">Yalnızca bir üst düzey dosya</span><span class="sxs-lookup"><span data-stu-id="e7114-111">Only one top-level file</span></span>

<span data-ttu-id="e7114-112">Bir uygulamanın yalnızca bir giriş noktası olması gerekir, bu nedenle bir projede en üst düzey deyimlerle yalnızca bir dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7114-112">An application must have only one entry point, so a project can have only one file with top-level statements.</span></span> <span data-ttu-id="e7114-113">En üst düzey deyimleri bir projede birden fazla dosyaya koymak aşağıdaki derleyici hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="e7114-113">Putting top-level statements in more than one file in a project results in the following compiler error:</span></span>

> <span data-ttu-id="e7114-114">CS8802 yalnızca bir derleme birimi en üst düzey deyimlerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7114-114">CS8802 Only one compilation unit can have top-level statements.</span></span>

<span data-ttu-id="e7114-115">Bir proje, en üst düzey deyimleri olmayan herhangi bir sayıda ek kaynak kodu dosyasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7114-115">A project can have any number of additional source code files that don't have top-level statements.</span></span>

## <a name="no-other-entry-points"></a><span data-ttu-id="e7114-116">Başka giriş noktası yok</span><span class="sxs-lookup"><span data-stu-id="e7114-116">No other entry points</span></span>

<span data-ttu-id="e7114-117">Bir `Main` yöntemi açıkça yazabilirsiniz, ancak giriş noktası olarak çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="e7114-117">You can write a `Main` method explicitly, but it can't function as an entry point.</span></span> <span data-ttu-id="e7114-118">Derleyici aşağıdaki uyarıyı verir:</span><span class="sxs-lookup"><span data-stu-id="e7114-118">The compiler issues the following warning:</span></span>

> <span data-ttu-id="e7114-119">CS7022, programın giriş noktası genel koddur; ' Main () ' giriş noktası yoksayılıyor.</span><span class="sxs-lookup"><span data-stu-id="e7114-119">CS7022 The entry point of the program is global code; ignoring 'Main()' entry point.</span></span>

<span data-ttu-id="e7114-120">Üst düzey deyimler içeren bir projede, proje bir veya daha fazla yöntem içerse bile, giriş noktasını seçmek için [-Main](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject) derleyici seçeneğini kullanamazsınız `Main` .</span><span class="sxs-lookup"><span data-stu-id="e7114-120">In a project with top-level statements, you can't use the [-main](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject) compiler option to select the entry point, even if the project has one or more `Main` methods.</span></span>

## <a name="using-directives"></a><span data-ttu-id="e7114-121">`using` yönergeler</span><span class="sxs-lookup"><span data-stu-id="e7114-121">`using` directives</span></span>

<span data-ttu-id="e7114-122">Using yönergelerini eklerseniz, bu örnekte olduğu gibi, ilk olarak dosyada gelmelidir:</span><span class="sxs-lookup"><span data-stu-id="e7114-122">If you include using directives, they must come first in the file, as in this example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

## <a name="global-namespace"></a><span data-ttu-id="e7114-123">Genel ad alanı</span><span class="sxs-lookup"><span data-stu-id="e7114-123">Global namespace</span></span>

<span data-ttu-id="e7114-124">En üst düzey deyimler, genel ad alanında örtülü olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="e7114-124">Top-level statements are implicitly in the global namespace.</span></span>

## <a name="namespaces-and-type-definitions"></a><span data-ttu-id="e7114-125">Ad alanları ve tür tanımları</span><span class="sxs-lookup"><span data-stu-id="e7114-125">Namespaces and type definitions</span></span>

<span data-ttu-id="e7114-126">En üst düzey deyimlerle bir dosya ad alanları ve tür tanımları da içerebilir, ancak en üst düzey deyimlerden sonra gelmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7114-126">A file with top-level statements can also contain namespaces and type definitions, but they must come after the top-level statements.</span></span> <span data-ttu-id="e7114-127">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e7114-127">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-2/Program.cs":::

## `args`

<span data-ttu-id="e7114-128">En üst düzey deyimler, `args` girilen tüm komut satırı bağımsız değişkenlerine erişmek için değişkenine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="e7114-128">Top-level statements can reference the `args` variable to access any command-line arguments that were entered.</span></span> <span data-ttu-id="e7114-129">`args`Değişken hiçbir şekilde null değildir ancak `Length` hiçbir komut satırı bağımsız değişkeni sağlanmazsa sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="e7114-129">The `args` variable is never null but its `Length` is zero if no command-line arguments were provided.</span></span> <span data-ttu-id="e7114-130">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e7114-130">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-3/Program.cs":::

## `await`

<span data-ttu-id="e7114-131">Kullanarak zaman uyumsuz bir yöntem çağırabilirsiniz `await` .</span><span class="sxs-lookup"><span data-stu-id="e7114-131">You can call an async method by using `await`.</span></span> <span data-ttu-id="e7114-132">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e7114-132">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-4/Program.cs":::

## <a name="exit-code-for-the-process"></a><span data-ttu-id="e7114-133">İşlem için çıkış kodu</span><span class="sxs-lookup"><span data-stu-id="e7114-133">Exit code for the process</span></span>

<span data-ttu-id="e7114-134">`int`Uygulama sona erdiğinde bir değer döndürmek için, `return` ifadesini döndüren bir yöntemde olduğu gibi kullanın `Main` `int` .</span><span class="sxs-lookup"><span data-stu-id="e7114-134">To return an `int` value when the application ends, use the `return` statement as you would in a `Main` method that returns an `int`.</span></span> <span data-ttu-id="e7114-135">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e7114-135">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-5/Program.cs":::

## <a name="implicit-entry-point-method"></a><span data-ttu-id="e7114-136">Örtük giriş noktası yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7114-136">Implicit entry point method</span></span>

<span data-ttu-id="e7114-137">Derleyici, en üst düzey deyimlerle bir proje için program giriş noktası olarak kullanılacak bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e7114-137">The compiler generates a method to serve as the program entry point for a project with top-level statements.</span></span> <span data-ttu-id="e7114-138">Bu yöntemin adı aslında değil `Main` , kodunuzun doğrudan başvurılemeyeceğini bir uygulama ayrıntısı.</span><span class="sxs-lookup"><span data-stu-id="e7114-138">The name of this method isn't actually `Main`, it's an implementation detail that your code can't reference directly.</span></span> <span data-ttu-id="e7114-139">Yönteminin imzası, en üst düzey deyimlerin anahtar sözcüğünü mi yoksa deyimini mi içerdiğini bağlıdır `await` `return` .</span><span class="sxs-lookup"><span data-stu-id="e7114-139">The signature of the method depends on whether the top-level statements contain the `await` keyword or the `return` statement.</span></span> <span data-ttu-id="e7114-140">Aşağıdaki tabloda, yöntemi için tablodaki Yöntem adı kullanılarak yöntem imzasının nasıl görünebilecekleri gösterilmektedir `Main` .</span><span class="sxs-lookup"><span data-stu-id="e7114-140">The following table shows what the method signature would look like, using the method name `Main` in the table for convenience.</span></span>

| <span data-ttu-id="e7114-141">Üst düzey kod içerir</span><span class="sxs-lookup"><span data-stu-id="e7114-141">Top-level code contains</span></span>| <span data-ttu-id="e7114-142">Örtük `Main` imza</span><span class="sxs-lookup"><span data-stu-id="e7114-142">Implicit `Main` signature</span></span>                    |
|------------------------|----------------------------------------------|
| <span data-ttu-id="e7114-143">`await` ve `return`</span><span class="sxs-lookup"><span data-stu-id="e7114-143">`await` and `return`</span></span>   | `static async Task<int> Main(string[] args)` |
| `await`                | `static async Task Main(string[] args)`      |
| `return`               | `static int Main(string[] args)`             |
| <span data-ttu-id="e7114-144">Hayır `await` veya `return`</span><span class="sxs-lookup"><span data-stu-id="e7114-144">No `await` or `return`</span></span> | `static void Main(string[] args)`            |

## <a name="c-language-specification"></a><span data-ttu-id="e7114-145">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e7114-145">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
[<span data-ttu-id="e7114-146">Üst düzey deyimler</span><span class="sxs-lookup"><span data-stu-id="e7114-146">Top-level statements</span></span>](~/_csharplang/proposals/csharp-9.0/top-level-statements.md)

## <a name="see-also"></a><span data-ttu-id="e7114-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7114-147">See also</span></span>

- [<span data-ttu-id="e7114-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e7114-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e7114-149">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e7114-149">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="e7114-150">C# programı içinde</span><span class="sxs-lookup"><span data-stu-id="e7114-150">Inside a C# Program</span></span>](../inside-a-program/index.md)
