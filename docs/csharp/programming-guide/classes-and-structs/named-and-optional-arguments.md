---
title: Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)
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
ms.openlocfilehash: b0963457e22bf0c3fc92d33c5ed0eb699be27cf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326338"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="a6464-102">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a6464-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="a6464-103"> adlandırılmış ve isteğe bağlı bağımsız değişkenler tanıtır.</span><span class="sxs-lookup"><span data-stu-id="a6464-103"> introduces named and optional arguments.</span></span> <span data-ttu-id="a6464-104">*Bağımsız değişkenler adlı* , belirli bir parametre için bir bağımsız değişken bağımsız değişken parametre adı yerine parametre listesinde parametrenin konumu ile ilişkilendirerek belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="a6464-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="a6464-105">*İsteğe bağlı bağımsız değişkenler* bazı parametreler için bağımsız değişken atlayın olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6464-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="a6464-106">Her iki tekniği yöntemleri, dizin oluşturucular, Oluşturucular ve temsilciler ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6464-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="a6464-107">Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişken bağımsız değişken listesi, parametre listesi görünme sırasını değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a6464-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="a6464-108">Adlandırılmış ve isteğe bağlı parametreler birlikte kullanıldığında, yalnızca birkaç parametre isteğe bağlı parametreler listesinden için bağımsız değişkenleri eklemek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a6464-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="a6464-109">Bu özelliği COM arabirimleri gibi Microsoft Office Otomasyon API çağrıları büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a6464-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="a6464-110">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a6464-110">Named Arguments</span></span>  
 <span data-ttu-id="a6464-111">Adlandırılmış bağımsız değişkenler gereken anımsaması veya çağrılan yöntem parametre listesi parametrelerinde sırasını bakmak için gelen boş.</span><span class="sxs-lookup"><span data-stu-id="a6464-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="a6464-112">Her değişken için parametresi tarafından parametre adı belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6464-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="a6464-113">Örneğin, sipariş ayrıntılarını yazdırır bir işlev (gibi satıcı adı, sipariş numarası & ürün adı) standart biçiminde bağımsız değişkenleri sıralamasında, işlev tarafından tanımlanan gönderen tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6464-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="a6464-114">Parametreler sırası hatırlamıyorsanız, ancak adlarını bilmeniz bağımsız değişkenler herhangi bir sırada gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6464-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="a6464-115">Adlandırılmış bağımsız değişkenler ne her bağımsız değişkeni temsil eden belirleyerek kodunuzun okunabilirliğini de geliştirir.</span><span class="sxs-lookup"><span data-stu-id="a6464-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="a6464-116">Aşağıdaki örnek yönteminde `sellerName` null veya boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="a6464-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="a6464-117">Her ikisi de olarak `sellerName` ve `productName` dize türleri, bağımsız değişkenleri konuma göre göndermek yerine, iki belirsizliğini ortadan kaldırmak ve kod okuyan herkes için karışıklığı azaltmak için adlandırılmış bağımsız değişkenler kullanılacak mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="a6464-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="a6464-118">Bağımsız değişkenler, konumsal bağımsız değişkenlerle birlikte kullanıldığında adlı, geçerli olan sürece</span><span class="sxs-lookup"><span data-stu-id="a6464-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="a6464-119">Bunlar konumsal tüm bağımsız değişkenleri tarafından izlenmeyen veya</span><span class="sxs-lookup"><span data-stu-id="a6464-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="a6464-120">_C# ile 7.2 Başlangıç_, doğru konumda kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="a6464-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="a6464-121">Parametre aşağıdaki örnekte `orderNum` doğru konumda olsa da açıkça adlı değil.</span><span class="sxs-lookup"><span data-stu-id="a6464-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="a6464-122">Ancak, sipariş adlandırılmış bağımsız değişkenler konumsal değişkenleriyle ardından varsa geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="a6464-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="a6464-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6464-123">Example</span></span>  
 <span data-ttu-id="a6464-124">Aşağıdaki kod, bu bölümde bazı ek olanları birlikte örneklerinden uygular.</span><span class="sxs-lookup"><span data-stu-id="a6464-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="a6464-125">İsteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a6464-125">Optional Arguments</span></span>  
 <span data-ttu-id="a6464-126">Yöntemi, oluşturucusu, dizin oluşturucu veya temsilci tanımını parametrelerini gerekli veya isteğe bağlı oldukları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6464-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="a6464-127">Tüm çağrısı tüm gerekli parametreleri için bağımsız değişkenleri belirtmeniz gerekir, ancak isteğe bağlı parametreler için bağımsız değişken atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6464-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="a6464-128">Her isteğe bağlı bir parametre kendi tanımının bir parçası olarak varsayılan bir değeri yok.</span><span class="sxs-lookup"><span data-stu-id="a6464-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="a6464-129">Bu parametre için bağımsız değişken gönderilirse, varsayılan değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6464-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="a6464-130">Varsayılan değer ifadelerin aşağıdaki türlerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a6464-130">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="a6464-131">bir sabit ifadesine;</span><span class="sxs-lookup"><span data-stu-id="a6464-131">a constant expression;</span></span>  
  
-   <span data-ttu-id="a6464-132">bir ifade formun `new ValType()`, burada `ValType` olduğu gibi bir değer türü bir [enum](../../../csharp/language-reference/keywords/enum.md) veya [yapısı](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="a6464-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="a6464-133">bir ifade formun [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), burada `ValType` değer türü değil.</span><span class="sxs-lookup"><span data-stu-id="a6464-133">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="a6464-134">İsteğe bağlı parametreler parametre listesinin sonuna sonra gerekli parametreleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a6464-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="a6464-135">Çağıran bir bağımsız değişken isteğe bağlı parametrelerden biri art arda herhangi biri için sağlıyorsa, tüm önceki isteğe bağlı parametreler için bağımsız değişken sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6464-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="a6464-136">Bağımsız değişken listesi boşluklar virgülle ayrılmış desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a6464-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="a6464-137">Örneğin, aşağıdaki kodda yöntemi örneği `ExampleMethod` gerekli bir ve iki isteğe bağlı parametreler ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a6464-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 <span data-ttu-id="a6464-138">Aşağıdaki çağrı `ExampleMethod` üçüncü parametre için kullanılabilir ancak ikinci bağımsız değişken sağlanan derleyici hatası neden olur.</span><span class="sxs-lookup"><span data-stu-id="a6464-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="a6464-139">Ancak, üçüncü parametre adını biliyorsanız, görevi gerçekleştirmek için bir adlandırılmış bağımsız değişkeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6464-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="a6464-140">IntelliSense köşeli isteğe bağlı parametreler belirtmek için aşağıdaki çizimde gösterildiği gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6464-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="a6464-141">![ExampleMethod yöntemi için IntelliSense Hızlı bilgileri. ] (../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="a6464-141">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="a6464-142">ExampleMethod isteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="a6464-142">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6464-143">.NET kullanarak isteğe bağlı parametreler bildirebilirsiniz <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a6464-143">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="a6464-144">`OptionalAttribute` Parametreler varsayılan bir değer gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a6464-144">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6464-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6464-145">Example</span></span>  
 <span data-ttu-id="a6464-146">Aşağıdaki örnekte, Oluşturucusu `ExampleClass` isteğe bağlı olduğu bir parametre içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a6464-146">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="a6464-147">Örnek yöntemi `ExampleMethod` gerekli parametresinin, `required`ve iki isteğe bağlı parametreler `optionalstr` ve `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="a6464-147">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="a6464-148">Kodda `Main` , yöntemi ve Oluşturucusu çağrılabilir farklı yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6464-148">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="a6464-149">COM arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a6464-149">COM Interfaces</span></span>  
 <span data-ttu-id="a6464-150">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler ve diğer geliştirmeler desteğinin yanı sıra Office Automation API'leri gibi COM API'leri ile birlikte çalışabilirlik büyük ölçüde artırır.</span><span class="sxs-lookup"><span data-stu-id="a6464-150">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="a6464-151">Örneğin, [biçim](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) Microsoft Office Excel yönteminde [aralığı](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) arabirimi tümü isteğe bağlı yedi parametreleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a6464-151">For example, the [AutoFormat](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) method in the Microsoft Office Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="a6464-152">Bu parametreler aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6464-152">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="a6464-153">![Otomatik Biçim yöntemi için IntelliSense Hızlı bilgileri. ] (../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="a6464-153">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="a6464-154">Otomatik Biçim parametreleri</span><span class="sxs-lookup"><span data-stu-id="a6464-154">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="a6464-155">C# 3.0 ve önceki sürümlerde, bağımsız değişken aşağıdaki örnekte gösterildiği gibi her bir parametreyi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a6464-155">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 <span data-ttu-id="a6464-156">Ancak, büyük ölçüde çağrısı basitleştirebilir `AutoFormat` C# 4. 0'sunulan adlandırılmış ve isteğe bağlı bağımsız değişkenler, kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a6464-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="a6464-157">Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değeri değiştirmek istemiyorsanız, isteğe bağlı bir parametre için bağımsız değişken atlamak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a6464-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="a6464-158">Aşağıdaki çağrısında yedi parametrelerden yalnızca birini kullanmak için bir değer belirtilirse.</span><span class="sxs-lookup"><span data-stu-id="a6464-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 <span data-ttu-id="a6464-159">Daha fazla bilgi ve örnekler için bkz: [nasıl yapılır: kullanım adlandırılmış ve isteğe bağlı bağımsız değişkenler Office programlama](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) ve [nasıl yapılır: erişim Office birlikte çalışma nesnelerine kullanarak olan Visual C# özellikleri tarafından](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="a6464-159">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="a6464-160">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="a6464-160">Overload Resolution</span></span>  
 <span data-ttu-id="a6464-161">Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullanımını aşırı yükleme çözümü aşağıdaki şekillerde etkiler:</span><span class="sxs-lookup"><span data-stu-id="a6464-161">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="a6464-162">Yöntemi, dizin oluşturucu veya oluşturucusu yürütme aday, tüm parametrelerinin isteğe bağlı olduğu veya karşılık gelen, adıyla veya konuma arama deyiminde tek bir bağımsız değişken ve bağımsız değişken parametre türüne dönüştürülebilir ise.</span><span class="sxs-lookup"><span data-stu-id="a6464-162">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="a6464-163">Birden fazla aday bulunursa, tercih edilen dönüştürmeleri için aşırı çözümleme kurallarını açıkça belirtilen bağımsız değişkenler için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a6464-163">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="a6464-164">İsteğe bağlı parametreleri belirtilmemişse bağımsız değişkenleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="a6464-164">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="a6464-165">İki aday eşit iyi olmasını nitelendirilmiştir, tercih değişkenleri çağrısında atlanmış isteğe bağlı parametreler yok bir aday gider.</span><span class="sxs-lookup"><span data-stu-id="a6464-165">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="a6464-166">Daha az parametrelere sahip bir aday aşırı çözünürlük genel bir tercih sonucu budur.</span><span class="sxs-lookup"><span data-stu-id="a6464-166">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a6464-167">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a6464-167">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6464-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6464-168">See Also</span></span>  
 [<span data-ttu-id="a6464-169">Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a6464-169">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [<span data-ttu-id="a6464-170">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="a6464-170">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="a6464-171">Oluşturucuları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a6464-171">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [<span data-ttu-id="a6464-172">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="a6464-172">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
