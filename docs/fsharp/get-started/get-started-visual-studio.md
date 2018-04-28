---
title: 'F # Visual Studio ile çalışmaya başlama'
description: 'F # Visual Studio ile nasıl kullanacağınızı öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 29e24f755e6d97c4b31c0d01b254bf90cf77bf17
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="ce98e-103">F # Visual Studio ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="ce98e-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="ce98e-104">F # ve Visual F # Araçları Visual Studio IDE içinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ce98e-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="ce98e-105">Başlamak için aşağıdakileri yapmalısınız [Visual Studio indirme](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), henüz yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="ce98e-105">To begin, you should [download Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="ce98e-106">Bu makalede Visual Studio 2017 Community Edition kullanır, ancak F # tercih ettiğiniz sürümüyle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce98e-106">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="ce98e-107">F # yükleme</span><span class="sxs-lookup"><span data-stu-id="ce98e-107">Installing F#</span></span> #

<span data-ttu-id="ce98e-108">İlk olarak Visual Studio indirme değilse, önce Visual Studio yükleyicisi yükler.</span><span class="sxs-lookup"><span data-stu-id="ce98e-108">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="ce98e-109">Visual Studio 2017 herhangi bir sürümünü Yükleyiciden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="ce98e-109">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="ce98e-110">Yüklü zaten varsa tıklatın **Değiştir**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-110">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="ce98e-111">Sonraki iş yüklerinin bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ce98e-111">You'll next see a list of Workloads.</span></span> <span data-ttu-id="ce98e-112">F # aşağıdaki iş yüklerini kanalıyla yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ce98e-112">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="ce98e-113">İş yükü</span><span class="sxs-lookup"><span data-stu-id="ce98e-113">Workload</span></span>|<span data-ttu-id="ce98e-114">Eylem</span><span class="sxs-lookup"><span data-stu-id="ce98e-114">Action</span></span>|
|--------|------|
| <span data-ttu-id="ce98e-115">.NET core platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="ce98e-115">.NET Core cross-platform development</span></span> | <span data-ttu-id="ce98e-116">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="ce98e-116">No action - F# is installed by default</span></span> |
| <span data-ttu-id="ce98e-117">ASP.NET ve web geliştirme</span><span class="sxs-lookup"><span data-stu-id="ce98e-117">ASP.NET and web development</span></span> | <span data-ttu-id="ce98e-118">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="ce98e-118">No action - F# is installed by default</span></span> |
| <span data-ttu-id="ce98e-119">Azure geliştirme</span><span class="sxs-lookup"><span data-stu-id="ce98e-119">Azure development</span></span> | <span data-ttu-id="ce98e-120">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="ce98e-120">No action - F# is installed by default</span></span> |
| <span data-ttu-id="ce98e-121">.NET ile Mobil Geliştirme</span><span class="sxs-lookup"><span data-stu-id="ce98e-121">Mobile development with .NET</span></span> | <span data-ttu-id="ce98e-122">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="ce98e-122">No action - F# is installed by default</span></span> |
| <span data-ttu-id="ce98e-123">Veri bilimi ve analitik uygulamalar</span><span class="sxs-lookup"><span data-stu-id="ce98e-123">Data science and analytical applications</span></span> | <span data-ttu-id="ce98e-124">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="ce98e-124">No action - F# is installed by default</span></span> |
| <span data-ttu-id="ce98e-125">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="ce98e-125">.NET desktop development</span></span> | <span data-ttu-id="ce98e-126">Seçin **F # Masaüstü dil desteği** sağ taraftaki</span><span class="sxs-lookup"><span data-stu-id="ce98e-126">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="ce98e-127">Veri depolama ve işleme</span><span class="sxs-lookup"><span data-stu-id="ce98e-127">Data storage and processing</span></span> | <span data-ttu-id="ce98e-128">Seçin **F # Masaüstü dil desteği** sağ taraftaki</span><span class="sxs-lookup"><span data-stu-id="ce98e-128">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="ce98e-129">Bundan sonra öğesini **Değiştir** alt sağ tarafındaki.</span><span class="sxs-lookup"><span data-stu-id="ce98e-129">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="ce98e-130">Bu, seçtiğiniz her şeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="ce98e-130">This will install everything you have selected.</span></span>  <span data-ttu-id="ce98e-131">Tıklayarak Visual Studio 2017 F # dili desteği ile sonra açabilirsiniz **başlatma**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-131">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="ce98e-132">Bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce98e-132">Creating a console application</span></span>

<span data-ttu-id="ce98e-133">Visual Studio'da en temel projeler konsol uygulaması biridir.</span><span class="sxs-lookup"><span data-stu-id="ce98e-133">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="ce98e-134">Bunun nasıl yapılacağı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce98e-134">Here's how to do it.</span></span>  <span data-ttu-id="ce98e-135">Visual Studio açıldıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="ce98e-135">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="ce98e-136">Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-136">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="ce98e-137">Yeni Proje iletişim kutusunda, altında **şablonları**, görmeniz gerekir **Visual F #**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-137">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="ce98e-138">F # şablonları göstermek için bunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ce98e-138">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="ce98e-139">Şunlardan birini seçin **.NET Core konsol uygulaması** veya **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-139">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="ce98e-140">Seçin **Tamam** F # projesi oluşturmak için düğmesini!</span><span class="sxs-lookup"><span data-stu-id="ce98e-140">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="ce98e-141">F # projesinde Solution Explorer'da görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ce98e-141">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="ce98e-142">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="ce98e-142">Writing your code</span></span>

<span data-ttu-id="ce98e-143">İlk olarak bazı kodlar yazarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="ce98e-143">Let's get started by writing some code first.</span></span>  <span data-ttu-id="ce98e-144">Olduğundan emin olun `Program.fs` dosya açın ve ardından içeriğini aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ce98e-144">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="ce98e-145">Önceki kod örneğinde, bir işlev `square` adlı bir girdi aldığı tanımlanmış `x` ve hizmeti kendi başına çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="ce98e-145">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="ce98e-146">F # kullandığından [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ce98e-146">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="ce98e-147">F # derleyici çarpma olduğu geçerli türleri anlar ve bir türe atayacaktır `x` hakkında temel `square` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ce98e-147">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="ce98e-148">Üzerine getirirseniz `square`, aşağıdaki görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ce98e-148">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="ce98e-149">Bu ne işlev türü imza olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="ce98e-149">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="ce98e-150">Bunu şu şekilde okunabilir: "kare adlı bir tamsayı alan bir işlevi olduğunu x ve tamsayı üretir".</span><span class="sxs-lookup"><span data-stu-id="ce98e-150">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="ce98e-151">Derleyici vermiş Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak bunun yerine kapalı türleri arasında genel kümesidir.</span><span class="sxs-lookup"><span data-stu-id="ce98e-151">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="ce98e-152">F # derleyici çekilen `int` şu anda noktası, ancak Ayarla tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.</span><span class="sxs-lookup"><span data-stu-id="ce98e-152">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="ce98e-153">Başka bir işlev `main`, tanımlanan ile donatılmış `EntryPoint` Bu program yürütme F # derleyici bildirmek için özniteliği yok başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce98e-153">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="ce98e-154">Aynısına diğer izleyen [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), burada komut satırı bağımsız değişkenleri bu işleve geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).</span><span class="sxs-lookup"><span data-stu-id="ce98e-154">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="ce98e-155">Diyoruz Bu işlevde olduğu `square` işlevi bağımsız değişkeninin ile `12`.</span><span class="sxs-lookup"><span data-stu-id="ce98e-155">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="ce98e-156">F # derleyici sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan işlevi bir `int` ve üreten bir `int`).</span><span class="sxs-lookup"><span data-stu-id="ce98e-156">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="ce98e-157">Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve sonuç ve yeni bir satır yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ce98e-157">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="ce98e-158">Kodunuzu çalıştırmaya</span><span class="sxs-lookup"><span data-stu-id="ce98e-158">Running your code</span></span>

<span data-ttu-id="ce98e-159">Kodu çalıştırmak ve sonuçları tuşlarına basarak görmek **ctrl-f5**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-159">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="ce98e-160">Bu program hata ayıklama olmadan çalıştırma ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce98e-160">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="ce98e-161">Alternatif olarak, seçebileceğiniz **hata ayıklama** en üst düzey menü öğesi Visual Studio'da ve seçin **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-161">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="ce98e-162">Visual Studio Sil'i yukarı konsol penceresine yazdırılan aşağıdaki görmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="ce98e-162">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="ce98e-163">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="ce98e-163">Congratulations!</span></span>  <span data-ttu-id="ce98e-164">Visual Studio'da ilk F # projenize oluşturulan, bu işlev çağırma sonuçları bir F # işlevi yazdırılan yazılır ve bazı sonuçları görmek için projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ce98e-164">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="ce98e-165">F # Etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="ce98e-165">Using F# Interactive</span></span>

<span data-ttu-id="ce98e-166">En iyi özelliklerini Visual F Visual Studio'da tooling # F # Etkileşimli pencere biridir.</span><span class="sxs-lookup"><span data-stu-id="ce98e-166">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="ce98e-167">Burada bu kodu çağırın ve sonuçları etkileşimli olarak görmek bir işlem kodu üzerinden göndermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce98e-167">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="ce98e-168">Kullanmaya başlamak için vurgulayın `square` kodunuzda tanımlanan işlevi.</span><span class="sxs-lookup"><span data-stu-id="ce98e-168">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="ce98e-169">Ardından, tutun **Alt** anahtar ve tuşuna **Enter**.</span><span class="sxs-lookup"><span data-stu-id="ce98e-169">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="ce98e-170">Bu kod F # Etkileşimli penceresinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="ce98e-170">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="ce98e-171">F # Etkileşimli aşağıdakileri görünür penceresini görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ce98e-171">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="ce98e-172">Bu aynı işlev imzası gösterir `square` işlevi üzerine getirildiği oluşturduğunuzda, daha önce gördüğünüzle işlevi.</span><span class="sxs-lookup"><span data-stu-id="ce98e-172">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="ce98e-173">Çünkü `square` olduğundan F # Etkileşimli işlemde tanımlanan şimdi farklı değerlerle çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ce98e-173">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="ce98e-174">Bu işlev çalıştırır, yeni bir ad sonucu bağlar `it`, türünü ve değerini görüntüler `it`.</span><span class="sxs-lookup"><span data-stu-id="ce98e-174">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="ce98e-175">Her satırın bitmesi Not `;;`.</span><span class="sxs-lookup"><span data-stu-id="ce98e-175">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="ce98e-176">Nasıl F # Etkileşimli işlev çağrısı bittiği bilir budur.</span><span class="sxs-lookup"><span data-stu-id="ce98e-176">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="ce98e-177">F # Etkileşimli'de yeni işlevler de tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ce98e-177">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="ce98e-178">Yukarıdaki yeni bir işlev tanımlayan `isOdd`, hangi alır bir `int` ve tek olup olmadığını görmek için denetimleri!</span><span class="sxs-lookup"><span data-stu-id="ce98e-178">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="ce98e-179">Neler farklı girişle döndürür görmek için bu işlevi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce98e-179">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="ce98e-180">İşlev çağrıları işlevlerinde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ce98e-180">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="ce98e-181">De kullanabilirsiniz [kanal İleri işleci](../language-reference/symbol-and-operator-reference/index.md) değeri iki işlevlerini kanalı için:</span><span class="sxs-lookup"><span data-stu-id="ce98e-181">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="ce98e-182">Kanal İleri işleci ve daha fazlası sonraki öğreticilerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce98e-182">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="ce98e-183">F # Etkileşimli ile neler yapabileceğinizi içine yalnızca bir bakışta budur.</span><span class="sxs-lookup"><span data-stu-id="ce98e-183">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="ce98e-184">Daha fazla bilgi için kullanıma [etkileşimli programlama F # ile](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce98e-184">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ce98e-185">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ce98e-185">Next steps</span></span>

<span data-ttu-id="ce98e-186">Henüz yapmadıysanız, kullanıma [Tur, F #](../tour.md), hangi kapsayan F # dilinin temel özelliklerden bazıları.</span><span class="sxs-lookup"><span data-stu-id="ce98e-186">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="ce98e-187">Bu bazı F # özelliklerini genel bakış sağlar ve Visual Studio'ya kopyalama ve çalıştırma geniş kod örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce98e-187">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="ce98e-188">Ayrıca kullanabileceğiniz bazı harika dış kaynaklara vardır, showcased [F # Kılavuzu](../index.md).</span><span class="sxs-lookup"><span data-stu-id="ce98e-188">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce98e-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce98e-189">See also</span></span>
 [<span data-ttu-id="ce98e-190">Visual F#</span><span class="sxs-lookup"><span data-stu-id="ce98e-190">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="ce98e-191">F# Turu</span><span class="sxs-lookup"><span data-stu-id="ce98e-191">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="ce98e-192">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="ce98e-192">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="ce98e-193">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="ce98e-193">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="ce98e-194">Simge ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="ce98e-194">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
