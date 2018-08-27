---
title: using static yönergesi (C# Başvurusu)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e7368a6b6a4453f2dd07c7afdc0bffa7473ed1
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929684"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="49476-102">using static yönergesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="49476-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="49476-103">`using static` Yönergesi, statik üyeleri ve iç içe geçmiş türler erişebileceğiniz bir tür adı belirtmeden bir tür belirler.</span><span class="sxs-lookup"><span data-stu-id="49476-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="49476-104">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="49476-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="49476-105">Burada *tam olarak nitelenmiş-tür adı* türün statik üyeleri adıdır ve iç içe geçmiş türler, tür adı belirtmeden başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="49476-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="49476-106">Tam olarak nitelenmiş tür adını (tam ad alanı adı tür adıyla birlikte) sağlamazsanız, C# derleyici hatası oluşturur [CS0246](../compiler-messages/cs0246.md): "' türü/ad alanı' tür veya ad alanı adı bulunamadı (bir using eksik yönergesi veya derleme başvurunuz?) ".</span><span class="sxs-lookup"><span data-stu-id="49476-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="49476-107">`using static` Yönergesi Ayrıca örnek üyeleri sahip olsa bile statik üyeler (veya iç içe geçmiş türler) olan herhangi bir türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="49476-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="49476-108">Ancak, örnek üyeleri yalnızca tür örneği çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="49476-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="49476-109">`using static` Yönergesi, C# 6'da sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="49476-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="49476-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49476-110">Remarks</span></span>
 
<span data-ttu-id="49476-111">Normalde, bir statik üye çağırdığınızda, üye adıyla birlikte tür adı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="49476-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="49476-112">Art arda türün üyeleri çağırmak için aynı tür adı girerek, ayrıntılı, belirsiz kodu neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="49476-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="49476-113">Örneğin, aşağıdaki tanımını bir `Circle` sınıfına başvuran bir dizi üyeleri <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49476-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="49476-114">Açıkça başvuru gereksinimini ortadan kaldıran tarafından <xref:System.Math> sınıf üyesi başvuruluyor, her zaman `using static` yönergesi çok daha temiz bir kod üretir:</span><span class="sxs-lookup"><span data-stu-id="49476-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="49476-115">`using static` yalnızca erişilebilir statik üyeleri ve belirtilen türde bildirilen iç içe geçmiş türleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="49476-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="49476-116">Devralınan üyeleri içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="49476-116">Inherited members are not imported.</span></span>  <span data-ttu-id="49476-117">Kullanarak herhangi bir adlandırılmış tür içeri aktarabileceğiniz static yönergesi, Visual Basic modülleri dahil.</span><span class="sxs-lookup"><span data-stu-id="49476-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="49476-118">F # en üst düzey işlev meta verilerinde geçerli bir C# tanımlayıcı adı olan adlandırılmış bir türün statik üyeleri görünüyorsa, F # işlevleri içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="49476-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="49476-119">`using static` Uzantı yöntemi araması için kullanılabilen belirtilen türde bildirilen genişletme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="49476-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="49476-120">Ancak, genişletme yöntemleri adlarını nitelenmemiş bir başvuru kod kapsama içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="49476-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="49476-121">Farklı türlerden farklı tarafından alınan aynı ada sahip yöntem `using static` yönergeleri aynı derleme biriminde veya ad alanı bir yöntem grubu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="49476-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="49476-122">Bu yöntem grupları aşırı yükleme çözünürlüğüne normal C# kurallara uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="49476-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49476-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="49476-123">Example</span></span>

<span data-ttu-id="49476-124">Aşağıdaki örnekte `using static` statik üyelerinden birini yapmak için yönergesi <xref:System.Console>, <xref:System.Math>, ve <xref:System.String> sınıflarının kendi tür adını belirtmenize gerek kalmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="49476-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="49476-125">Örnekte, `using static` yönergesi ayrıca uygulanıp uygulanmadığını için <xref:System.Double> türü.</span><span class="sxs-lookup"><span data-stu-id="49476-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="49476-126">Bu, çağrılabilir alacağımızdı <xref:System.Double.TryParse(System.String,System.Double@)> türü adı belirtilmeden yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49476-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="49476-127">Ancak, bu daha okunabilir bir kod oluşturur denetlemek gerekli hale beri `using static` hangi sayısal türün belirlemek için ifadeleri `TryParse` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="49476-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="49476-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49476-128">See also</span></span>

- [<span data-ttu-id="49476-129">using yönergesi</span><span class="sxs-lookup"><span data-stu-id="49476-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="49476-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="49476-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="49476-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="49476-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="49476-132">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="49476-132">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="49476-133">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="49476-133">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [<span data-ttu-id="49476-134">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="49476-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
