---
title: 'Mac için Visual Studio F # ile çalışmaya başlama'
description: "F # ' Mac için Visual Studio nasıl kullanacağınızı öğrenin."
ms.date: 07/03/2018
ms.openlocfilehash: d2ad24ad18bb31419b39508f2cf555c82fbe2e0b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437990"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="fdda6-103">Mac için Visual Studio F # ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="fdda6-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="fdda6-104">F # ve Visual F# araçları Mac için Visual Studio IDE 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="fdda6-105">[Mac için Visual Studio yüklü](install-fsharp.md#install-f-with-visual-studio-for-mac)olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fdda6-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="fdda6-106">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdda6-106">Creating a console application</span></span>

<span data-ttu-id="fdda6-107">Mac için Visual Studio ' deki en temel projelerden biri konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="fdda6-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="fdda6-108">Bunun nasıl yapılacağı aşağıda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fdda6-108">Here's how to do it.</span></span>  <span data-ttu-id="fdda6-109">Mac için Visual Studio açıldıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="fdda6-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="fdda6-110">**Dosya** menüsünde, **yeni çözüm**' ı işaret edin.</span><span class="sxs-lookup"><span data-stu-id="fdda6-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="fdda6-111">Yeni proje iletişim kutusunda, konsol uygulaması için 2 farklı şablon vardır.</span><span class="sxs-lookup"><span data-stu-id="fdda6-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="fdda6-112">.NET Framework hedefleyen diğer > .NET altında bir tane vardır.</span><span class="sxs-lookup"><span data-stu-id="fdda6-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="fdda6-113">Diğer şablon, .NET Core ' u hedefleyen .NET Core-> uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="fdda6-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="fdda6-114">Her iki şablon da bu makalenin amacına göre çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdda6-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="fdda6-115">Konsol uygulaması altında, gerekirse C# ' ı F # olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fdda6-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="fdda6-116">İleri gitmek için **İleri** düğmesini seçin!</span><span class="sxs-lookup"><span data-stu-id="fdda6-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="fdda6-117">Projenize bir ad verin ve uygulama için istediğiniz seçenekleri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="fdda6-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="fdda6-118">Ekranın yanındaki Önizleme bölmesi, seçilen seçeneklere göre oluşturulacak dizin yapısını gösterecek şekilde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="fdda6-119">**Oluştur**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fdda6-119">Click **Create**.</span></span>  <span data-ttu-id="fdda6-120">Artık Çözüm Gezgini bir F # projesi görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="fdda6-121">Kodunuzu yazma</span><span class="sxs-lookup"><span data-stu-id="fdda6-121">Writing your code</span></span>

<span data-ttu-id="fdda6-122">Önce bazı kodları yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="fdda6-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="fdda6-123">Dosyanın açık olduğundan emin olun `Program.fs` ve ardından içeriğini aşağıdakiler ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fdda6-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="fdda6-124">Önceki kod örneğinde, `square` adlı bir girişi alan `x` ve kendisiyle çarpar bir işlev tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="fdda6-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="fdda6-125">F # [tür çıkarımı](../language-reference/type-inference.md)kullandığından, türünün `x` belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fdda6-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="fdda6-126">F # derleyicisi, çarpma 'nın geçerli olduğu türleri anlamıştır ve `x` nasıl çağrıldığını temel alarak bir tür atar `square` .</span><span class="sxs-lookup"><span data-stu-id="fdda6-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="fdda6-127">Üzerine geldiğinizde `square` , aşağıdakileri görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="fdda6-127">If you hover over `square`, you should see the following:</span></span>

```console
val square: x:int -> int
```

<span data-ttu-id="fdda6-128">İşlevin tür imzası olarak bilinen budur.</span><span class="sxs-lookup"><span data-stu-id="fdda6-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="fdda6-129">Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir".</span><span class="sxs-lookup"><span data-stu-id="fdda6-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="fdda6-130">Derleyicinin `square` `int` Şu an için türü vermiştir. bunun nedeni, çarpma 'nın *Tüm* türler genelinde genel olmaması, ancak kapalı bir tür kümesi genelinde genel olması.</span><span class="sxs-lookup"><span data-stu-id="fdda6-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="fdda6-131">F # derleyicisi `int` Bu noktada çekildi, ancak gibi farklı bir giriş türüyle çağırırsanız tür imzasını ayarlar `square` `float` .</span><span class="sxs-lookup"><span data-stu-id="fdda6-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="fdda6-132">Diğer bir işlev olan, `main` `EntryPoint` F # derleyicisine program yürütmenin bu şekilde başlaması gerektiğini bildirmek için özniteliğiyle donatılmış tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="fdda6-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="fdda6-133">Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler `0` .</span><span class="sxs-lookup"><span data-stu-id="fdda6-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="fdda6-134">`square`İşlevi bir bağımsız değişkeniyle çağırdığımız bu işlevde `12` .</span><span class="sxs-lookup"><span data-stu-id="fdda6-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="fdda6-135">F # derleyicisi daha sonra türü `square` `int -> int` (diğer bir deyişle, ' ı alan ve üreten bir işlev) olarak atar `int` `int` .</span><span class="sxs-lookup"><span data-stu-id="fdda6-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="fdda6-136">' A çağrısı, `printfn` C stili programlama dilleri, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler, ancak sonucu ve yeni bir satırı yazdıran biçim dizesi kullanan biçimli bir yazdırma işlevidir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="fdda6-137">Kodunuzu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="fdda6-137">Running your code</span></span>

<span data-ttu-id="fdda6-138">Kodu çalıştırabilir ve en üst düzey menüsünde **Çalıştır** ' a tıklayıp **hata ayıklama olmadan başlatabilirsiniz**.</span><span class="sxs-lookup"><span data-stu-id="fdda6-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="fdda6-139">Bu işlem, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdda6-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="fdda6-140">Şimdi, Mac için Visual Studio oluşan konsol penceresinde yazdırılmış olan aşağıdakileri görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="fdda6-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="fdda6-141">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="fdda6-141">Congratulations!</span></span>  <span data-ttu-id="fdda6-142">İlk F # projenizi Mac için Visual Studio oluşturdunuz, bir F # işlevi bu işlevi çağırma sonuçlarını yazdırıldı ve bazı sonuçları görmek için projeyi çalıştırmadınız.</span><span class="sxs-lookup"><span data-stu-id="fdda6-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="fdda6-143">F# Etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="fdda6-143">Using F# Interactive</span></span>

<span data-ttu-id="fdda6-144">Mac için Visual Studio araç Visual F# araçlarının en iyi özelliklerinden biri F# Etkileşimli penceresidir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="fdda6-145">Bu kodu çağırabileceğiniz ve sonucu etkileşimli olarak görebileceğiniz bir işleme kod göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdda6-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="fdda6-146">Kullanmaya başlamak için `square` kodunuzda tanımlanan işlevi vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="fdda6-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="fdda6-147">Sonra, üst düzey menüsünden **Düzenle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fdda6-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="fdda6-148">Sonra **seçimi F# Etkileşimli gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="fdda6-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="fdda6-149">Bu, kodu F# Etkileşimli penceresinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="fdda6-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="fdda6-150">Alternatif olarak, seçime sağ tıklayıp **F# Etkileşimli seçim gönder**' i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdda6-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="fdda6-151">F# Etkileşimli penceresinin içinde aşağıdaki gibi göründüğünü görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="fdda6-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```console
>

val square : x:int -> int

>
```

<span data-ttu-id="fdda6-152">Bu, işlevin `square` üzerine gelindiğinde daha önce gördüğünüz işlev için aynı işlev imzasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="fdda6-153">`square`Artık F# Etkileşimli işleminde tanımlandığından, farklı değerlerle çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fdda6-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="fdda6-154">Bu, işlevi yürütür, sonucu yeni bir ada bağlar `it` ve türünü ve değerini görüntüler `it` .</span><span class="sxs-lookup"><span data-stu-id="fdda6-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="fdda6-155">Her satırı ile birlikte sonlandırabilmeniz gerektiğini unutmayın `;;` .</span><span class="sxs-lookup"><span data-stu-id="fdda6-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="fdda6-156">Bu, işlev çağrın ne zaman tamamlandığını F# Etkileşimli bilir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="fdda6-157">Ayrıca, F# Etkileşimli yeni işlevler de tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fdda6-157">You can also define new functions in F# Interactive:</span></span>

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="fdda6-158">Yukarıdaki yeni bir işlevi tanımlar, `isOdd` `int` ve tek bir olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="fdda6-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="fdda6-159">Bu işlevi, farklı girişlerle ne döndürdüğünü görmek için çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdda6-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="fdda6-160">İşlev çağrılarının içindeki işlevleri çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fdda6-160">You can call functions within function calls:</span></span>

```console
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="fdda6-161">Ayrıca, değeri iki işlev için ardışık düzen için [Kanal-iletme işlecini](../language-reference/symbol-and-operator-reference/index.md) de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fdda6-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="fdda6-162">Kanal iletme operatörü ve daha fazlası sonraki öğreticilerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="fdda6-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="fdda6-163">Bu, F# Etkileşimli ile yapabileceklerinize yalnızca bir göz alabilir.</span><span class="sxs-lookup"><span data-stu-id="fdda6-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="fdda6-164">Daha fazla bilgi edinmek için, [F # Ile etkileşimli programlamaya](../tools/fsharp-interactive/index.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="fdda6-164">To learn more, check out [Interactive Programming with F#](../tools/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fdda6-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="fdda6-165">Next steps</span></span>

<span data-ttu-id="fdda6-166">Henüz yapmadıysanız, f # dilinin bazı temel özelliklerini kapsayan [f # turuna](../tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="fdda6-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="fdda6-167">Bu, F # ' ın bazı özelliklerine ilişkin bir genel bakış sağlar ve Mac için Visual Studio kopyalayabilir ve çalıştırmak için örnek kod örnekleri sunar.</span><span class="sxs-lookup"><span data-stu-id="fdda6-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="fdda6-168">Ayrıca, [F # kılavuzunda](../index.yml)kullanabileceğiniz bazı harika dış kaynaklar da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="fdda6-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdda6-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdda6-169">See also</span></span>

- [<span data-ttu-id="fdda6-170">F# kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fdda6-170">F# guide</span></span>](../index.yml)
- [<span data-ttu-id="fdda6-171">F# Turu</span><span class="sxs-lookup"><span data-stu-id="fdda6-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="fdda6-172">F# dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="fdda6-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="fdda6-173">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="fdda6-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="fdda6-174">Sembol ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="fdda6-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
