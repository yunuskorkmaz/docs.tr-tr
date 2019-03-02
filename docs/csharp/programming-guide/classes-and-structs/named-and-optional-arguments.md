---
title: Adlandırılmış ve isteğe bağlı bağımsız değişkenler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: d31cec602516b7cf3e4b358fa4b3f10e167e6e17
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202744"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="b8838-102">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b8838-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] <span data-ttu-id="b8838-103">adlandırılmış ve isteğe bağlı bağımsız değişkenler tanıtır.</span><span class="sxs-lookup"><span data-stu-id="b8838-103">introduces named and optional arguments.</span></span> <span data-ttu-id="b8838-104">*Adlandırılmış bağımsız değişkenler* bağımsız değişken parametre adı yerine parametre listesinde parametrenin konumu ile ilişkilendirerek belirli bir parametre için bir bağımsız değişken belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="b8838-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="b8838-105">*İsteğe bağlı bağımsız değişkenlere* bazı parametrelerin bağımsız değişkenleri atlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8838-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="b8838-106">Her iki tekniği, yöntemleri, Dizinleyicileri, Oluşturucular ve temsilciler ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8838-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="b8838-107">Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişken, parametre listesi bağımsız değişken listesinde göründükleri sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b8838-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="b8838-108">Adlandırılmış ve isteğe bağlı parametreler birlikte kullanıldığında, yalnızca birkaç parametreleri isteğe bağlı parametreler için bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8838-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="b8838-109">Bu özellik, Microsoft Office Otomasyon API'leri gibi COM arabirimleri çağrıları büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b8838-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="b8838-110">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b8838-110">Named Arguments</span></span>  
 <span data-ttu-id="b8838-111">Adlandırılmış bağımsız değişkenler unutmayın veya çağrılan yöntemlerin parametre listeleri parametrelerinde sırasını aramak için gereken gelen boş.</span><span class="sxs-lookup"><span data-stu-id="b8838-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="b8838-112">Parametresi her bağımsız değişkeni için parametre adı belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b8838-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="b8838-113">Örneğin, sipariş ayrıntılarını yazdırır bir işlev (gibi satıcı adı, sipariş numarası & ürün adı) işlev tarafından tanımlanan sırayla konuma göre bağımsız değişken göndererek standart yolla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8838-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="b8838-114">Parametreler sırası hatırlıyor musunuz, ancak adlarını bilmeniz, bağımsız değişkenler herhangi bir sırada gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8838-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="b8838-115">Adlandırılmış bağımsız değişkenler de ne her bağımsız değişken temsil eden belirleyerek kodunuzu okunabilirliğini geliştirmek.</span><span class="sxs-lookup"><span data-stu-id="b8838-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="b8838-116">Aşağıdaki örnek yöntemi içinde `sellerName` null veya boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="b8838-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="b8838-117">Her ikisi de olarak `sellerName` ve `productName` dize türleri, bağımsız değişkenleri konuma göre göndermek yerine, iki belirsizliğinin ortadan kaldırılmasını ve Karışıklığın kodu okuyan herkese adlandırılmış bağımsız değişkenler kullanan mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="b8838-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="b8838-118">Konumsal bağımsız değişkenlerle birlikte kullanıldığında adlandırılmış bağımsız değişkenler, geçerli olduğu sürece</span><span class="sxs-lookup"><span data-stu-id="b8838-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="b8838-119">hiçbir konumsal bağımsız değişkeni tarafından ardından veya</span><span class="sxs-lookup"><span data-stu-id="b8838-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="b8838-120">_C# 7.2 ile başlayan_, doğru konumda hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="b8838-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="b8838-121">Parametresi aşağıdaki örnekte `orderNum` doğru konumda olmakla birlikte açıkça adlandırılmış değil.</span><span class="sxs-lookup"><span data-stu-id="b8838-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="b8838-122">Ancak, sırası adlandırılmış bağımsız değişkenler konumsal bağımsız değişkenler ardından varsa geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="b8838-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="b8838-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8838-123">Example</span></span>  
 <span data-ttu-id="b8838-124">Aşağıdaki kod, bazı bulunmakla birlikte, bu bölümdeki örnekler uygular.</span><span class="sxs-lookup"><span data-stu-id="b8838-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="b8838-125">İsteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b8838-125">Optional Arguments</span></span>  
 <span data-ttu-id="b8838-126">Yöntemi, oluşturucu, dizin oluşturucu veya temsilci tanımı parametreleri gerekli veya isteğe bağlı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8838-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="b8838-127">Tüm çağrıların tüm gerekli parametrelerin bağımsız değişkenleri belirtmeniz gerekir, ancak isteğe bağlı parametrelerin bağımsız değişkenleri atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8838-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="b8838-128">Her isteğe bağlı parametre bir varsayılan değeri kendi tanımının bir parçası olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="b8838-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="b8838-129">Bu parametre için hiçbir bağımsız değişken gönderirse, varsayılan değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8838-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="b8838-130">Varsayılan değer ifadelerin aşağıdaki türlerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b8838-130">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="b8838-131">sabit bir ifade;</span><span class="sxs-lookup"><span data-stu-id="b8838-131">a constant expression;</span></span>  
  
-   <span data-ttu-id="b8838-132">bir ifade formun `new ValType()`burada `ValType` bir değer türü olduğu gibi bir [enum](../../../csharp/language-reference/keywords/enum.md) veya bir [yapı](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="b8838-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="b8838-133">bir ifade formun [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md)burada `ValType` bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="b8838-133">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="b8838-134">İsteğe bağlı parametreler tüm gerekli parametrelerden sonra parametre listesinin sonunda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b8838-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="b8838-135">Çağıran, isteğe bağlı parametreler izleyenler herhangi biri için bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenleri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8838-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="b8838-136">Bağımsız değişken listesini virgülle ayrılmış boşlukları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b8838-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="b8838-137">Örneğin, aşağıdaki kodda, yöntem örnek `ExampleMethod` bir gerekli ve isteğe bağlı parametrelerden ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b8838-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="b8838-138">Aşağıdaki çağrı `ExampleMethod` üçüncü parametresi için kullanılabilir ancak ikinci bağımsız değişken sağlandığından bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b8838-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="b8838-139">Üçüncü parametre adını biliyorsanız, bu görevi gerçekleştirmek için bir adlandırılmış bağımsız değişkeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8838-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="b8838-140">IntelliSense ayraçlar isteğe bağlı parametreleri belirtmek için aşağıdaki çizimde gösterildiği gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8838-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b8838-141">![Hızlı bilgi ExampleMethod yöntemi için IntelliSense. ](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="b8838-141">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="b8838-142">ExampleMethod isteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="b8838-142">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8838-143">.NET kullanarak isteğe bağlı parametreler bildirebilirsiniz <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8838-143">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="b8838-144">`OptionalAttribute` parametre bir varsayılan değer gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b8838-144">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8838-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8838-145">Example</span></span>  
 <span data-ttu-id="b8838-146">Aşağıdaki örnekte, Oluşturucusu `ExampleClass` isteğe bağlı olduğu bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="b8838-146">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="b8838-147">Örnek yöntemi `ExampleMethod` bir gerekli parametresi `required`ve isteğe bağlı parametrelerden `optionalstr` ve `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="b8838-147">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="b8838-148">Kodda `Main` , yöntem ve oluşturucu çağrılacak farklı yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8838-148">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="b8838-149">COM arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b8838-149">COM Interfaces</span></span>  
 <span data-ttu-id="b8838-150">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneleri ve diğer geliştirmeler desteği yanı sıra Office Otomasyon API'leri gibi COM API'leri ile birlikte çalışabilirlik büyük ölçüde geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8838-150">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="b8838-151">Örneğin, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Microsoft Office Excel yönteminde <xref:Microsoft.Office.Interop.Excel.Range> arabirimi tümü isteğe bağlı olan yedi parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b8838-151">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="b8838-152">Bu parametreler aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8838-152">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b8838-153">![AutoFormat yöntemi için hızlı bilgi IntelliSense. ](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="b8838-153">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="b8838-154">AutoFormat parametreleri</span><span class="sxs-lookup"><span data-stu-id="b8838-154">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="b8838-155">C# 3.0 ve önceki sürümlerde, bağımsız değişken aşağıdaki örnekte gösterildiği gibi her parametre için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8838-155">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="b8838-156">Ancak, büyük ölçüde çağrısı basitleştirebilirsiniz `AutoFormat` C# 4.0 sunulan adlandırılmış ve isteğe bağlı bağımsız değişkenler, kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b8838-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="b8838-157">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değeri değiştirmek istemiyorsanız, isteğe bağlı parametresi için bağımsız değişkeni atlamak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b8838-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="b8838-158">Aşağıdaki çağrıda yedi parametreleri yalnızca biri için bir değer belirtilirse.</span><span class="sxs-lookup"><span data-stu-id="b8838-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="b8838-159">Daha fazla bilgi ve örnekler için bkz. [nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) ve [nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b8838-159">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="b8838-160">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="b8838-160">Overload Resolution</span></span>  
 <span data-ttu-id="b8838-161">Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullanımını aşırı yükleme çözünürlüğü aşağıdaki şekillerde etkiler:</span><span class="sxs-lookup"><span data-stu-id="b8838-161">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="b8838-162">Yöntem, dizin oluşturucu veya Oluşturucu bir aday yürütme için kendi parametrelerinin her biri, isteğe bağlı olduğunu veya karşılık gelen, adına veya konumuna çağrı deyimindeki tek bir bağımsız değişken ve bağımsız değişken, parametre türüne dönüştürülebilen olur.</span><span class="sxs-lookup"><span data-stu-id="b8838-162">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="b8838-163">Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözünürlüğü kuralları açıkça belirtilen bağımsız değişkenler için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b8838-163">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="b8838-164">İsteğe bağlı parametreler için atlanmış bağımsız değişkenler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b8838-164">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="b8838-165">İki adayları eşit derecede iyi olmasını materyali çağrıda atlanıp bağımsız değişkenler için isteğe bağlı parametrelere sahip olmayan bir aday için tercih gider.</span><span class="sxs-lookup"><span data-stu-id="b8838-165">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="b8838-166">Bu aşırı yükleme çözünürlüğü içinde genel bir tercih daha az parametrelere sahip adayları için bir sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="b8838-166">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b8838-167">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b8838-167">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8838-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8838-168">See also</span></span>

- [<span data-ttu-id="b8838-169">Nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="b8838-169">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="b8838-170">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="b8838-170">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="b8838-171">Oluşturucuları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8838-171">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [<span data-ttu-id="b8838-172">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8838-172">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
