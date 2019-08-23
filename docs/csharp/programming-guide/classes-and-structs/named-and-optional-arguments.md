---
title: Adlandırılmış ve Isteğe bağlı bağımsız C# değişkenler-Programlama Kılavuzu
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
ms.openlocfilehash: ad3f7949e01a387c3c7de2a0702d11b106ea0040
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922204"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="a4eac-102">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a4eac-102">Named and Optional Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="a4eac-103">C#4 adlandırılmış ve isteğe bağlı bağımsız değişkenleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-103">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="a4eac-104">*Adlandırılmış bağımsız değişkenler* , bağımsız değişkenini parametrenin adıyla ilişkilendirerek parametre listesindeki konumuyla değil, belirli bir parametre için bir bağımsız değişken belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4eac-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="a4eac-105">*Isteğe bağlı bağımsız değişkenler* bazı parametrelerin bağımsız değişkenlerini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4eac-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="a4eac-106">Her iki yöntem de Yöntemler, Dizin oluşturucular, oluşturucular ve temsilcilerle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="a4eac-107">Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişkenler parametre listesinde değil, bağımsız değişken listesinde göründükleri sırada değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="a4eac-108">Adlandırılmış ve isteğe bağlı parametreler birlikte kullanıldığında, isteğe bağlı parametrelerin bir listesinden yalnızca birkaç parametre için bağımsız değişkenler vermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4eac-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="a4eac-109">Bu yetenek, Microsoft Office Automation API 'Leri gibi COM arabirimlerine yönelik çağrıları büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="a4eac-110">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a4eac-110">Named Arguments</span></span>  
 <span data-ttu-id="a4eac-111">Adlandırılmış bağımsız değişkenler, çağrılan yöntemlerin parametre listelerindeki parametrelerin sırasını aramak ya da sağlamak için sizi hatırlamanız ya da aramanız gereksiniminizden muaf değildir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="a4eac-112">Her bağımsız değişkenin parametresi parametre adı ile belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="a4eac-113">Örneğin, sipariş ayrıntılarını (örneğin, satıcı adı, sipariş numarası & ürün adı) yazdıran bir işlev, işlev tarafından tanımlanan sırada konuma göre bağımsız değişkenler gönderilerek standart şekilde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="a4eac-114">Parametrelerin sırasını hatırlamıyorsanız ancak adlarını biliyorsanız, bağımsız değişkenleri istediğiniz sırada gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4eac-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="a4eac-115">Adlandırılmış bağımsız değişkenler, her bir bağımsız değişkenin ne temsil ettiğini tanımlayarak kodunuzun okunabilirliğini de artırır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="a4eac-116">Aşağıdaki `sellerName` örnek yöntemde null veya boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="a4eac-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="a4eac-117">Hem hem `sellerName` de `productName` dize türlerdir, konumlarına göre bağımsız değişken göndermek yerine, iki bağımsız değişkeni de kullanarak kodu okuyan kişilerin karışmasını azaltır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="a4eac-118">Konumsal bağımsız değişkenlerle birlikte kullanıldığında adlandırılmış bağımsız değişkenler şu kadar geçerlidir</span><span class="sxs-lookup"><span data-stu-id="a4eac-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="a4eac-119">Bunlar, herhangi bir Konumsal bağımsız değişkenle izlenmez veya</span><span class="sxs-lookup"><span data-stu-id="a4eac-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="a4eac-120">_7,2 ile C# başlayarak_, doğru konumda kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="a4eac-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="a4eac-121">Aşağıdaki örnekte, parametresi `orderNum` doğru konumda, ancak açıkça adlandırılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a4eac-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="a4eac-122">Ancak, daha sonra Konumsal bağımsız değişkenler tarafından izleniyorlarsa, sıra dışı adlandırılmış bağımsız değişkenler geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="a4eac-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4eac-123">Example</span></span>  
 <span data-ttu-id="a4eac-124">Aşağıdaki kod, bu bölümdeki örnekleri bazı ek kişilerle birlikte uygular.</span><span class="sxs-lookup"><span data-stu-id="a4eac-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="a4eac-125">İsteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a4eac-125">Optional Arguments</span></span>  
 <span data-ttu-id="a4eac-126">Bir yöntem, Oluşturucu, Dizin Oluşturucu veya temsilci tanımı, parametrelerinin gerekli olduğunu veya isteğe bağlı olduğunu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="a4eac-127">Herhangi bir çağrı gerekli tüm parametrelerin bağımsız değişkenlerini sağlamalıdır, ancak isteğe bağlı parametrelerin bağımsız değişkenlerini atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="a4eac-128">Her isteğe bağlı parametre, tanımının bir parçası olarak varsayılan bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="a4eac-129">Bu parametre için bir bağımsız değişken gönderilmezse, varsayılan değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="a4eac-130">Varsayılan değer, aşağıdaki ifade türlerinden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a4eac-130">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="a4eac-131">sabit bir ifade;</span><span class="sxs-lookup"><span data-stu-id="a4eac-131">a constant expression;</span></span>  
  
- <span data-ttu-id="a4eac-132">formun `new ValType()`bir ifadesi, burada `ValType` [enum](../../language-reference/keywords/enum.md) veya [struct](./structs.md)gibi bir değer türüdür;</span><span class="sxs-lookup"><span data-stu-id="a4eac-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/keywords/enum.md) or a [struct](./structs.md);</span></span>  
  
- <span data-ttu-id="a4eac-133">bir değer türü `ValType` olan [varsayılan form (ValType)](../../language-reference/operators/default.md)ifadesi.</span><span class="sxs-lookup"><span data-stu-id="a4eac-133">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="a4eac-134">İsteğe bağlı parametreler, gerekli parametrelerden sonra parametre listesinin sonunda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="a4eac-135">Çağıran isteğe bağlı parametrelerin her biri için bir bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenlerini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="a4eac-136">Bağımsız değişken listesindeki virgülle ayrılmış boşluklar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a4eac-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="a4eac-137">Örneğin, aşağıdaki kodda, örnek yöntemi `ExampleMethod` bir gerekli ve iki isteğe bağlı parametre ile tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="a4eac-138">Aşağıdaki çağrı `ExampleMethod` , bir derleyici hatasına neden olur, çünkü üçüncü parametre için bir bağımsız değişken sağlanır, ikincisi için değil.</span><span class="sxs-lookup"><span data-stu-id="a4eac-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="a4eac-139">Ancak, üçüncü parametrenin adını biliyorsanız, görevi gerçekleştirmek için adlandırılmış bağımsız değişkeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4eac-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="a4eac-140">IntelliSense, aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreleri göstermek için köşeli ayraçları kullanır:</span><span class="sxs-lookup"><span data-stu-id="a4eac-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![ExampleMethod yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> <span data-ttu-id="a4eac-142">.Net <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfını kullanarak isteğe bağlı parametreler de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4eac-142">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="a4eac-143">`OptionalAttribute`parametreler varsayılan değer gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a4eac-143">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4eac-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4eac-144">Example</span></span>  
 <span data-ttu-id="a4eac-145">Aşağıdaki örnekte, için `ExampleClass` oluşturucusunun bir parametresi vardır, bu isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-145">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="a4eac-146">Örnek yönteminde `ExampleMethod` bir gerekli parametre `optionalstr` , `required`ve `optionalint`iki isteğe bağlı iki parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-146">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="a4eac-147">İçindeki `Main` kod, oluşturucunun ve yönteminin çağrılabileceği farklı yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-147">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="a4eac-148">COM arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a4eac-148">COM Interfaces</span></span>  
 <span data-ttu-id="a4eac-149">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler ve diğer geliştirmeler desteğiyle birlikte, Office Otomasyonu API 'leri gibi COM API 'Leri ile birlikte çalışabilirliği büyük ölçüde geliştirir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="a4eac-150">Örneğin, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> arabirimindeki yöntemin yedi parametresi vardır, hepsi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-150">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="a4eac-151">Bu parametreler aşağıdaki çizimde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a4eac-151">These parameters are shown in the following illustration:</span></span>  
  
 ![Otomatik biçim yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="a4eac-153">C# 3,0 ve önceki sürümlerde, aşağıdaki örnekte gösterildiği gibi her bir parametre için bir bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-153">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="a4eac-154">Ancak, 4,0 ' de `AutoFormat` C# tanıtılan adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanarak çağrısını büyük ölçüde kolaylaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4eac-154">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="a4eac-155">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değerini değiştirmek istemiyorsanız isteğe bağlı bir parametre için bağımsız değişkenini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4eac-155">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="a4eac-156">Aşağıdaki çağrıda, yedi parametreden yalnızca biri için bir değer belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a4eac-156">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="a4eac-157">Daha fazla bilgi ve örnek için bkz [. nasıl yapılır: Office Programlamada](./how-to-use-named-and-optional-arguments-in-office-programming.md) adlandırılmış ve isteğe bağlı bağımsız değişkenleri ve [nasıl yapılacağını kullanın: Visual C# özelliklerini](../interop/how-to-access-office-onterop-objects.md)kullanarak Office birlikte çalışma nesnelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="a4eac-157">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="a4eac-158">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="a4eac-158">Overload Resolution</span></span>  
 <span data-ttu-id="a4eac-159">Adlandırılmış ve isteğe bağlı bağımsız değişkenlerin kullanılması, aşırı yükleme çözünürlüğünü aşağıdaki yollarla etkiler:</span><span class="sxs-lookup"><span data-stu-id="a4eac-159">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="a4eac-160">Bir yöntem, Dizin Oluşturucu veya Oluşturucu, parametrelerinden her biri isteğe bağlı veya bir konuma göre, çağırma deyimindeki tek bir bağımsız değişkene ve bu bağımsız değişken parametre türüne dönüştürülebileceğinden yürütme için bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-160">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="a4eac-161">Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözümleme kuralları, açıkça belirtilen bağımsız değişkenlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-161">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="a4eac-162">İsteğe bağlı parametreler için Atlanan bağımsız değişkenler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="a4eac-162">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="a4eac-163">İki aday eşit derecede iyi bir şekilde yarar olursa, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametreleri olmayan bir adaya gider.</span><span class="sxs-lookup"><span data-stu-id="a4eac-163">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="a4eac-164">Bu, daha az parametreye sahip adaylar için aşırı yükleme çözünürlüğünde genel bir tercihin sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a4eac-164">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a4eac-165">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a4eac-165">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a4eac-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4eac-166">See also</span></span>

- [<span data-ttu-id="a4eac-167">Nasıl yapılır: Office Programlamada adlandırılmış ve Isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a4eac-167">How to: Use Named and Optional Arguments in Office Programming</span></span>](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="a4eac-168">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="a4eac-168">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="a4eac-169">Oluşturucuları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a4eac-169">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="a4eac-170">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="a4eac-170">Using Indexers</span></span>](../indexers/using-indexers.md)
