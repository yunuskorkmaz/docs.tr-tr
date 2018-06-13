---
title: using statik yönergesi (C# Başvurusu)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b7508c6e751f83fdc16a700ad68aa7de36e497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285141"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="cc70a-102">using statik yönergesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cc70a-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="cc70a-103">`using static` Yönergesi statik üyeler türü adı belirtmeden erişmek için bir türü belirler.</span><span class="sxs-lookup"><span data-stu-id="cc70a-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="cc70a-104">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cc70a-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="cc70a-105">Burada *tam-etki-türü-adı* statik üyeleri bir tür adı belirtmeden başvurulabilir türünün adı.</span><span class="sxs-lookup"><span data-stu-id="cc70a-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="cc70a-106">Tam olarak nitelenmiş tür adını (tür adı ile birlikte tam ad alanı adı) belirtmezseniz, C# Derleyici Hatası CS0246 oluşturur: "'< tür-adı >' türü veya ad alanı adı bulunamadı."</span><span class="sxs-lookup"><span data-stu-id="cc70a-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="cc70a-107">`using static` Yönergesi örnek üyelerin de sahip olsa bile statik üyeleri olan tüm türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="cc70a-108">Ancak, örnek üyeleri yalnızca türü örneği çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="cc70a-109">`using static` Yönergesi, C# 6'sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="cc70a-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc70a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc70a-110">Remarks</span></span>
 
<span data-ttu-id="cc70a-111">Normalde, statik bir üyenin çağırdığınızda, üye adı ile birlikte türü adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="cc70a-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="cc70a-112">Art arda türün üyeleri çağırmak için aynı tür adı girerek ayrıntılı, belirsiz kodda neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="cc70a-113">Örneğin, aşağıdaki tanımı bir `Circle` sınıfı üyeleri sayısı başvuran <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cc70a-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="cc70a-114">Açıkça başvuru gereğini ortadan tarafından <xref:System.Math> sınıf üyesi başvurulur, her zaman `using static` yönergesi kadar temizleyici kod üretir:</span><span class="sxs-lookup"><span data-stu-id="cc70a-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="cc70a-115">`using static` yalnızca erişilebilir statik üyeleri ve iç içe geçmiş türler belirtilen türdeki bildirilen alır.</span><span class="sxs-lookup"><span data-stu-id="cc70a-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="cc70a-116">Devralınan üyeleri içeri aktarılmadı.</span><span class="sxs-lookup"><span data-stu-id="cc70a-116">Inherited members are not imported.</span></span>  <span data-ttu-id="cc70a-117">Her adlandırılmış tür kullanarak içeri aktarabilirsiniz Visual Basic modülleri dahil statik yönergesi.</span><span class="sxs-lookup"><span data-stu-id="cc70a-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="cc70a-118">F # en üst düzey işlevleri meta verilerinde geçerli bir C# tanımlayıcı adı olan adlandırılmış bir türün statik üyeleri görünüyorsa, F # işlevleri içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="cc70a-119">`using static` uzantısı yöntemi arama için kullanılabilen belirtilen türü içinde bildirilen genişletme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc70a-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="cc70a-120">Ancak, genişletme yöntemleri adlarını kodda nitelenmemiş başvurusu için kapsam içine içeri aktarılmadı.</span><span class="sxs-lookup"><span data-stu-id="cc70a-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="cc70a-121">Farklı türler farklı tarafından alınan aynı ada sahip yöntem `using static` yönergeleri aynı derleme birim veya ad alanı form yöntemi grubu.</span><span class="sxs-lookup"><span data-stu-id="cc70a-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="cc70a-122">Bu yöntem grupları içinde aşırı yükleme çözünürlüğü normal C# kurallara uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc70a-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc70a-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc70a-123">Example</span></span>

<span data-ttu-id="cc70a-124">Aşağıdaki örnek kullanır `using static` statik üyeleri yapmak için yönergesi <xref:System.Console>, <xref:System.Math>, ve <xref:System.String> sınıfları kendi türü adını belirtmek zorunda kalmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="cc70a-125">Örnekte, `using static` yönergesi ayrıca uygulandı için <xref:System.Double> türü.</span><span class="sxs-lookup"><span data-stu-id="cc70a-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="cc70a-126">Bu çağrı mümkün yapılan <xref:System.Double.TryParse(System.String,System.Double@)> bir tür adı belirtmeden yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc70a-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="cc70a-127">Ancak, bu daha az okunabilir kod oluşturur denetlemek gerekli hale beri `using static` hangi sayısal türün belirlemek için deyimleri `TryParse` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cc70a-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc70a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc70a-128">See also</span></span>

<span data-ttu-id="cc70a-129">[using yönergesi](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="cc70a-129">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="cc70a-130">[C# başvurusu](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc70a-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="cc70a-131">[C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc70a-131">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="cc70a-132">[Ad alanlarını kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="cc70a-132">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="cc70a-133">[Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="cc70a-133">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="cc70a-134">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="cc70a-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   
