---
title: Kullanmaya başlama F# Mac için Visual Studio
description: Nasıl kullanacağınızı öğrenin F# Mac için Visual Studio ile
ms.date: 07/03/2018
ms.openlocfilehash: e37600b2ca8f845ec1068a55ff1f9964d2527742
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604177"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="edc12-103">Kullanmaya başlama F# Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="edc12-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="edc12-104">F#ve görsel F# Mac IDE için Visual Studio Araçları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="edc12-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="edc12-105">Sahip olduğunuzdan emin olun [yüklü Mac için Visual Studio](install-fsharp.md#install-f-with-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="edc12-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="edc12-106">Bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="edc12-106">Creating a console application</span></span>

<span data-ttu-id="edc12-107">Mac için Visual Studio'daki en temel projelerden birine bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="edc12-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="edc12-108">Nasıl yapılacağı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="edc12-108">Here's how to do it.</span></span>  <span data-ttu-id="edc12-109">Mac için Visual Studio açık olduğunda:</span><span class="sxs-lookup"><span data-stu-id="edc12-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="edc12-110">Üzerinde **dosya** menüsünde **yeni çözüm**.</span><span class="sxs-lookup"><span data-stu-id="edc12-110">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="edc12-111">Yeni Proje iletişim kutusunda, konsol uygulaması için 2 farklı şablonlar vardır.</span><span class="sxs-lookup"><span data-stu-id="edc12-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="edc12-112">Bir diğer altında .NET Framework'ü hedefleyen .NET ->.</span><span class="sxs-lookup"><span data-stu-id="edc12-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="edc12-113">Diğer .NET Core altında şablonudur hedefleyen .NET Core uygulamasını ->.</span><span class="sxs-lookup"><span data-stu-id="edc12-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="edc12-114">Bu makalede amacıyla ya da şablon çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="edc12-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="edc12-115">Konsol uygulaması değiştirme C# için F# gerekirse.</span><span class="sxs-lookup"><span data-stu-id="edc12-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="edc12-116">Seçin **sonraki** ilerlemek için düğmeyi!</span><span class="sxs-lookup"><span data-stu-id="edc12-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="edc12-117">Projenize bir ad verin ve uygulama için istediğiniz seçenekleri seçin.</span><span class="sxs-lookup"><span data-stu-id="edc12-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="edc12-118">Uyarı, Önizleme bölmesi ekranın oluşturulacak dizin yapısını göstermek için seçilen seçeneklere dayalı.</span><span class="sxs-lookup"><span data-stu-id="edc12-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="edc12-119">**Oluştur**'u tıklatın.</span><span class="sxs-lookup"><span data-stu-id="edc12-119">Click **Create**.</span></span>  <span data-ttu-id="edc12-120">Görmelisiniz bir F# Çözüm Gezgini'nde proje.</span><span class="sxs-lookup"><span data-stu-id="edc12-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="edc12-121">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="edc12-121">Writing your code</span></span>

<span data-ttu-id="edc12-122">Öncelikle bazı kodlar yazarak Haydi başlayalım.</span><span class="sxs-lookup"><span data-stu-id="edc12-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="edc12-123">Emin olun `Program.fs` dosya açıksa ve sonra dosyanın içeriğini aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="edc12-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="edc12-124">Önceki kod örneğinde, bir işlev `square` adlı girdi aldığı tanımlanan `x` ve kendisi tarafından çarpar.</span><span class="sxs-lookup"><span data-stu-id="edc12-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="edc12-125">Çünkü F# kullanan [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="edc12-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="edc12-126">F# Derleyici çarpma olduğu geçerli türlerinin bilincindedir ve bir türe atar `x` bağlı `square` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="edc12-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="edc12-127">Üzerine gelin, `square`, aşağıdaki görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="edc12-127">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="edc12-128">İşlevin türü imza olarak bilinen budur.</span><span class="sxs-lookup"><span data-stu-id="edc12-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="edc12-129">Aşağıdaki gibi okunabilir: "Kare adlı bir tamsayı alan bir işlev, x ve bir tamsayı üretir".</span><span class="sxs-lookup"><span data-stu-id="edc12-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="edc12-130">Derleyici verdiğiniz Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak yerine kapalı türleri arasında genel kümesidir.</span><span class="sxs-lookup"><span data-stu-id="edc12-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="edc12-131">F# Çekilen derleyici `int` şu anda noktası, ancak ayarlamak tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.</span><span class="sxs-lookup"><span data-stu-id="edc12-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="edc12-132">Başka bir işlev `main`, tanımlanır ile donatılmış `EntryPoint` bildirmek için öznitelik F# program yürütmesini derleyici var. başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="edc12-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="edc12-133">Diğer ile aynı kuralı izler [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)burada komut satırı bağımsız değişkenleri için bu işlevi geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).</span><span class="sxs-lookup"><span data-stu-id="edc12-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="edc12-134">Dediğimiz Bu işlevde harcanan olan `square` işlevi bağımsız `12`.</span><span class="sxs-lookup"><span data-stu-id="edc12-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="edc12-135">F# Derleyici sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan bir işlev bir `int` ve üreten bir `int`).</span><span class="sxs-lookup"><span data-stu-id="edc12-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="edc12-136">Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen platformlarla karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve ardından sonucu ve yeni bir satır yazdırır.</span><span class="sxs-lookup"><span data-stu-id="edc12-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="edc12-137">Kodunuzu çalıştıran</span><span class="sxs-lookup"><span data-stu-id="edc12-137">Running your code</span></span>

<span data-ttu-id="edc12-138">Kodu çalıştırmak ve sonuçları tıklayarak görmek **çalıştırma** üst düzey menüsünde ve ardından **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="edc12-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="edc12-139">Bu, hata ayıklama olmadan programı çalıştırır ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="edc12-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="edc12-140">Artık Mac için Visual Studio açıldığını konsol penceresine yazdırılan aşağıdaki görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="edc12-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="edc12-141">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="edc12-141">Congratulations!</span></span>  <span data-ttu-id="edc12-142">İlk oluşturduğunuz F# yazılmış, Mac için Visual Studio projesinde bir F# işlevi, işlev ve bazı sonuçları görmek için projenizi çalıştırarak arama sonuçlarının yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="edc12-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="edc12-143">Kullanarak F# etkileşimli</span><span class="sxs-lookup"><span data-stu-id="edc12-143">Using F# Interactive</span></span>

<span data-ttu-id="edc12-144">Görselin en iyi özelliklerinden biri F# Mac için Visual Studio Araçları F# etkileşimli penceresi.</span><span class="sxs-lookup"><span data-stu-id="edc12-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="edc12-145">Kod üzerinde bir işlem burada o kod çağırabilir ve sonuçları etkileşimli olarak görmek için göndermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="edc12-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="edc12-146">Hizmeti kullanmaya başlamak için vurgulayın `square` kodunuzda tanımlanan işlev.</span><span class="sxs-lookup"><span data-stu-id="edc12-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="edc12-147">Ardından, tıklayarak **Düzenle** üst düzey menüsünde.</span><span class="sxs-lookup"><span data-stu-id="edc12-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="edc12-148">Ardından **göndermek için seçimi F# etkileşimli**.</span><span class="sxs-lookup"><span data-stu-id="edc12-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="edc12-149">Bu kodu yürütür F# etkileşimli penceresi.</span><span class="sxs-lookup"><span data-stu-id="edc12-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="edc12-150">Alternatif olarak, seçime sağ tıklayın ve seçin **göndermek için seçimi F# etkileşimli**.</span><span class="sxs-lookup"><span data-stu-id="edc12-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="edc12-151">Görmelisiniz F# da aşağıdaki etkileşimli penceresi görünür:</span><span class="sxs-lookup"><span data-stu-id="edc12-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="edc12-152">Bu aynı işlev imzası gösterir `square` işlevin üzerine gelindiğinde, daha önce gördüğünüzle işlevi.</span><span class="sxs-lookup"><span data-stu-id="edc12-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="edc12-153">Çünkü `square` artık tanımlanan F# etkileşimli işlem çağırabilirsiniz, farklı değerlere sahip:</span><span class="sxs-lookup"><span data-stu-id="edc12-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="edc12-154">Bu işlevi yürütür, sonuç yeni bir ad ile bağlar `it`, türünü ve değerini görüntüler `it`.</span><span class="sxs-lookup"><span data-stu-id="edc12-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="edc12-155">Her satırın erdirmelisiniz Not `;;`.</span><span class="sxs-lookup"><span data-stu-id="edc12-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="edc12-156">Bu, nasıl F# etkileşimli, işlev çağrısı tamamlandığında bilir.</span><span class="sxs-lookup"><span data-stu-id="edc12-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="edc12-157">Yeni işlevleri de tanımlayabilirsiniz F# etkileşimli:</span><span class="sxs-lookup"><span data-stu-id="edc12-157">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="edc12-158">Yukarıdaki yeni bir işlev tanımlar `isOdd`, hangi alır bir `int` ve tek sayı olup olmadığını görmek için denetimleri!</span><span class="sxs-lookup"><span data-stu-id="edc12-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="edc12-159">Neler farklı girişlerle döndürür görmek için bu işlevi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edc12-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="edc12-160">İşlev çağrıları içindeki işlevleri çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="edc12-160">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="edc12-161">Ayrıca [kanal İleri işleci](../language-reference/symbol-and-operator-reference/index.md) değeri iki işlevlerini işlem hattı için:</span><span class="sxs-lookup"><span data-stu-id="edc12-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="edc12-162">Sonraki öğreticilerde, kanal İleri işleci ve diğer değinilmektedir.</span><span class="sxs-lookup"><span data-stu-id="edc12-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="edc12-163">İle yapabilecekleriniz içine yalnızca bir bakışta budur F# etkileşimli.</span><span class="sxs-lookup"><span data-stu-id="edc12-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="edc12-164">Daha fazla bilgi için kullanıma [etkileşimli programlama F# ](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="edc12-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="edc12-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="edc12-165">Next steps</span></span>

<span data-ttu-id="edc12-166">Henüz yapmadıysanız, kullanıma [Turu F# ](../tour.md), bazı çekirdek özellikleri kapsayan F# dili.</span><span class="sxs-lookup"><span data-stu-id="edc12-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="edc12-167">Size bazı özelliklerine genel bir bakış sunacak F#ve Mac ve çalıştırma için Visual Studio'ya kopyalayabilirsiniz bol miktarda kod örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="edc12-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="edc12-168">Ayrıca kullanabileceğiniz bazı harika dış kaynaklar verilmiştir büyütmüş içinde [ F# Kılavuzu](../index.md).</span><span class="sxs-lookup"><span data-stu-id="edc12-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="edc12-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edc12-169">See also</span></span>

- [<span data-ttu-id="edc12-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="edc12-170">Visual F#</span></span>](../index.md)
- [<span data-ttu-id="edc12-171">F# Turu</span><span class="sxs-lookup"><span data-stu-id="edc12-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="edc12-172">F#Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="edc12-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="edc12-173">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="edc12-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="edc12-174">Simge ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="edc12-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
