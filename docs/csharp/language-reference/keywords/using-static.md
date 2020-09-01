---
description: static yönergesini kullanma-C# başvurusu
title: static yönergesini kullanma-C# başvurusu
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: a10c315a05c28bce9b5ddb65af67dde6446d031d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141926"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="021cb-103">static yönergesini kullanma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="021cb-103">using static directive (C# Reference)</span></span>

<span data-ttu-id="021cb-104">`using static`Yönergesi statik üyeleri ve iç içe geçmiş türleri bir tür adı belirtmeden erişebileceğiniz bir türü belirler.</span><span class="sxs-lookup"><span data-stu-id="021cb-104">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="021cb-105">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="021cb-105">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="021cb-106">*tam nitelikli tür* adı, statik üyeleri ve iç içe türlerine bir tür adı belirtilmeden başvurulabilen türün adıdır.</span><span class="sxs-lookup"><span data-stu-id="021cb-106">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="021cb-107">Tam nitelikli tür adı (tür adıyla birlikte tam ad alanı adı) sağlamazsanız, C# derleyici hatası oluşturur [CS0246](../compiler-messages/cs0246.md): "tür veya ad alanı adı ' Type/Namespace ' bulunamadı (bir using yönergesi veya derleme başvurunuz eksik olabilir mi?)".</span><span class="sxs-lookup"><span data-stu-id="021cb-107">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="021cb-108">`using static`Yönergesi, örnek üyelerine de sahip olsa bile statik üyelere (veya iç içe türler) sahip her tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="021cb-108">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="021cb-109">Ancak, örnek üyeleri yalnızca tür örneği aracılığıyla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="021cb-109">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="021cb-110">`using static`Yönerge C# 6 ' da tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="021cb-110">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="021cb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="021cb-111">Remarks</span></span>

<span data-ttu-id="021cb-112">Genellikle, bir statik üye çağırdığınızda, tür adını üye adıyla birlikte sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="021cb-112">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="021cb-113">Türün üyelerini çağırmak için aynı tür adının tekrar tekrar girilmesi, ayrıntılı ve belirsiz kod oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="021cb-113">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="021cb-114">Örneğin, bir sınıfın aşağıdaki tanımı, `Circle` sınıfının bir dizi üyesine başvurur <xref:System.Math> .</span><span class="sxs-lookup"><span data-stu-id="021cb-114">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="021cb-115"><xref:System.Math>Bir üyeye her başvurulilişinde, bir sınıfa açık bir şekilde başvuruda bulunmak gereksinimini ortadan kaldırarak, `using static` yönerge çok daha Temizleyici kod üretir:</span><span class="sxs-lookup"><span data-stu-id="021cb-115">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="021cb-116">`using static` yalnızca erişilebilir statik üyeleri ve belirtilen türde tanımlanmış iç içe geçmiş türleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="021cb-116">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="021cb-117">Devralınan Üyeler içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="021cb-117">Inherited members are not imported.</span></span>  <span data-ttu-id="021cb-118">Visual Basic modüller dahil olmak üzere, bir using static yönergesi ile herhangi bir adlandırılmış türden içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="021cb-118">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="021cb-119">F # en üst düzey işlevleri meta verilerde adı geçerli bir C# tanımlayıcısı olan bir adlandırılmış türün statik üyeleri olarak görünürse, F # işlevleri içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="021cb-119">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="021cb-120">`using static` Uzantı yöntemi arama için belirtilen türde belirtilen uzantı yöntemlerini kullanılabilir yapar.</span><span class="sxs-lookup"><span data-stu-id="021cb-120">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="021cb-121">Ancak, uzantı yöntemlerinin adları kodda nitelenmemiş başvuru için kapsama aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="021cb-121">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="021cb-122">Aynı ada sahip Yöntemler `using static` aynı derleme birimi veya ad alanı içinde farklı yönergelere göre farklı türlerden içeri aktarılmalıdır bir yöntem grubu.</span><span class="sxs-lookup"><span data-stu-id="021cb-122">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="021cb-123">Bu yöntem grupları içindeki aşırı yükleme çözümlemesi normal C# kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="021cb-123">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="021cb-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="021cb-124">Example</span></span>

<span data-ttu-id="021cb-125">Aşağıdaki örnek `using static` <xref:System.Console> ,, ve sınıflarının statik üyelerini <xref:System.Math> <xref:System.String> tür adlarını belirtmeye gerek kalmadan kullanılabilir hale getirmek için yönergesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="021cb-125">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="021cb-126">Örnekte, `using static` yönergesi türüne de uygulanmış olabilir <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="021cb-126">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="021cb-127">Bu, <xref:System.Double.TryParse(System.String,System.Double@)> bir tür adı belirtmeden yöntemi çağırmak mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="021cb-127">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="021cb-128">Ancak, bu, `using static` hangi sayısal tür yönteminin çağrıldığını belirleyen yönergeleri denetlemek için gerekli hale geldiği için, daha az okunabilir bir kod oluşturur `TryParse` .</span><span class="sxs-lookup"><span data-stu-id="021cb-128">However, this creates less readable code, since it becomes necessary to check the `using static` directives to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="021cb-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="021cb-129">See also</span></span>

- [<span data-ttu-id="021cb-130">using yönergesi</span><span class="sxs-lookup"><span data-stu-id="021cb-130">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="021cb-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="021cb-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="021cb-132">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="021cb-132">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="021cb-133">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="021cb-133">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="021cb-134">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="021cb-134">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
