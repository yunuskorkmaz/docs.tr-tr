---
title: 'F # Visual Studio için Mac kullanmaya başlama'
description: 'F # Visual Studio ile Mac için nasıl kullanacağınızı öğrenin'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 232235952ec43f682dc21de4ef7dde9c1b553364
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="d0351-103">F # Visual Studio için Mac kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d0351-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="d0351-104">F # ve Visual F # Araçları Visual Studio'da Mac IDE için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d0351-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span>  <span data-ttu-id="d0351-105">Başlamak için aşağıdakileri yapmalısınız [Mac için Visual Studio indirme](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), henüz yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="d0351-105">To begin, you should [download Visual Studio for Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="d0351-106">Bu makalede, Mac için Visual Studio Community 2017 kullanır, ancak F # tercih ettiğiniz sürümüyle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0351-106">This article uses the Visual Studio Community 2017 for Mac, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="d0351-107">F # yükleme</span><span class="sxs-lookup"><span data-stu-id="d0351-107">Installing F#</span></span> #

<span data-ttu-id="d0351-108">Mac için Visual Studio indirdikten sonra yüklemek istediğiniz seçmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="d0351-108">After downloading Visual Studio for Mac, it will prompt you to choose what you want to install.</span></span>  <span data-ttu-id="d0351-109">Bu makalede amaçları doğrultusunda biz Varsayılanları bırakarak.</span><span class="sxs-lookup"><span data-stu-id="d0351-109">For the purposes of this article we will be leaving the defaults.</span></span>  <span data-ttu-id="d0351-110">Windows için Visual Studio aksine, özellikle F # desteği yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d0351-110">In contrast to Visual Studio for Windows, you do not need to specifically install F# support.</span></span>  <span data-ttu-id="d0351-111">Devam etmek için "Yükle" tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d0351-111">Press "Install" to proceed.</span></span>

<span data-ttu-id="d0351-112">Yükleme tamamlandıktan sonra "Visual Studio Başlat" ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0351-112">After the install completes, choose "Start Visual Studio".</span></span>  <span data-ttu-id="d0351-113">Ayrıca, Bulucu üzerinde macOS başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0351-113">You can also launch it through Finder on macOS.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="d0351-114">Bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0351-114">Creating a console application</span></span>

<span data-ttu-id="d0351-115">Mac için Visual Studio en temel projeler konsol uygulaması biridir.</span><span class="sxs-lookup"><span data-stu-id="d0351-115">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="d0351-116">Bunun nasıl yapılacağı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0351-116">Here's how to do it.</span></span>  <span data-ttu-id="d0351-117">Mac için Visual Studio açıldıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="d0351-117">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="d0351-118">Üzerinde **dosya** menüsündeki **yeni çözüm**.</span><span class="sxs-lookup"><span data-stu-id="d0351-118">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="d0351-119">Yeni Proje iletişim kutusunda, konsol uygulaması için 2 farklı şablonlar vardır.</span><span class="sxs-lookup"><span data-stu-id="d0351-119">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="d0351-120">Bir diğer altında olduğundan, .NET Framework hedefler .NET ->.</span><span class="sxs-lookup"><span data-stu-id="d0351-120">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="d0351-121">Diğer .NET Core altında şablonudur .NET Core hedefler uygulamasını ->.</span><span class="sxs-lookup"><span data-stu-id="d0351-121">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="d0351-122">Bu makalede amacıyla ya da şablon çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0351-122">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="d0351-123">Konsol uygulaması altında C# F # için gerekiyorsa değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d0351-123">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="d0351-124">Seçin **sonraki** ilerlemek için düğmesini!</span><span class="sxs-lookup"><span data-stu-id="d0351-124">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="d0351-125">Projenizi adlandırın ve uygulama için istediğiniz seçenekleri seçin.</span><span class="sxs-lookup"><span data-stu-id="d0351-125">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="d0351-126">Bildirim, oluşturulacak dizin yapısını gösteren ekran tarafına önizleme bölmesinde seçilen seçeneklere dayalı.</span><span class="sxs-lookup"><span data-stu-id="d0351-126">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="d0351-127">**Oluştur**'u tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d0351-127">Click **Create**.</span></span>  <span data-ttu-id="d0351-128">F # projesinde Solution Explorer'da görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d0351-128">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="d0351-129">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="d0351-129">Writing your code</span></span>

<span data-ttu-id="d0351-130">İlk olarak bazı kodlar yazarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="d0351-130">Let's get started by writing some code first.</span></span>  <span data-ttu-id="d0351-131">Olduğundan emin olun `Program.fs` dosya açın ve ardından içeriğini aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d0351-131">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="d0351-132">Önceki kod örneğinde, bir işlev `square` adlı bir girdi aldığı tanımlanmış `x` ve hizmeti kendi başına çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="d0351-132">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="d0351-133">F # kullandığından [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d0351-133">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="d0351-134">F # derleyici çarpma olduğu geçerli türleri anlar ve bir türe atayacaktır `x` hakkında temel `square` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d0351-134">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="d0351-135">Üzerine getirirseniz `square`, aşağıdaki görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="d0351-135">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="d0351-136">Bu ne işlev türü imza olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="d0351-136">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="d0351-137">Bunu şu şekilde okunabilir: "kare adlı bir tamsayı alan bir işlevi olduğunu x ve tamsayı üretir".</span><span class="sxs-lookup"><span data-stu-id="d0351-137">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="d0351-138">Derleyici vermiş Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak bunun yerine kapalı türleri arasında genel kümesidir.</span><span class="sxs-lookup"><span data-stu-id="d0351-138">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="d0351-139">F # derleyici çekilen `int` şu anda noktası, ancak Ayarla tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.</span><span class="sxs-lookup"><span data-stu-id="d0351-139">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="d0351-140">Başka bir işlev `main`, tanımlanan ile donatılmış `EntryPoint` Bu program yürütme F # derleyici bildirmek için özniteliği yok başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0351-140">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="d0351-141">Aynısına diğer izleyen [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), burada komut satırı bağımsız değişkenleri bu işleve geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).</span><span class="sxs-lookup"><span data-stu-id="d0351-141">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="d0351-142">Diyoruz Bu işlevde olduğu `square` işlevi bağımsız değişkeninin ile `12`.</span><span class="sxs-lookup"><span data-stu-id="d0351-142">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="d0351-143">F # derleyici sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan işlevi bir `int` ve üreten bir `int`).</span><span class="sxs-lookup"><span data-stu-id="d0351-143">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="d0351-144">Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve sonuç ve yeni bir satır yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0351-144">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="d0351-145">Kodunuzu çalıştırmaya</span><span class="sxs-lookup"><span data-stu-id="d0351-145">Running your code</span></span>

<span data-ttu-id="d0351-146">Kodu çalıştırmak ve sonuçları tıklayarak görmek **çalıştırmak** en üst düzey menüsünde ve ardından **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="d0351-146">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="d0351-147">Bu program hata ayıklama olmadan çalıştırma ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0351-147">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="d0351-148">Mac için Visual Studio Sil'i yukarı konsol penceresine yazdırılan aşağıdaki görmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="d0351-148">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="d0351-149">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="d0351-149">Congratulations!</span></span>  <span data-ttu-id="d0351-150">İlk F # projenizi Visual Studio'da Mac için oluşturulan, bu işlev çağırma sonuçları bir F # işlevi yazdırılan yazılır ve bazı sonuçları görmek için projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d0351-150">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="d0351-151">F # Etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="d0351-151">Using F# Interactive</span></span>

<span data-ttu-id="d0351-152">En iyi özelliklerini Visual F Mac için Visual Studio Araçları # F # Etkileşimli pencere biridir.</span><span class="sxs-lookup"><span data-stu-id="d0351-152">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="d0351-153">Burada bu kodu çağırın ve sonuçları etkileşimli olarak görmek bir işlem kodu üzerinden göndermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0351-153">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="d0351-154">Kullanmaya başlamak için vurgulayın `square` kodunuzda tanımlanan işlevi.</span><span class="sxs-lookup"><span data-stu-id="d0351-154">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="d0351-155">Ardından, tıklayın **Düzenle** en üst düzey menüsünden.</span><span class="sxs-lookup"><span data-stu-id="d0351-155">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="d0351-156">Ardından **seçimi F # Etkileşimli için Gönder getirin**.</span><span class="sxs-lookup"><span data-stu-id="d0351-156">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="d0351-157">Bu kod F # Etkileşimli penceresinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="d0351-157">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="d0351-158">Alternatif olarak, seçime sağ tıklatın ve seçin **seçimi F # Etkileşimli için Gönder getirin**.</span><span class="sxs-lookup"><span data-stu-id="d0351-158">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="d0351-159">F # Etkileşimli aşağıdakileri görünür penceresini görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="d0351-159">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="d0351-160">Bu aynı işlev imzası gösterir `square` işlevi üzerine getirildiği oluşturduğunuzda, daha önce gördüğünüzle işlevi.</span><span class="sxs-lookup"><span data-stu-id="d0351-160">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="d0351-161">Çünkü `square` olduğundan F # Etkileşimli işlemde tanımlanan şimdi farklı değerlerle çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0351-161">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="d0351-162">Bu işlev çalıştırır, yeni bir ad sonucu bağlar `it`, türünü ve değerini görüntüler `it`.</span><span class="sxs-lookup"><span data-stu-id="d0351-162">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="d0351-163">Her satırın bitmesi Not `;;`.</span><span class="sxs-lookup"><span data-stu-id="d0351-163">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="d0351-164">Nasıl F # Etkileşimli işlev çağrısı bittiği bilir budur.</span><span class="sxs-lookup"><span data-stu-id="d0351-164">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="d0351-165">F # Etkileşimli'de yeni işlevler de tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0351-165">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="d0351-166">Yukarıdaki yeni bir işlev tanımlayan `isOdd`, hangi alır bir `int` ve tek olup olmadığını görmek için denetimleri!</span><span class="sxs-lookup"><span data-stu-id="d0351-166">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="d0351-167">Neler farklı girişle döndürür görmek için bu işlevi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0351-167">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="d0351-168">İşlev çağrıları işlevlerinde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0351-168">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="d0351-169">De kullanabilirsiniz [kanal İleri işleci](../language-reference/symbol-and-operator-reference/index.md) değeri iki işlevlerini kanalı için:</span><span class="sxs-lookup"><span data-stu-id="d0351-169">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="d0351-170">Kanal İleri işleci ve daha fazlası sonraki öğreticilerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0351-170">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="d0351-171">F # Etkileşimli ile neler yapabileceğinizi içine yalnızca bir bakışta budur.</span><span class="sxs-lookup"><span data-stu-id="d0351-171">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="d0351-172">Daha fazla bilgi için kullanıma [etkileşimli programlama F # ile](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0351-172">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d0351-173">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d0351-173">Next steps</span></span>

<span data-ttu-id="d0351-174">Henüz yapmadıysanız, kullanıma [Tur, F #](../tour.md), hangi kapsayan F # dilinin temel özelliklerden bazıları.</span><span class="sxs-lookup"><span data-stu-id="d0351-174">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="d0351-175">Bunu genel bir bakış bazı F # özelliklerini verin ve Mac için Visual Studio'ya kopyalayıp çalıştırabilirsiniz geniş kod örnekleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d0351-175">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="d0351-176">Ayrıca kullanabileceğiniz bazı harika dış kaynaklara vardır, showcased [F # Kılavuzu](../index.md).</span><span class="sxs-lookup"><span data-stu-id="d0351-176">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0351-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0351-177">See also</span></span>
 [<span data-ttu-id="d0351-178">Visual F#</span><span class="sxs-lookup"><span data-stu-id="d0351-178">Visual F#</span></span>](../index.md)  
 [<span data-ttu-id="d0351-179">F# Turu</span><span class="sxs-lookup"><span data-stu-id="d0351-179">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="d0351-180">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="d0351-180">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="d0351-181">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="d0351-181">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="d0351-182">Simge ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="d0351-182">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
