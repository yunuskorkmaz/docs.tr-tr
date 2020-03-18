---
title: statik yönergeyi kullanarak - C# Referans
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712955"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="29b2a-102">statik yönergeyi kullanarak (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="29b2a-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="29b2a-103">Yönerge, `using static` bir tür adı belirtmeden erişebileceğiniz statik üyeleri ve iç içe geçmiş türleri olan bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="29b2a-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="29b2a-104">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="29b2a-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="29b2a-105">*tam nitelikli tür adı* olan statik üyeleri ve iç içe türleri bir tür adı belirtilmeden başvurulabilir türün adıdır.</span><span class="sxs-lookup"><span data-stu-id="29b2a-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="29b2a-106">Tam nitelikli bir tür adı (tür adı ile birlikte tam ad alanı adı) sağlamazsanız, C# derleyici hatası [CS0246](../compiler-messages/cs0246.md)oluşturur : "Tür veya ad alanı adı 'type/namespace' bulunamadı (bir kullanma yönergesi veya derleme başvurusu eksik mi?)".</span><span class="sxs-lookup"><span data-stu-id="29b2a-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="29b2a-107">Yönerge, `using static` örnek üyeleri olsa bile statik üyeleri (veya iç içe geçmiş türleri) olan tüm türler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29b2a-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="29b2a-108">Ancak, örnek üyeler yalnızca tür örneği aracılığıyla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="29b2a-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="29b2a-109">Direktif `using static` C# 6'da tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="29b2a-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="29b2a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29b2a-110">Remarks</span></span>

<span data-ttu-id="29b2a-111">Normalde, statik bir üyeyi aradiğinizde, tür adını üye adı ile birlikte sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="29b2a-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="29b2a-112">Türün üyelerini çağırmak için aynı tür adı tekrar tekrar girmek ayrıntılı, belirsiz kodla sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="29b2a-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="29b2a-113">Örneğin, sınıfın `Circle` aşağıdaki tanımı sınıfın birkaç üyesine <xref:System.Math> başvurur.</span><span class="sxs-lookup"><span data-stu-id="29b2a-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="29b2a-114">Bir üyeye her başvuruda <xref:System.Math> bulunulan sınıfa açıkça başvurma `using static` gereksinimini ortadan kaldırarak, yönerge çok daha temiz bir kod üretir:</span><span class="sxs-lookup"><span data-stu-id="29b2a-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="29b2a-115">`using static`yalnızca erişilebilir statik üyeleri ve belirtilen türde bildirilen iç içe geçmiş türleri içeri alır.</span><span class="sxs-lookup"><span data-stu-id="29b2a-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="29b2a-116">Devralınan üyeler alınmaz.</span><span class="sxs-lookup"><span data-stu-id="29b2a-116">Inherited members are not imported.</span></span>  <span data-ttu-id="29b2a-117">Visual Basic modülleri de dahil olmak üzere statik yönergekullanarak herhangi bir adlandırılmış türden içe aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29b2a-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="29b2a-118">F# üst düzey işlevler meta verilerde adı geçerli bir C# tanımlayıcısı olan bir adı taşıyan bir türün statik üyeleri olarak görünürse, F# işlevleri içe aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="29b2a-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="29b2a-119">`using static`uzantı yöntemi araması için belirtilen türde bildirilen uzatma yöntemlerini yapar.</span><span class="sxs-lookup"><span data-stu-id="29b2a-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="29b2a-120">Ancak, uzantı yöntemlerinin adları kodda niteliksiz başvuru için kapsamına alınmaz.</span><span class="sxs-lookup"><span data-stu-id="29b2a-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="29b2a-121">Aynı derleme biriminde veya ad `using static` alanında farklı yönergeler tarafından farklı türlerden alınan aynı ada sahip yöntemler bir yöntem grubu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29b2a-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="29b2a-122">Bu yöntem grupları içinde aşırı yükleme çözümü normal C# kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="29b2a-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="29b2a-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="29b2a-123">Example</span></span>

<span data-ttu-id="29b2a-124">Aşağıdaki örnek, `using static` tür adlarını belirtmek zorunda <xref:System.Console> <xref:System.Math>kalmadan, , ve <xref:System.String> sınıfların statik üyelerini kullanılabilir hale getirmek için yönergeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="29b2a-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="29b2a-125">Örnekte, `using static` yönerge <xref:System.Double> türüne de uygulanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="29b2a-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="29b2a-126">Bu, bir tür adı <xref:System.Double.TryParse(System.String,System.Double@)> belirtmeden yöntemi çağırmayı mümkün kılardı.</span><span class="sxs-lookup"><span data-stu-id="29b2a-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="29b2a-127">Ancak, sayısal türün `using static` `TryParse` yönteminin çağrıldığını belirlemek için ifadeleri denetlemek gerekli hale geldiğinden, bu daha az okunabilir kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29b2a-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="29b2a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29b2a-128">See also</span></span>

- [<span data-ttu-id="29b2a-129">yönergeyi kullanarak</span><span class="sxs-lookup"><span data-stu-id="29b2a-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="29b2a-130">C# Referans</span><span class="sxs-lookup"><span data-stu-id="29b2a-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="29b2a-131">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="29b2a-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="29b2a-132">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="29b2a-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="29b2a-133">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="29b2a-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
