---
title: statik yönerge kullanma- C# başvuru
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 1a0e26d8b0a14e0c77b724fc492588e08762e47f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099993"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="42859-102">static yönergesini kullanma (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="42859-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="42859-103">`using static` yönergesi statik üyeleri ve iç içe geçmiş türleri bir tür adı belirtmeden erişebileceğiniz bir türü belirler.</span><span class="sxs-lookup"><span data-stu-id="42859-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="42859-104">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="42859-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="42859-105">*tam nitelikli tür* adı, statik üyeleri ve iç içe türlerine bir tür adı belirtilmeden başvurulabilen türün adıdır.</span><span class="sxs-lookup"><span data-stu-id="42859-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="42859-106">Tam nitelikli tür adı (tür adıyla birlikte tam ad alanı adı) sağlamazsanız, C# derleyici hatası oluşturur [CS0246](../compiler-messages/cs0246.md): "tür veya ad alanı adı ' Type/Namespace ' bulunamadı (bir using yönergeniz veya bir bütünleştirilmiş kod eksik olabilir başvuru?) ".</span><span class="sxs-lookup"><span data-stu-id="42859-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="42859-107">`using static` yönergesi, örnek üyelerine de sahip olsa bile statik üyelere (veya iç içe türler) sahip her tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="42859-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="42859-108">Ancak, örnek üyeleri yalnızca tür örneği aracılığıyla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="42859-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="42859-109">`using static` yönergesi 6 ' da C# sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="42859-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="42859-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42859-110">Remarks</span></span>

<span data-ttu-id="42859-111">Genellikle, bir statik üye çağırdığınızda, tür adını üye adıyla birlikte sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="42859-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="42859-112">Türün üyelerini çağırmak için aynı tür adının tekrar tekrar girilmesi, ayrıntılı ve belirsiz kod oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="42859-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="42859-113">Örneğin, bir `Circle` sınıfının aşağıdaki tanımı <xref:System.Math> sınıfının bir dizi üyesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="42859-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="42859-114">Bir üyeye her başvurulilişinde <xref:System.Math> sınıfına açıkça başvuru ihtiyacını ortadan kaldırarak `using static` yönergesi çok Temizleyici kod üretir:</span><span class="sxs-lookup"><span data-stu-id="42859-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="42859-115">`using static`, yalnızca erişilebilir statik üyeleri ve belirtilen türde tanımlanan iç içe geçmiş türleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="42859-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="42859-116">Devralınan Üyeler içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="42859-116">Inherited members are not imported.</span></span>  <span data-ttu-id="42859-117">Visual Basic modüller dahil olmak üzere, bir using static yönergesi ile herhangi bir adlandırılmış türden içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42859-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="42859-118">F# Üst düzey işlevler, adı geçerli C# bir tanımlayıcı olan adlandırılmış türün statik üyeleri olarak meta verilerde görünürse, F# işlevler içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="42859-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="42859-119">`using static`, belirtilen türde tanımlanan uzantı yöntemlerinin genişletme yöntemi araması için kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="42859-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="42859-120">Ancak, uzantı yöntemlerinin adları kodda nitelenmemiş başvuru için kapsama aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="42859-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="42859-121">Aynı ada sahip Yöntemler aynı derleme birimi veya ad alanı içinde farklı `using static` yönergeleri tarafından bir yöntem grubu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42859-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="42859-122">Bu yöntem grupları içindeki aşırı yükleme çözümlemesi normal C# kuralları izler.</span><span class="sxs-lookup"><span data-stu-id="42859-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="42859-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="42859-123">Example</span></span>

<span data-ttu-id="42859-124">Aşağıdaki örnek, <xref:System.Console>, <xref:System.Math>ve <xref:System.String> sınıflarının statik üyelerini tür adlarını belirtmek zorunda kalmadan kullanılabilir hale getirmek için `using static` yönergesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="42859-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="42859-125">Örnekte, `using static` yönergesi <xref:System.Double> türüne de uygulanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="42859-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="42859-126">Bu, bir tür adı belirtmeden <xref:System.Double.TryParse(System.String,System.Double@)> yöntemini çağırmak mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="42859-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="42859-127">Ancak, bu, hangi sayısal tür `TryParse` yönteminin çağrıldığını belirleyen `using static` deyimlerini denetlemek için gerekli hale geldiği için, daha az okunabilir bir kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42859-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="42859-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42859-128">See also</span></span>

- [<span data-ttu-id="42859-129">using yönergesi</span><span class="sxs-lookup"><span data-stu-id="42859-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="42859-130">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="42859-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="42859-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="42859-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="42859-132">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="42859-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="42859-133">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="42859-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
