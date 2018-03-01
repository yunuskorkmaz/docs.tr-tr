---
title: "using statik yönergesi (C# Başvurusu)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5838bede475cf2ad1b72518770241e86206a06bb
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="d5308-102">using statik yönergesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d5308-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="d5308-103">`using static` Yönergesi statik üyeler türü adı belirtmeden erişmek için bir türü belirler.</span><span class="sxs-lookup"><span data-stu-id="d5308-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="d5308-104">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d5308-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="d5308-105">Burada *tam-etki-türü-adı* statik üyeleri bir tür adı belirtmeden başvurulabilir türünün adı.</span><span class="sxs-lookup"><span data-stu-id="d5308-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="d5308-106">Tam olarak nitelenmiş tür adını (tür adı ile birlikte tam ad alanı adı) belirtmezseniz, C# Derleyici Hatası CS0246 oluşturur: "'< tür-adı >' türü veya ad alanı adı bulunamadı."</span><span class="sxs-lookup"><span data-stu-id="d5308-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="d5308-107">`using static` Yönergesi örnek üyelerin de sahip olsa bile statik üyeleri olan tüm türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d5308-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="d5308-108">Ancak, örnek üyeleri yalnızca türü örneği çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5308-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="d5308-109">`using static` Yönergesi, C# 6'sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d5308-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5308-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5308-110">Remarks</span></span>
 
<span data-ttu-id="d5308-111">Normalde, statik bir üyenin çağırdığınızda, üye adı ile birlikte türü adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d5308-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="d5308-112">Art arda türün üyeleri çağırmak için aynı tür adı girerek ayrıntılı, belirsiz kodda neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5308-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="d5308-113">Örneğin, aşağıdaki tanımı bir `Circle` sınıfı üyeleri sayısı başvuran <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5308-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="d5308-114">Açıkça başvuru gereğini ortadan tarafından <xref:System.Math> sınıf üyesi başvurulur, her zaman `using static` yönergesi kadar temizleyici kod üretir:</span><span class="sxs-lookup"><span data-stu-id="d5308-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="d5308-115">`using static`yalnızca erişilebilir statik üyeleri ve iç içe geçmiş türler belirtilen türdeki bildirilen alır.</span><span class="sxs-lookup"><span data-stu-id="d5308-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="d5308-116">Devralınan üyeleri içeri aktarılmadı.</span><span class="sxs-lookup"><span data-stu-id="d5308-116">Inherited members are not imported.</span></span>  <span data-ttu-id="d5308-117">Her adlandırılmış tür kullanarak içeri aktarabilirsiniz Visual Basic modülleri dahil statik yönergesi.</span><span class="sxs-lookup"><span data-stu-id="d5308-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="d5308-118">F # en üst düzey işlevleri meta verilerinde geçerli bir C# tanımlayıcı adı olan adlandırılmış bir türün statik üyeleri görünüyorsa, F # işlevleri içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5308-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="d5308-119">`using static`uzantısı yöntemi arama için kullanılabilen belirtilen türü içinde bildirilen genişletme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5308-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="d5308-120">Ancak, genişletme yöntemleri adlarını kodda nitelenmemiş başvurusu için kapsam içine içeri aktarılmadı.</span><span class="sxs-lookup"><span data-stu-id="d5308-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="d5308-121">Farklı türler farklı tarafından alınan aynı ada sahip yöntem `using static` yönergeleri aynı derleme birim veya ad alanı form yöntemi grubu.</span><span class="sxs-lookup"><span data-stu-id="d5308-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="d5308-122">Bu yöntem grupları içinde aşırı yükleme çözünürlüğü normal C# kurallara uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5308-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5308-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5308-123">Example</span></span>

<span data-ttu-id="d5308-124">Aşağıdaki örnek kullanır `using static` statik üyeleri yapmak için yönergesi <xref:System.Console>, <xref:System.Math>, ve <xref:System.String> sınıfları kendi türü adını belirtmek zorunda kalmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5308-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="d5308-125">Örnekte, `using static` yönergesi ayrıca uygulandı için <xref:System.Double> türü.</span><span class="sxs-lookup"><span data-stu-id="d5308-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="d5308-126">Bu çağrı mümkün yapılan <xref:System.Double.TryParse(System.String,System.Double@)> bir tür adı belirtmeden yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5308-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="d5308-127">Ancak, bu daha az okunabilir kod oluşturur denetlemek gerekli hale beri `using static` hangi sayısal türün belirlemek için deyimleri `TryParse` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d5308-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5308-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5308-128">See also</span></span>

<span data-ttu-id="d5308-129">[using yönergesi](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="d5308-129">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="d5308-130">[C# başvurusu](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5308-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="d5308-131">[C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5308-131">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="d5308-132">[Ad alanlarını kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="d5308-132">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="d5308-133">[Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="d5308-133">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="d5308-134">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="d5308-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   
