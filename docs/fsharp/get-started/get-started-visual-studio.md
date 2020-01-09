---
title: Visual Studio F# 'da kullanmaya başlayın
description: Visual Studio ile nasıl F# kullanacağınızı öğrenin.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337343"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="b1fd5-103">Visual Studio F# 'da kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="b1fd5-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="b1fd5-104">F#Visual Studio tümleşik F# geliştirme ORTAMıNDA (IDE) Visual araçları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-104">F# and the Visual F# tooling are supported in the Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="b1fd5-105">Başlamak için, [Visual Studio 'nun destek F# ile yüklü](install-fsharp.md#install-f-with-visual-studio)olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-105">To begin, ensure that you have [Visual Studio installed with F# support](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b1fd5-106">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1fd5-106">Create a console application</span></span>

<span data-ttu-id="b1fd5-107">Visual Studio 'daki en temel projelerden biri konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-107">One of the most basic projects in Visual Studio is the console app.</span></span> <span data-ttu-id="b1fd5-108">Bunun nasıl oluşturulacağı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b1fd5-108">Here's how to create one:</span></span>

1. <span data-ttu-id="b1fd5-109">Visual Studio 2019 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-109">Open Visual Studio 2019.</span></span>

2. <span data-ttu-id="b1fd5-110">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-110">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="b1fd5-111">**Yeni proje oluştur** sayfasında, dil listesinden öğesini seçin **F#** .</span><span class="sxs-lookup"><span data-stu-id="b1fd5-111">On the **Create a new project** page, choose **F#** from the Language list.</span></span>

4. <span data-ttu-id="b1fd5-112">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-112">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

5. <span data-ttu-id="b1fd5-113">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-113">On the **Configure your new project** page, enter a name in the **Project name** box.</span></span> <span data-ttu-id="b1fd5-114">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-114">Then, choose **Create**.</span></span>

   <span data-ttu-id="b1fd5-115">Visual Studio yeni F# projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-115">Visual Studio creates the new F# project.</span></span> <span data-ttu-id="b1fd5-116">Çözüm Gezgini penceresinde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-116">You can see it in the Solution Explorer window.</span></span>

## <a name="write-the-code"></a><span data-ttu-id="b1fd5-117">Kodu yazma</span><span class="sxs-lookup"><span data-stu-id="b1fd5-117">Write the code</span></span>

<span data-ttu-id="b1fd5-118">Biraz kod yazarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-118">Let's get started by writing some code.</span></span> <span data-ttu-id="b1fd5-119">`Program.fs` dosyasının açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1fd5-119">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="b1fd5-120">Önceki kod örneği, `x` adlı bir girişi alan `square` adlı bir işlevi tanımlar ve kendisiyle çarpar.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-120">The previous code sample defines a function called `square` that takes an input named `x` and multiplies it by itself.</span></span> <span data-ttu-id="b1fd5-121">F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından `x` türünün belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-121">Because F# uses [Type inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span> <span data-ttu-id="b1fd5-122">F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve `square` nasıl çağrıldığını temel alarak `x` bir tür atar.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-122">The F# compiler understands the types where multiplication is valid and assigns a type to `x` based on how `square` is called.</span></span> <span data-ttu-id="b1fd5-123">`square`üzerine geldiğinizde, aşağıdakileri görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1fd5-123">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="b1fd5-124">İşlevin tür imzası olarak bilinen budur.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-124">This is what is known as the function's type signature.</span></span> <span data-ttu-id="b1fd5-125">Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir".</span><span class="sxs-lookup"><span data-stu-id="b1fd5-125">It can be read like this: "Square is a function that takes an integer named x and produces an integer".</span></span> <span data-ttu-id="b1fd5-126">Derleyici, `int` türü `square` verdi; Bunun nedeni, çarpma 'nın *Tüm* türler genelinde genel olmaması, ancak kapalı bir tür kümesidir.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-126">The compiler gave `square` the `int` type for now; this is because multiplication is not generic across *all* types but rather a closed set of types.</span></span> <span data-ttu-id="b1fd5-127">`float`F# gibi farklı bir giriş türüyle `square` çağırırsanız derleyici tür imzasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-127">The F# compiler will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="b1fd5-128">`main`, `EntryPoint` özniteliğiyle donatılmış başka bir işlev tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-128">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute.</span></span> <span data-ttu-id="b1fd5-129">Bu öznitelik, F# derleyicinin program yürütmesinin burada başlaması gerektiğini söyler.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-129">This attribute tells the F# compiler that program execution should start there.</span></span> <span data-ttu-id="b1fd5-130">Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-130">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="b1fd5-131">Bir `12`bağımsız değişkeniyle `square` işlevini çağırdığınız `main`giriş noktası işlevidir.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-131">It is in the entry point function, `main`, that you call the `square` function with an argument of `12`.</span></span> <span data-ttu-id="b1fd5-132">F# Derleyici daha sonra `int -> int` (bir `int` alan ve bir `int`üreten bir işlev) `square` türünü atar.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-132">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function that takes an `int` and produces an `int`).</span></span> <span data-ttu-id="b1fd5-133">`printfn` çağrısı, biçim dizesi kullanan ve sonucu yazdıran (ve yeni bir satır) biçimli bir yazdırma işlevidir.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-133">The call to `printfn` is a formatted printing function that uses a format string and prints the result (and a new line).</span></span> <span data-ttu-id="b1fd5-134">C stili programlama dillerine benzer biçim dizesinde, kendisine geçirilen bağımsız değişkenlere karşılık gelen parametreler (`%d`) bulunur, bu durumda `12` ve `(square 12)`.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-134">The format string, similar to C-style programming languages, has parameters (`%d`) that correspond to the arguments that are passed to it, in this case, `12` and `(square 12)`.</span></span>

## <a name="run-the-code"></a><span data-ttu-id="b1fd5-135">Kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b1fd5-135">Run the code</span></span>

<span data-ttu-id="b1fd5-136">Kodu çalıştırabilir ve **Ctrl**+**F5**tuşlarına basarak sonuçları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-136">You can run the code and see the results by pressing **Ctrl**+**F5**.</span></span> <span data-ttu-id="b1fd5-137">Alternatif olarak, üst düzey menü çubuğundan hata **ayıklama** > **Başlat** ' ı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-137">Alternatively, you can choose the **Debug** > **Start Without Debugging** from the top-level menu bar.</span></span> <span data-ttu-id="b1fd5-138">Bu, programı hata ayıklama olmadan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-138">This runs the program without debugging.</span></span>

<span data-ttu-id="b1fd5-139">Aşağıdaki çıktı, Visual Studio 'nun açtığı konsol penceresine yazdırır:</span><span class="sxs-lookup"><span data-stu-id="b1fd5-139">The following output prints to the console window that Visual Studio opened:</span></span>

```console
12 squared is: 144!
```

<span data-ttu-id="b1fd5-140">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="b1fd5-140">Congratulations!</span></span> <span data-ttu-id="b1fd5-141">Visual Studio 'da ilk F# projenizi oluşturdunuz, bir değeri hesaplayan ve yazdıran F# bir işlev yazdı ve sonuçları görmek için projeyi çalıştırdık.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-141">You've created your first F# project in Visual Studio, written an F# function that calculates and prints a value, and run the project to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1fd5-142">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b1fd5-142">Next steps</span></span>

<span data-ttu-id="b1fd5-143">Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-143">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span> <span data-ttu-id="b1fd5-144">Visual Studio 'ya kopyalayabileceğiniz ve çalıştırmak için kullanabileceğiniz bazı yetenekler F# ve örnek kod örnekleri hakkında genel bir bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-144">It provides an overview of some of the capabilities of F# and ample code samples that you can copy into Visual Studio and run.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b1fd5-145">F# Turu</span><span class="sxs-lookup"><span data-stu-id="b1fd5-145">Tour of F#</span></span>](../tour.md)

## <a name="see-also"></a><span data-ttu-id="b1fd5-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1fd5-146">See also</span></span>

- [<span data-ttu-id="b1fd5-147">F#dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="b1fd5-147">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="b1fd5-148">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="b1fd5-148">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="b1fd5-149">Sembol ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="b1fd5-149">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
