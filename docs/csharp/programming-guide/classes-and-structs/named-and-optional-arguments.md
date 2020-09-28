---
title: Adlandırılmış ve Isteğe bağlı bağımsız değişkenler-C# Programlama Kılavuzu
description: C# ' de adlandırılmış bağımsız değişkenler, konum değil, ada göre bağımsız değişkenleri belirtir. İsteğe bağlı bağımsız değişkenler atlanabilir.
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
ms.openlocfilehash: 4c9c932e3df4035024c90e92e4d80309fffe3ce3
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406238"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="668b5-104">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="668b5-104">Named and Optional Arguments (C# Programming Guide)</span></span>

<span data-ttu-id="668b5-105">C# 4 adlandırılmış ve isteğe bağlı bağımsız değişkenleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="668b5-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="668b5-106">*Adlandırılmış bağımsız değişkenler* , bağımsız değişkenini parametre listesindeki konumuyla değil, adıyla eşleştirerek bir parametre için bir bağımsız değişken belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="668b5-106">*Named arguments* enable you to specify an argument for a parameter by matching the argument with its name rather than with its position in the parameter list.</span></span> <span data-ttu-id="668b5-107">*Isteğe bağlı bağımsız değişkenler* bazı parametrelerin bağımsız değişkenlerini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="668b5-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="668b5-108">Her iki yöntem de Yöntemler, Dizin oluşturucular, oluşturucular ve temsilcilerle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>

<span data-ttu-id="668b5-109">Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişkenler parametre listesinde değil, bağımsız değişken listesinde göründükleri sırada değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>

<span data-ttu-id="668b5-110">Adlandırılmış ve isteğe bağlı parametreler, seçili parametreler için bağımsız değişkenler vermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="668b5-110">Named and optional parameters enable you to supply arguments for selected parameters.</span></span> <span data-ttu-id="668b5-111">Bu özellik, Microsoft Office Automation API 'Leri gibi COM arabirimlerine yapılan çağrıları büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="668b5-111">This capability greatly eases calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="668b5-112">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="668b5-112">Named Arguments</span></span>

<span data-ttu-id="668b5-113">Adlandırılmış bağımsız değişkenler, çağrılan yöntemlerin parametre listelerindeki parametrelerin sırasını eşleştirmeden size ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="668b5-113">Named arguments free you from matching the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="668b5-114">Her bağımsız değişkenin parametresi parametre adı ile belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="668b5-115">Örneğin, sipariş ayrıntılarını (örneğin, satıcı adı, sipariş numarası & ürün adı) yazdıran bir işlev, işlev tarafından tanımlanan sırada konuma göre bağımsız değişkenler gönderilerek çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called by sending arguments by position, in the order defined by the function.</span></span>

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

<span data-ttu-id="668b5-116">Parametrelerin sırasını hatırlamıyorsanız ancak adlarını biliyorsanız, bağımsız değişkenleri istediğiniz sırada gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="668b5-116">If you don't remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

<span data-ttu-id="668b5-117">Adlandırılmış bağımsız değişkenler, her bir bağımsız değişkenin ne temsil ettiğini tanımlayarak kodunuzun okunabilirliğini de artırır.</span><span class="sxs-lookup"><span data-stu-id="668b5-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="668b5-118">Aşağıdaki örnek yöntemde `sellerName` null veya boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="668b5-118">In the example method below, the `sellerName` can't be null or white space.</span></span> <span data-ttu-id="668b5-119">Hem hem `sellerName` de `productName` dize türlerdir, konumlarına göre bağımsız değişken göndermek yerine, iki bağımsız değişkeni de kullanarak kodu okuyan kişilerin karışmasını azaltır.</span><span class="sxs-lookup"><span data-stu-id="668b5-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
<span data-ttu-id="668b5-120">Konumsal bağımsız değişkenlerle birlikte kullanıldığında adlandırılmış bağımsız değişkenler şu kadar geçerlidir</span><span class="sxs-lookup"><span data-stu-id="668b5-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="668b5-121">Bunlar, herhangi bir Konumsal bağımsız değişkenle izlenmez veya</span><span class="sxs-lookup"><span data-stu-id="668b5-121">they're not followed by any positional arguments, or</span></span>

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- <span data-ttu-id="668b5-122">_C# 7,2 ile başlayarak_, doğru konumda kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="668b5-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="668b5-123">Aşağıdaki örnekte, parametresi `orderNum` doğru konumda, ancak açıkça adlandırılmıyor.</span><span class="sxs-lookup"><span data-stu-id="668b5-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

<span data-ttu-id="668b5-124">Herhangi bir sıra dışı adlandırılmış bağımsız değişkeni izleyen Konumsal bağımsız değişkenler geçersiz.</span><span class="sxs-lookup"><span data-stu-id="668b5-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a><span data-ttu-id="668b5-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="668b5-125">Example</span></span>

<span data-ttu-id="668b5-126">Aşağıdaki kod, bu bölümdeki örnekleri bazı ek kişilerle birlikte uygular.</span><span class="sxs-lookup"><span data-stu-id="668b5-126">The following code implements the examples from this section along with some additional ones.</span></span>  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a><span data-ttu-id="668b5-127">İsteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="668b5-127">Optional Arguments</span></span>

<span data-ttu-id="668b5-128">Bir yöntem, Oluşturucu, Dizin Oluşturucu ya da temsilcinin tanımı, parametrelerinin gerekli veya isteğe bağlı olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-128">The definition of a method, constructor, indexer, or delegate can specify its parameters are required or optional.</span></span> <span data-ttu-id="668b5-129">Herhangi bir çağrı gerekli tüm parametrelerin bağımsız değişkenlerini sağlamalıdır, ancak isteğe bağlı parametrelerin bağımsız değişkenlerini atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>

<span data-ttu-id="668b5-130">Her isteğe bağlı parametre, tanımının bir parçası olarak varsayılan bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="668b5-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="668b5-131">Bu parametre için bir bağımsız değişken gönderilmezse, varsayılan değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="668b5-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="668b5-132">Varsayılan değer, aşağıdaki ifade türlerinden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="668b5-132">A default value must be one of the following types of expressions:</span></span>
  
- <span data-ttu-id="668b5-133">sabit bir ifade;</span><span class="sxs-lookup"><span data-stu-id="668b5-133">a constant expression;</span></span>  
- <span data-ttu-id="668b5-134">formun bir ifadesi, `new ValType()` burada `ValType` [enum](../../language-reference/builtin-types/enum.md) veya [struct](../../language-reference/builtin-types/struct.md)gibi bir değer türüdür;</span><span class="sxs-lookup"><span data-stu-id="668b5-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>
- <span data-ttu-id="668b5-135">bir değer türü olan [varsayılan form (ValType)](../../language-reference/operators/default.md)ifadesi `ValType` .</span><span class="sxs-lookup"><span data-stu-id="668b5-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>

<span data-ttu-id="668b5-136">İsteğe bağlı parametreler, gerekli parametrelerden sonra parametre listesinin sonunda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="668b5-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="668b5-137">Çağıran isteğe bağlı parametrelerin her biri için bir bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenlerini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="668b5-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="668b5-138">Bağımsız değişken listesindeki virgülle ayrılmış boşluklar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="668b5-138">Comma-separated gaps in the argument list aren't supported.</span></span> <span data-ttu-id="668b5-139">Örneğin, aşağıdaki kodda, örnek yöntemi `ExampleMethod` bir gerekli ve iki isteğe bağlı parametre ile tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="668b5-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

<span data-ttu-id="668b5-140">Aşağıdaki çağrı, `ExampleMethod` bir derleyici hatasına neden olur, çünkü üçüncü parametre için bir bağımsız değişken sağlanır, ikincisi için değil.</span><span class="sxs-lookup"><span data-stu-id="668b5-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>

```csharp
//anExample.ExampleMethod(3, ,4);
```

<span data-ttu-id="668b5-141">Ancak, üçüncü parametrenin adını biliyorsanız, görevi gerçekleştirmek için adlandırılmış bağımsız değişkeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="668b5-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

<span data-ttu-id="668b5-142">IntelliSense, aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreleri göstermek için köşeli ayraçları kullanır:</span><span class="sxs-lookup"><span data-stu-id="668b5-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>

![ExampleMethod yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> <span data-ttu-id="668b5-144">.NET sınıfını kullanarak isteğe bağlı parametreler de bildirebilirsiniz <xref:System.Runtime.InteropServices.OptionalAttribute> .</span><span class="sxs-lookup"><span data-stu-id="668b5-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="668b5-145">`OptionalAttribute` parametreler varsayılan değer gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="668b5-145">`OptionalAttribute` parameters do not require a default value.</span></span>

## <a name="example"></a><span data-ttu-id="668b5-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="668b5-146">Example</span></span>

<span data-ttu-id="668b5-147">Aşağıdaki örnekte, için oluşturucusunun `ExampleClass` bir parametresi vardır, bu isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="668b5-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="668b5-148">Örnek yönteminde `ExampleMethod` bir gerekli parametre, `required` ve iki isteğe bağlı iki parametre vardır `optionalstr` `optionalint` .</span><span class="sxs-lookup"><span data-stu-id="668b5-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="668b5-149">İçindeki kod, `Main` oluşturucunun ve yönteminin çağrılabileceği farklı yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="668b5-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

<span data-ttu-id="668b5-150">Yukarıdaki kod, isteğe bağlı parametrelerin doğru uygulanmadığı bir dizi örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="668b5-150">The preceding code shows a number of examples where optional parameters aren't applied correctly.</span></span> <span data-ttu-id="668b5-151">İlki, gereken ilk parametre için bir bağımsız değişkenin sağlanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="668b5-151">The first illustrates that an argument must be supplied for the first parameter, which is required.</span></span>
  
## <a name="com-interfaces"></a><span data-ttu-id="668b5-152">COM arabirimleri</span><span class="sxs-lookup"><span data-stu-id="668b5-152">COM Interfaces</span></span>

<span data-ttu-id="668b5-153">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler desteğiyle birlikte, Office Otomasyonu API 'leri gibi COM API 'Leri ile birlikte çalışabilirliği büyük ölçüde geliştirir.</span><span class="sxs-lookup"><span data-stu-id="668b5-153">Named and optional arguments, along with support for dynamic objects, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>

<span data-ttu-id="668b5-154">Örneğin, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> arabirimindeki yöntemin yedi parametresi vardır, hepsi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="668b5-154">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="668b5-155">Bu parametreler aşağıdaki çizimde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="668b5-155">These parameters are shown in the following illustration:</span></span>

![Otomatik biçim yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)

<span data-ttu-id="668b5-157">C# 3,0 ve önceki sürümlerinde, aşağıdaki örnekte gösterildiği gibi her bir parametre için bir bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="668b5-157">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

<span data-ttu-id="668b5-158">Ancak, `AutoFormat` C# 4,0 ' de tanıtılan adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanarak çağrısı büyük ölçüde basitleşebilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-158">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="668b5-159">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değerini değiştirmek istemiyorsanız isteğe bağlı bir parametre için bağımsız değişkenini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="668b5-159">Named and optional arguments enable you to omit the argument for an optional parameter if you don't want to change the parameter's default value.</span></span> <span data-ttu-id="668b5-160">Aşağıdaki çağrıda, yedi parametreden yalnızca biri için bir değer belirtilir.</span><span class="sxs-lookup"><span data-stu-id="668b5-160">In the following call, a value is specified for only one of the seven parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

<span data-ttu-id="668b5-161">Daha fazla bilgi ve örnek için bkz. [Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](./how-to-use-named-and-optional-arguments-in-office-programming.md) ve [C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişme](../interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="668b5-161">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>
  
## <a name="overload-resolution"></a><span data-ttu-id="668b5-162">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="668b5-162">Overload Resolution</span></span>

<span data-ttu-id="668b5-163">Adlandırılmış ve isteğe bağlı bağımsız değişkenlerin kullanılması, aşırı yükleme çözünürlüğünü aşağıdaki yollarla etkiler:</span><span class="sxs-lookup"><span data-stu-id="668b5-163">Use of named and optional arguments affects overload resolution in the following ways:</span></span>

- <span data-ttu-id="668b5-164">Bir yöntem, Dizin Oluşturucu veya Oluşturucu, parametrelerinden her biri isteğe bağlı veya bir konuma göre, çağırma deyimindeki tek bir bağımsız değişkene ve bu bağımsız değişken parametre türüne dönüştürülebileceğinden yürütme için bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="668b5-164">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
- <span data-ttu-id="668b5-165">Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözümleme kuralları, açıkça belirtilen bağımsız değişkenlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="668b5-165">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="668b5-166">İsteğe bağlı parametreler için Atlanan bağımsız değişkenler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="668b5-166">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="668b5-167">İki aday eşit derecede iyi bir şekilde yarar olursa, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametreleri olmayan bir adaya gider.</span><span class="sxs-lookup"><span data-stu-id="668b5-167">If two candidates are judged to be equally good, preference goes to a candidate that doesn't have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="668b5-168">Aşırı yükleme çözümlemesi genellikle daha az parametreye sahip adayları tercih eder.</span><span class="sxs-lookup"><span data-stu-id="668b5-168">Overload resolution generally prefers candidates that have fewer parameters.</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="668b5-169">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="668b5-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
