---
title: Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler - C# Programlama Kılavuzu
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
ms.openlocfilehash: 15b685248730c1f742035612a201d97d180bbc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399814"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="a562b-102">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a562b-102">Named and Optional Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="a562b-103">C# 4 adlı ve isteğe bağlı bağımsız değişkenleri tanır.</span><span class="sxs-lookup"><span data-stu-id="a562b-103">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="a562b-104">*Adlandırılmış bağımsız değişkenler,* parametre listesindeki parametrenin konumu yerine bağımsız değişkeni parametrenin adı ile ilişkilendirerek belirli bir parametre için bir bağımsız değişken belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a562b-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="a562b-105">*İsteğe bağlı bağımsız değişkenler,* bazı parametreler için bağımsız değişkenleri atlayabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a562b-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="a562b-106">Her iki teknik de yöntemler, dizin oluşturucular, oluşturucular ve temsilcilerle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a562b-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="a562b-107">Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişkenler parametre listesinde değil, bağımsız değişken listesinde göründükleri sırada değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a562b-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="a562b-108">Adlandırılmış ve isteğe bağlı parametreler, birlikte kullanıldığında, isteğe bağlı parametreler listesinden yalnızca birkaç parametre için bağımsız değişken ler sağlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a562b-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="a562b-109">Bu özellik, Microsoft Office Automation API'leri gibi COM arabirimlerine yapılan çağrıları büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a562b-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="a562b-110">Adlandırılmış Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a562b-110">Named Arguments</span></span>  
 <span data-ttu-id="a562b-111">Adlandırılmış bağımsız değişkenler, çağrılan yöntemlerin parametre listelerindeki parametrelerin sırasını hatırlama veya arama gereksiniminden sizi kurtarır.</span><span class="sxs-lookup"><span data-stu-id="a562b-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="a562b-112">Her bağımsız değişken için parametre parametre adı ile belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a562b-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="a562b-113">Örneğin, sipariş ayrıntılarını yazdıran bir işlev (satıcı adı, sipariş numarası & ürün adı gibi) işlev tarafından tanımlanan sırada, konuma göre bağımsız değişkenler gönderilerek standart şekilde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a562b-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="a562b-114">Parametrelerin sırasını hatırlamıyor ancak adlarını biliyorsanız, bağımsız değişkenleri istediğiniz sırada gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a562b-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="a562b-115">Adlandırılmış bağımsız değişkenler, her bağımsız değişkenin neyi temsil ettiğini belirleyerek kodunuzu okunabilirliğini de artırır.</span><span class="sxs-lookup"><span data-stu-id="a562b-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="a562b-116">Aşağıdaki örnek yöntemde, `sellerName` null veya beyaz boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="a562b-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="a562b-117">Her `sellerName` ikisi `productName` de ve dize türleri olarak, yerine konuma göre bağımsız değişkenler gönderme, bu iki ayrıştırmak ve kodu okuyan herkes için karışıklığı azaltmak için adlandırılmış bağımsız değişkenleri kullanmak mantıklı.</span><span class="sxs-lookup"><span data-stu-id="a562b-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="a562b-118">Adlandırılmış bağımsız değişkenler, konumsal bağımsız değişkenler ile kullanıldığında,</span><span class="sxs-lookup"><span data-stu-id="a562b-118">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="a562b-119">herhangi bir konumsal argüman tarafından takip edilmez, ya da</span><span class="sxs-lookup"><span data-stu-id="a562b-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="a562b-120">_C# 7.2 ile başlayarak,_ doğru pozisyonda kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="a562b-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="a562b-121">Aşağıdaki örnekte, parametre `orderNum` doğru konumdadır, ancak açıkça adlandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="a562b-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="a562b-122">Adlandırılmış bağımsız değişkenleri izleyen konum dışı bağımsız değişkenler geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="a562b-122">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="a562b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="a562b-123">Example</span></span>  
 <span data-ttu-id="a562b-124">Aşağıdaki kod, bazı ek leriyle birlikte bu bölümden örnekler uygular.</span><span class="sxs-lookup"><span data-stu-id="a562b-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="a562b-125">İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a562b-125">Optional Arguments</span></span>  
 <span data-ttu-id="a562b-126">Yöntemin, oluşturucunun, dizinin dizinleyicinin veya temsilcinin tanımı, parametrelerinin gerekli olduğunu veya isteğe bağlı olduğunu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="a562b-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="a562b-127">Herhangi bir çağrı, gerekli tüm parametreler için bağımsız değişkenler sağlamalıdır, ancak isteğe bağlı parametreler için bağımsız değişkenleri atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a562b-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="a562b-128">Her isteğe bağlı parametre, tanımının bir parçası olarak varsayılan değere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a562b-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="a562b-129">Bu parametre için bağımsız değişken gönderilmezse, varsayılan değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a562b-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="a562b-130">Varsayılan değer aşağıdaki ifade türlerinden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a562b-130">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="a562b-131">sabit bir ifade;</span><span class="sxs-lookup"><span data-stu-id="a562b-131">a constant expression;</span></span>  
  
- <span data-ttu-id="a562b-132">formun `new ValType()`bir ifadesi `ValType` , bir değer türü, bir [enum](../../language-reference/builtin-types/enum.md) veya [bir yapı](../../language-reference/builtin-types/struct.md)gibi;</span><span class="sxs-lookup"><span data-stu-id="a562b-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>  
  
- <span data-ttu-id="a562b-133">form [varsayılan (ValType)](../../language-reference/operators/default.md)bir ifade `ValType` , bir değer türü dür.</span><span class="sxs-lookup"><span data-stu-id="a562b-133">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="a562b-134">İsteğe bağlı parametreler, gerekli parametrelerden sonra parametre listesinin sonunda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a562b-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="a562b-135">Arayan, ardışık isteğe bağlı parametrelerden herhangi biri için bir bağımsız değişken sağlarsa, önceki tüm isteğe bağlı parametreler için bağımsız değişkenler sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a562b-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="a562b-136">Bağımsız değişken listesindeki virgülden ayrılmış boşluklar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a562b-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="a562b-137">Örneğin, aşağıdaki kodda, örnek `ExampleMethod` yöntemi bir gerekli ve iki isteğe bağlı parametrelerile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a562b-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="a562b-138">Üçüncü parametre `ExampleMethod` için bir bağımsız değişken sağlandığı, ancak ikinci parametre için sağlanmadığından, derleyici hatasına neden olan aşağıdaki çağrı.</span><span class="sxs-lookup"><span data-stu-id="a562b-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="a562b-139">Ancak, üçüncü parametrenin adını biliyorsanız, görevi gerçekleştirmek için adlandırılmış bir bağımsız değişken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a562b-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="a562b-140">IntelliSense, aşağıdaki resimde gösterildiği gibi isteğe bağlı parametreleri belirtmek için parantez kullanır:</span><span class="sxs-lookup"><span data-stu-id="a562b-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![ExampleMethod yöntemi için IntelliSense hızlı bilgi gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> <span data-ttu-id="a562b-142">İsteğe bağlı parametreleri .NET <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfını kullanarak da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a562b-142">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="a562b-143">`OptionalAttribute`parametreler varsayılan değer gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a562b-143">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a562b-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="a562b-144">Example</span></span>  
 <span data-ttu-id="a562b-145">Aşağıdaki örnekte, kurucunun `ExampleClass` isteğe bağlı bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="a562b-145">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="a562b-146">Örnek `ExampleMethod` yönteminin bir gerekli `required`parametresi ve `optionalstr` `optionalint`iki isteğe bağlı parametresi vardır ve .</span><span class="sxs-lookup"><span data-stu-id="a562b-146">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="a562b-147">Kod, `Main` oluşturucu ve yöntemin çağrılabileceği farklı yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="a562b-147">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="a562b-148">COM Arayüzleri</span><span class="sxs-lookup"><span data-stu-id="a562b-148">COM Interfaces</span></span>  
 <span data-ttu-id="a562b-149">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler ve diğer geliştirmeler için destekle birlikte, Office Automation API'leri gibi COM API'leri ile birlikte çalışabilirliği büyük ölçüde artırır.</span><span class="sxs-lookup"><span data-stu-id="a562b-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="a562b-150">Örneğin, Microsoft <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Office Excel <xref:Microsoft.Office.Interop.Excel.Range> arabirimindeki yöntemin yedi parametresi vardır ve bunların tümü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a562b-150">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="a562b-151">Bu parametreler aşağıdaki resimde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a562b-151">These parameters are shown in the following illustration:</span></span>  
  
 ![AutoFormat yöntemi için IntelliSense hızlı bilgi gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="a562b-153">C# 3.0 ve önceki sürümlerde, aşağıdaki örnekte gösterildiği gibi, her parametre için bir bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a562b-153">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="a562b-154">Ancak, C# 4.0'da tanıtılan adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanarak aramayı `AutoFormat` büyük ölçüde basitleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a562b-154">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="a562b-155">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değerini değiştirmek istemiyorsanız, bağımsız değişkeni isteğe bağlı bir parametre için atabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a562b-155">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="a562b-156">Aşağıdaki çağrıda, yedi parametreden yalnızca biri için bir değer belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a562b-156">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="a562b-157">Daha fazla bilgi ve örnek için, [Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenlerin nasıl kullanılacağı](./how-to-use-named-and-optional-arguments-in-office-programming.md) ve [C# özelliklerini kullanarak Office interop nesnelerine nasıl](../interop/how-to-access-office-onterop-objects.md)erişilir'e bakın.</span><span class="sxs-lookup"><span data-stu-id="a562b-157">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="a562b-158">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="a562b-158">Overload Resolution</span></span>  
 <span data-ttu-id="a562b-159">Adlandırılmış ve isteğe bağlı bağımsız değişkenlerin kullanımı aşırı yük çözümünü aşağıdaki şekillerde etkiler:</span><span class="sxs-lookup"><span data-stu-id="a562b-159">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="a562b-160">Parametrelerinin her biri isteğe bağlı ysa veya ada veya konuma göre, çağrı deyimindeki tek bir bağımsız değişkene karşılık gelen ve bu bağımsız değişken parametre türüne dönüştürülebiliyorsa, bir yöntem, dizin oluşturucu veya oluşturucu yürütme için adaydır.</span><span class="sxs-lookup"><span data-stu-id="a562b-160">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="a562b-161">Birden fazla aday bulunursa, tercih edilen dönüşümler için aşırı yükleme çözümleme kuralları açıkça belirtilen bağımsız değişkenlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a562b-161">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="a562b-162">İsteğe bağlı parametreler için atlanan bağımsız değişkenler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="a562b-162">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="a562b-163">İki adayın eşit derecede iyi olduğuna karar vereliise, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametrelere sahip olmayan bir adaya gider.</span><span class="sxs-lookup"><span data-stu-id="a562b-163">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="a562b-164">Bu, daha az parametreye sahip adaylar için aşırı yük çözümünde genel bir tercihin sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a562b-164">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a562b-165">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a562b-165">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a562b-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a562b-166">See also</span></span>

- [<span data-ttu-id="a562b-167">Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a562b-167">How to use named and optional arguments in Office programming</span></span>](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="a562b-168">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="a562b-168">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="a562b-169">Oluşturucuları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a562b-169">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="a562b-170">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="a562b-170">Using Indexers</span></span>](../indexers/using-indexers.md)
