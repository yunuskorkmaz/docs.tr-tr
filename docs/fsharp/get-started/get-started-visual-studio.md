---
title: "F # Visual Studio ile çalışmaya başlama"
description: "F # Visual Studio ile nasıl kullanacağınızı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 944bbbba6a26634ace269d86cbbdde9ef9de7bcd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="26d45-104">F # Visual Studio ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="26d45-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="26d45-105">F # ve Visual F # Araçları Visual Studio IDE içinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="26d45-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="26d45-106">Başlamak için aşağıdakileri yapmalısınız [Visual Studio indirme](https://www.visualstudio.com/downloads/download-visual-studio-vs), henüz yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="26d45-106">To begin, you should [download Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs), if you haven't already.</span></span>  <span data-ttu-id="26d45-107">Bu makalede Visual Studio 2017 Community Edition kullanır, ancak F # tercih ettiğiniz sürümüyle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26d45-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="26d45-108">F # yükleme</span><span class="sxs-lookup"><span data-stu-id="26d45-108">Installing F#</span></span> #

<span data-ttu-id="26d45-109">İlk olarak Visual Studio indirme değilse, önce Visual Studio yükleyicisi yükler.</span><span class="sxs-lookup"><span data-stu-id="26d45-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="26d45-110">Visual Studio 2017 herhangi bir sürümünü Yükleyiciden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="26d45-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="26d45-111">Yüklü zaten varsa tıklatın **Değiştir**.</span><span class="sxs-lookup"><span data-stu-id="26d45-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="26d45-112">Sonraki iş yüklerinin bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="26d45-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="26d45-113">F # aşağıdaki iş yüklerini kanalıyla yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="26d45-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="26d45-114">İş yükü</span><span class="sxs-lookup"><span data-stu-id="26d45-114">Workload</span></span>|<span data-ttu-id="26d45-115">Eylem</span><span class="sxs-lookup"><span data-stu-id="26d45-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="26d45-116">.NET core platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="26d45-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="26d45-117">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="26d45-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="26d45-118">ASP.NET ve web geliştirme</span><span class="sxs-lookup"><span data-stu-id="26d45-118">ASP.NET and web development</span></span> | <span data-ttu-id="26d45-119">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="26d45-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="26d45-120">Azure geliştirme</span><span class="sxs-lookup"><span data-stu-id="26d45-120">Azure development</span></span> | <span data-ttu-id="26d45-121">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="26d45-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="26d45-122">.NET ile Mobil Geliştirme</span><span class="sxs-lookup"><span data-stu-id="26d45-122">Mobile development with .NET</span></span> | <span data-ttu-id="26d45-123">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="26d45-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="26d45-124">Veri bilimi ve analitik uygulamalar</span><span class="sxs-lookup"><span data-stu-id="26d45-124">Data science and analytical applications</span></span> | <span data-ttu-id="26d45-125">Hiçbir eylem - F # varsayılan olarak yüklenir</span><span class="sxs-lookup"><span data-stu-id="26d45-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="26d45-126">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="26d45-126">.NET desktop development</span></span> | <span data-ttu-id="26d45-127">Seçin **F # Masaüstü dil desteği** sağ taraftaki</span><span class="sxs-lookup"><span data-stu-id="26d45-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="26d45-128">Veri depolama ve işleme</span><span class="sxs-lookup"><span data-stu-id="26d45-128">Data storage and processing</span></span> | <span data-ttu-id="26d45-129">Seçin **F # Masaüstü dil desteği** sağ taraftaki</span><span class="sxs-lookup"><span data-stu-id="26d45-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="26d45-130">Bundan sonra öğesini **Değiştir** alt sağ tarafındaki.</span><span class="sxs-lookup"><span data-stu-id="26d45-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="26d45-131">Bu, seçtiğiniz her şeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="26d45-131">This will install everything you have selected.</span></span>  <span data-ttu-id="26d45-132">Tıklayarak Visual Studio 2017 F # dili desteği ile sonra açabilirsiniz **başlatma**.</span><span class="sxs-lookup"><span data-stu-id="26d45-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="26d45-133">Bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="26d45-133">Creating a console application</span></span>

<span data-ttu-id="26d45-134">Visual Studio'da en temel projeler konsol uygulaması biridir.</span><span class="sxs-lookup"><span data-stu-id="26d45-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="26d45-135">Bunun nasıl yapılacağı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="26d45-135">Here's how to do it.</span></span>  <span data-ttu-id="26d45-136">Visual Studio açıldıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="26d45-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="26d45-137">Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="26d45-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="26d45-138">Yeni Proje iletişim kutusunda, altında **şablonları**, görmeniz gerekir **Visual F #**.</span><span class="sxs-lookup"><span data-stu-id="26d45-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="26d45-139">F # şablonları göstermek için bunu seçin.</span><span class="sxs-lookup"><span data-stu-id="26d45-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="26d45-140">Şunlardan birini seçin **.NET Core konsol uygulaması** veya **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="26d45-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="26d45-141">Seçin **Tamam** F # projesi oluşturmak için düğmesini!</span><span class="sxs-lookup"><span data-stu-id="26d45-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="26d45-142">F # projesinde Solution Explorer'da görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="26d45-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="26d45-143">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="26d45-143">Writing your code</span></span>

<span data-ttu-id="26d45-144">İlk olarak bazı kodlar yazarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="26d45-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="26d45-145">Olduğundan emin olun `Program.fs` dosya açın ve ardından içeriğini aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="26d45-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="26d45-146">Önceki kod örneğinde, bir işlev `square` adlı bir girdi aldığı tanımlanmış `x` ve hizmeti kendi başına çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="26d45-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="26d45-147">F # kullandığından [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="26d45-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="26d45-148">F # derleyici çarpma olduğu geçerli türleri anlar ve bir türe atayacaktır `x` hakkında temel `square` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="26d45-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="26d45-149">Üzerine getirirseniz `square`, aşağıdaki görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="26d45-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="26d45-150">Bu ne işlev türü imza olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="26d45-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="26d45-151">Bunu şu şekilde okunabilir: "kare adlı bir tamsayı alan bir işlevi olduğunu x ve tamsayı üretir".</span><span class="sxs-lookup"><span data-stu-id="26d45-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="26d45-152">Derleyici vermiş Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak bunun yerine kapalı türleri arasında genel kümesidir.</span><span class="sxs-lookup"><span data-stu-id="26d45-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="26d45-153">F # derleyici çekilen `int` şu anda noktası, ancak Ayarla tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.</span><span class="sxs-lookup"><span data-stu-id="26d45-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="26d45-154">Başka bir işlev `main`, tanımlanan ile donatılmış `EntryPoint` Bu program yürütme F # derleyici bildirmek için özniteliği yok başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="26d45-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="26d45-155">Aynısına diğer izleyen [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), burada komut satırı bağımsız değişkenleri bu işleve geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).</span><span class="sxs-lookup"><span data-stu-id="26d45-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="26d45-156">Diyoruz Bu işlevde olduğu `square` işlevi bağımsız değişkeninin ile `12`.</span><span class="sxs-lookup"><span data-stu-id="26d45-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="26d45-157">F # derleyici sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan işlevi bir `int` ve üreten bir `int`).</span><span class="sxs-lookup"><span data-stu-id="26d45-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="26d45-158">Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve sonuç ve yeni bir satır yazdırır.</span><span class="sxs-lookup"><span data-stu-id="26d45-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="26d45-159">Kodunuzu çalıştırmaya</span><span class="sxs-lookup"><span data-stu-id="26d45-159">Running your code</span></span>

<span data-ttu-id="26d45-160">Kodu çalıştırmak ve sonuçları tuşlarına basarak görmek **ctrl-f5**.</span><span class="sxs-lookup"><span data-stu-id="26d45-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="26d45-161">Bu program hata ayıklama olmadan çalıştırma ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="26d45-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="26d45-162">Alternatif olarak, seçebileceğiniz **hata ayıklama** en üst düzey menü öğesi Visual Studio'da ve seçin **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="26d45-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="26d45-163">Visual Studio Sil'i yukarı konsol penceresine yazdırılan aşağıdaki görmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="26d45-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="26d45-164">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="26d45-164">Congratulations!</span></span>  <span data-ttu-id="26d45-165">Visual Studio'da ilk F # projenize oluşturulan, bu işlev çağırma sonuçları bir F # işlevi yazdırılan yazılır ve bazı sonuçları görmek için projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="26d45-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="26d45-166">F # Etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="26d45-166">Using F# Interactive</span></span>

<span data-ttu-id="26d45-167">En iyi özelliklerini Visual F Visual Studio'da tooling # F # Etkileşimli pencere biridir.</span><span class="sxs-lookup"><span data-stu-id="26d45-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="26d45-168">Burada bu kodu çağırın ve sonuçları etkileşimli olarak görmek bir işlem kodu üzerinden göndermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="26d45-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="26d45-169">Kullanmaya başlamak için vurgulayın `square` kodunuzda tanımlanan işlevi.</span><span class="sxs-lookup"><span data-stu-id="26d45-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="26d45-170">Ardından, tutun **Alt** anahtar ve tuşuna **Enter**.</span><span class="sxs-lookup"><span data-stu-id="26d45-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="26d45-171">Bu kod F # Etkileşimli penceresinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="26d45-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="26d45-172">F # Etkileşimli aşağıdakileri görünür penceresini görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="26d45-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="26d45-173">Bu aynı işlev imzası gösterir `square` işlevi üzerine getirildiği oluşturduğunuzda, daha önce gördüğünüzle işlevi.</span><span class="sxs-lookup"><span data-stu-id="26d45-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="26d45-174">Çünkü `square` olduğundan F # Etkileşimli işlemde tanımlanan şimdi farklı değerlerle çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="26d45-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="26d45-175">Bu işlev çalıştırır, yeni bir ad sonucu bağlar `it`, türünü ve değerini görüntüler `it`.</span><span class="sxs-lookup"><span data-stu-id="26d45-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="26d45-176">Her satırın bitmesi Not `;;`.</span><span class="sxs-lookup"><span data-stu-id="26d45-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="26d45-177">Nasıl F # Etkileşimli işlev çağrısı bittiği bilir budur.</span><span class="sxs-lookup"><span data-stu-id="26d45-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="26d45-178">F # Etkileşimli'de yeni işlevler de tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="26d45-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="26d45-179">Yukarıdaki yeni bir işlev tanımlayan `isOdd`, hangi alır bir `int` ve tek olup olmadığını görmek için denetimleri!</span><span class="sxs-lookup"><span data-stu-id="26d45-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="26d45-180">Neler farklı girişle döndürür görmek için bu işlevi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26d45-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="26d45-181">İşlev çağrıları işlevlerinde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="26d45-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="26d45-182">De kullanabilirsiniz [kanal İleri işleci](../language-reference/symbol-and-operator-reference/index.md) değeri iki işlevlerini kanalı için:</span><span class="sxs-lookup"><span data-stu-id="26d45-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="26d45-183">Kanal İleri işleci ve daha fazlası sonraki öğreticilerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="26d45-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="26d45-184">F # Etkileşimli ile neler yapabileceğinizi içine yalnızca bir bakışta budur.</span><span class="sxs-lookup"><span data-stu-id="26d45-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="26d45-185">Daha fazla bilgi için kullanıma [etkileşimli programlama F # ile](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="26d45-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="26d45-186">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="26d45-186">Next steps</span></span>

<span data-ttu-id="26d45-187">Henüz yapmadıysanız, kullanıma [Tur, F #](../tour.md), hangi kapsayan F # dilinin temel özelliklerden bazıları.</span><span class="sxs-lookup"><span data-stu-id="26d45-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="26d45-188">Bu bazı F # özelliklerini genel bakış sağlar ve Visual Studio'ya kopyalama ve çalıştırma geniş kod örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="26d45-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="26d45-189">Ayrıca kullanabileceğiniz bazı harika dış kaynaklara vardır, showcased [F # Kılavuzu](../index.md).</span><span class="sxs-lookup"><span data-stu-id="26d45-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26d45-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26d45-190">See also</span></span>
 [<span data-ttu-id="26d45-191">Visual F #</span><span class="sxs-lookup"><span data-stu-id="26d45-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="26d45-192">F # turu</span><span class="sxs-lookup"><span data-stu-id="26d45-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="26d45-193">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="26d45-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="26d45-194">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="26d45-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="26d45-195">Simge ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="26d45-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
