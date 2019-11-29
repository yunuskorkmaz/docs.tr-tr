---
title: Visual Studio F# 'da kullanmaya başlayın
description: Visual Studio ile nasıl F# kullanacağınızı öğrenin.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552829"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="31940-103">Visual Studio F# 'da kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="31940-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="31940-104">F#Visual Studio IDE F# 'de de görsel araç desteklenir.</span><span class="sxs-lookup"><span data-stu-id="31940-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="31940-105">Başlamak için [Visual Studio 'nun F#ile yüklü ](install-fsharp.md#install-f-with-visual-studio)olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="31940-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="31940-106">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="31940-106">Creating a console application</span></span>

<span data-ttu-id="31940-107">Visual Studio 'daki en temel projelerden biri konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="31940-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="31940-108">Bunun nasıl yapılacağını aşağıda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31940-108">Here's how to do it.</span></span>  <span data-ttu-id="31940-109">Visual Studio açık olduğunda:</span><span class="sxs-lookup"><span data-stu-id="31940-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="31940-110">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="31940-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="31940-111">Yeni proje iletişim kutusunda, **Şablonlar**altında, **görsel F#** ' i görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="31940-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="31940-112">F# Şablonları göstermek için bunu seçin.</span><span class="sxs-lookup"><span data-stu-id="31940-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="31940-113">**.NET Core konsol uygulaması** ya da **konsol uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="31940-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="31940-114">Projeyi oluşturmak için Tamam düğmesini seçin! F#</span><span class="sxs-lookup"><span data-stu-id="31940-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="31940-115">Artık Çözüm Gezgini bir F# proje görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="31940-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="31940-116">Kodunuzu yazma</span><span class="sxs-lookup"><span data-stu-id="31940-116">Writing your code</span></span>

<span data-ttu-id="31940-117">Önce bazı kodları yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="31940-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="31940-118">`Program.fs` dosyasının açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="31940-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="31940-119">Önceki kod örneğinde, `x` adlı bir girişi alan ve kendisini kendisi ile çarparak `square` bir işlev tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="31940-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="31940-120">F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından `x` türünün belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="31940-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="31940-121">F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve `square` nasıl çağrıldığını temel alarak `x` bir tür atayacaktır.</span><span class="sxs-lookup"><span data-stu-id="31940-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="31940-122">`square`üzerine geldiğinizde, aşağıdakileri görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="31940-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="31940-123">İşlevin tür imzası olarak bilinen budur.</span><span class="sxs-lookup"><span data-stu-id="31940-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="31940-124">Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir".</span><span class="sxs-lookup"><span data-stu-id="31940-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="31940-125">Derleyicinin şu an için `int` türü `square` olduğunu unutmayın. bunun nedeni, çarpma işlemi *Tüm* türler genelinde geneldir, ancak bunun yerine kapalı bir tür kümesinde geneldir.</span><span class="sxs-lookup"><span data-stu-id="31940-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="31940-126">F# Derleyici bu noktada `int` çekildi, ancak `square` `float`gibi farklı bir giriş türüyle çağırırsanız tür imzasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="31940-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="31940-127">`main`başka bir işlev, `EntryPoint` özniteliğiyle birlikte düzenlenmiş ve bu, F# derleyicinin program yürütmesinin burada başlaması gerektiğini söylemelidir.</span><span class="sxs-lookup"><span data-stu-id="31940-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="31940-128">Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.</span><span class="sxs-lookup"><span data-stu-id="31940-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="31940-129">Bu işlev, `square` işlevini `12`bir bağımsız değişkeniyle çağıracağız.</span><span class="sxs-lookup"><span data-stu-id="31940-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="31940-130">F# Derleyici daha sonra `int -> int` (bir `int` alan ve bir `int`üreten bir işlev) `square` türünü atar.</span><span class="sxs-lookup"><span data-stu-id="31940-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="31940-131">`printfn` çağrısı, C stili programlama dillerine benzer bir biçim dizesi, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler ve sonra sonucu ve yeni bir satırı yazdıran biçimli bir yazdırma işlevidir.</span><span class="sxs-lookup"><span data-stu-id="31940-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="31940-132">Kodunuzu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="31940-132">Running your code</span></span>

<span data-ttu-id="31940-133">Kodu çalıştırabilir ve **Ctrl**+**F5**tuşlarına basarak sonuçları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31940-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="31940-134">Bu, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="31940-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="31940-135">Alternatif olarak, Visual Studio 'da **hata ayıklama** üst düzey menü öğesini seçebilir ve **hata ayıklama olmadan Başlat**' ı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31940-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="31940-136">Artık, Visual Studio 'nun bir sonraki konsol penceresinde yazdırılmış olduğunu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="31940-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="31940-137">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="31940-137">Congratulations!</span></span>  <span data-ttu-id="31940-138">Visual Studio 'da ilk F# projenizi oluşturdunuz, bu işlevi çağıran sonuçları yazdırılmış F# bir işlev yazdı ve bazı sonuçları görmek için projeyi çalıştırdık.</span><span class="sxs-lookup"><span data-stu-id="31940-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="31940-139">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="31940-139">Next steps</span></span>

<span data-ttu-id="31940-140">Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="31940-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="31940-141">Size bazı özelliklerine F#ilişkin bir genel bakış sunar ve Visual Studio 'ya kopyalayabilir ve çalıştırmak için örnek kod örnekleri sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="31940-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="31940-142">Ayrıca belgeler F# [ F# giriş sayfasında](../index.yml)belgeler hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31940-142">You can also learn more about the F# documentation in the [F# docs homepage](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="31940-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31940-143">See also</span></span>

- [<span data-ttu-id="31940-144">F# Turu</span><span class="sxs-lookup"><span data-stu-id="31940-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="31940-145">F#dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="31940-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="31940-146">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="31940-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="31940-147">Sembol ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="31940-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
