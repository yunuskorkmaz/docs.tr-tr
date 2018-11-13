---
title: Visual Studio'da F# ile çalışmaya başlama
description: F# ile Visual Studio kullanmayı öğrenin.
ms.date: 07/03/2018
ms.openlocfilehash: 3dac8466501338873aeb308ceac9274a7934a8a9
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43872857"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="73c69-103">Visual Studio'da F# ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="73c69-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="73c69-104">F# ve Visual F# Araçları, Visual Studio IDE içinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="73c69-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="73c69-105">Başlamak için sahip olduğunuzdan emin olun [yüklü F# ile Visual Studio](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="73c69-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="73c69-106">Bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="73c69-106">Creating a console application</span></span>

<span data-ttu-id="73c69-107">Visual Studio'da en temel projelerden birine bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="73c69-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="73c69-108">Nasıl yapılacağı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="73c69-108">Here's how to do it.</span></span>  <span data-ttu-id="73c69-109">Visual Studio'yu açtıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="73c69-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="73c69-110">Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="73c69-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="73c69-111">Yeni iletişim kutusunda, altında proje **şablonları**, görmelisiniz **Visual F#**.</span><span class="sxs-lookup"><span data-stu-id="73c69-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="73c69-112">F# şablonları göstermek için bunu seçin.</span><span class="sxs-lookup"><span data-stu-id="73c69-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="73c69-113">Şunlardan birini seçin **.NET Core konsol uygulaması** veya **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="73c69-113">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="73c69-114">Seçin **Tamam** F# projesi oluşturmak için!</span><span class="sxs-lookup"><span data-stu-id="73c69-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="73c69-115">Çözüm Gezgini'nde bir F# projesi görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="73c69-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="73c69-116">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="73c69-116">Writing your code</span></span>

<span data-ttu-id="73c69-117">Öncelikle bazı kodlar yazarak Haydi başlayalım.</span><span class="sxs-lookup"><span data-stu-id="73c69-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="73c69-118">Emin olun `Program.fs` dosya açıksa ve sonra dosyanın içeriğini aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="73c69-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="73c69-119">Önceki kod örneğinde, bir işlev `square` adlı girdi aldığı tanımlanan `x` ve kendisi tarafından çarpar.</span><span class="sxs-lookup"><span data-stu-id="73c69-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="73c69-120">F# kullandığından [tür çıkarımı](../language-reference/type-inference.md), türü `x` belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="73c69-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="73c69-121">F# derleyicisi çarpma olduğu geçerli türlerinin bilincindedir ve bir türe atar `x` bağlı `square` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="73c69-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="73c69-122">Üzerine gelin, `square`, aşağıdaki görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="73c69-122">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="73c69-123">İşlevin türü imza olarak bilinen budur.</span><span class="sxs-lookup"><span data-stu-id="73c69-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="73c69-124">Bunu aşağıdaki gibi okunabilir: "kare adlı bir tamsayı alan bir işlev, x ve bir tamsayı üretir".</span><span class="sxs-lookup"><span data-stu-id="73c69-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="73c69-125">Derleyici verdiğiniz Not `square` `int` türü çarpma arasında genel olmadığından budur şimdilik - *tüm* türleri, ancak yerine kapalı türleri arasında genel kümesidir.</span><span class="sxs-lookup"><span data-stu-id="73c69-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="73c69-126">F# derleyicisi çekilen `int` şu anda noktası, ancak ayarlamak tür imzası çağırırsanız `square` farklı bir giriş türü gibi bir `float`.</span><span class="sxs-lookup"><span data-stu-id="73c69-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="73c69-127">Başka bir işlev `main`, tanımlanır ile donatılmış `EntryPoint` F# derleyicisi, program yürütme bildirmek için özniteliği var. başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="73c69-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="73c69-128">Diğer ile aynı kuralı izler [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)burada komut satırı bağımsız değişkenleri için bu işlevi geçirilebilir ve bir tamsayı kodu döndürdü (genellikle `0`).</span><span class="sxs-lookup"><span data-stu-id="73c69-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="73c69-129">Dediğimiz Bu işlevde harcanan olan `square` işlevi bağımsız `12`.</span><span class="sxs-lookup"><span data-stu-id="73c69-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="73c69-130">F# derleyicisi sonra türünü atar `square` olmasını `int -> int` (diğer bir deyişle, alan bir işlev bir `int` ve üreten bir `int`).</span><span class="sxs-lookup"><span data-stu-id="73c69-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="73c69-131">Çağrı `printfn` C stili programlama dilleri, Biçim dizesinde belirtilen platformlarla karşılık gelen parametreleri için benzer bir biçim dizesi kullanan biçimlendirilmiş bir yazdırma işlevi ve ardından sonucu ve yeni bir satır yazdırır.</span><span class="sxs-lookup"><span data-stu-id="73c69-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="73c69-132">Kodunuzu çalıştıran</span><span class="sxs-lookup"><span data-stu-id="73c69-132">Running your code</span></span>

<span data-ttu-id="73c69-133">Kodu çalıştırmak ve sonuçları tuşlarına basarak görmek **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="73c69-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="73c69-134">Bu, hata ayıklama olmadan programı çalıştırır ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="73c69-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="73c69-135">Alternatif olarak, seçebileceğiniz **hata ayıklama** üst düzey menü öğesi Visual Studio'da ve seçin **hata ayıklama olmadan Başlat**.</span><span class="sxs-lookup"><span data-stu-id="73c69-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="73c69-136">Şimdi Visual Studio açıldığını konsol penceresine yazdırılan aşağıdaki görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="73c69-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="73c69-137">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="73c69-137">Congratulations!</span></span>  <span data-ttu-id="73c69-138">İlk F# projenizi Visual Studio'da oluşturulan, F# işlevi, işlev çağırma sonuçları yazdırılan yazılan ve bazı sonuçları görmek için projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73c69-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="73c69-139">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="73c69-139">Next steps</span></span>

<span data-ttu-id="73c69-140">Henüz yapmadıysanız, kullanıma [turu, F#](../tour.md), F# dilinin temel özelliklerinden bazıları kapsayan.</span><span class="sxs-lookup"><span data-stu-id="73c69-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="73c69-141">Bazı F# özelliklerine genel bir bakış sunar ve Visual Studio'ya kopyalayıp çalıştırabilirsiniz bol miktarda kod örnekleri sağlamak.</span><span class="sxs-lookup"><span data-stu-id="73c69-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="73c69-142">Ayrıca kullanabileceğiniz bazı harika dış kaynaklar verilmiştir büyütmüş içinde [F# Kılavuzu](../index.md).</span><span class="sxs-lookup"><span data-stu-id="73c69-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73c69-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73c69-143">See also</span></span>

- [<span data-ttu-id="73c69-144">F# Turu</span><span class="sxs-lookup"><span data-stu-id="73c69-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="73c69-145">F# dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="73c69-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="73c69-146">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="73c69-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="73c69-147">Simge ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="73c69-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
