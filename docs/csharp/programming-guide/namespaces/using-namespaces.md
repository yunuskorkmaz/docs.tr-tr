---
title: Ad alanlarını - kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: bb491ef93f0f2da89f0101d10e2cf3d158962850
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423299"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="4efd1-102">Ad Alanlarını Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4efd1-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="4efd1-103">Ad alanlarında, C# programları iki yolla içinde yoğun olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4efd1-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="4efd1-104">İlk olarak, .NET Framework sınıfları ad alanları, çok sayıda sınıfa düzenlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4efd1-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="4efd1-105">İkincisi, kendi ad alanlarını bildirme denetimi sınıf ve metod kapsamını daha büyük programlama projelerinde adları yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4efd1-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="4efd1-106">Ad alanları erişme</span><span class="sxs-lookup"><span data-stu-id="4efd1-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="4efd1-107">Çoğu C# uygulama bölümü ile başlayan `using` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="4efd1-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="4efd1-108">Bu bölümde, uygulama sık sık kullanacağınız ve içinde yer alan bir yöntem kullanılır her zaman tamamen nitelikli ada belirtmelerini Programcı kaydeder ad alanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="4efd1-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="4efd1-109">Örneğin, satır dahil ederek:</span><span class="sxs-lookup"><span data-stu-id="4efd1-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="4efd1-110">Bir program başlangıcında, programcılar kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4efd1-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="4efd1-111">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="4efd1-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="4efd1-112">Namespace diğer adları</span><span class="sxs-lookup"><span data-stu-id="4efd1-112">Namespace Aliases</span></span>  
 <span data-ttu-id="4efd1-113">[Using yönergesi](../../../csharp/language-reference/keywords/using-directive.md) için bir diğer ad oluşturmak için de kullanılabilir bir [ad alanı](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="4efd1-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="4efd1-114">Örneğin, iç içe ad alanlarını içeren önceden yazılmış bir ad alanı kullanıyorsanız, aşağıdaki örnekte olduğu gibi bir özellikle, başvuru toplu bir yol sağlamak üzere bir diğer ad bildirmek isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4efd1-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="4efd1-115">Denetim kapsamı ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="4efd1-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="4efd1-116">`namespace` Anahtar sözcüğü bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4efd1-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="4efd1-117">Projenizi kapsamlarda oluşturma olanağı kodunu düzenlemenize yardımcı olur ve genel olarak benzersiz türleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4efd1-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="4efd1-118">Aşağıdaki örnekte, bir sınıf başlıklı `SampleClass` bir diğer içinde iç içe iki ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4efd1-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="4efd1-119">[Üye erişimi `.` işleci](../../language-reference/operators/member-access-operators.md#member-access-operator-) hangi yöntemi çağrıldığında ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4efd1-119">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="4efd1-120">Tam olarak nitelenmiş adlar</span><span class="sxs-lookup"><span data-stu-id="4efd1-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="4efd1-121">Ad alanları ve türler, mantıksal bir hiyerarşi gösteren tam olarak nitelenmiş adlar tarafından açıklanan benzersiz başlıkları sahip.</span><span class="sxs-lookup"><span data-stu-id="4efd1-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="4efd1-122">Örneğin, deyim `A.B` , gelir `A` ad alanı veya tür, adıdır ve `B` içinde iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="4efd1-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="4efd1-123">Aşağıdaki örnekte, iç içe geçmiş sınıflar ve ad alanları vardır.</span><span class="sxs-lookup"><span data-stu-id="4efd1-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="4efd1-124">Tam adı, her varlık aşağıdaki açıklama olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4efd1-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="4efd1-125">Önceki kod kesimi içinde:</span><span class="sxs-lookup"><span data-stu-id="4efd1-125">In the previous code segment:</span></span>  
  
- <span data-ttu-id="4efd1-126">Ad alanı `N1` genel ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="4efd1-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="4efd1-127">Tam olarak nitelenmiş adını `N1`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-127">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="4efd1-128">Ad alanı `N2` üyesi `N1`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="4efd1-129">Tam olarak nitelenmiş adını `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-129">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="4efd1-130">Sınıf `C1` üyesi `N1`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="4efd1-131">Tam olarak nitelenmiş adını `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-131">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="4efd1-132">Sınıf adı `C2` iki kez bu kodda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4efd1-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="4efd1-133">Ancak, tam nitelikli adları benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="4efd1-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="4efd1-134">İlk örneğinin `C2` içinde bildirilen `C1`; bu nedenle, tam ad: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="4efd1-135">İkinci bir örneğini `C2` bir ad alanı içinde bildirilen `N2`; bu nedenle, tam olarak nitelenmiş adını `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="4efd1-136">Önceki kod kesimi kullanarak yeni bir sınıf üyesi ekleyebilirsiniz `C3`, ad alanına `N1.N2` gibi:</span><span class="sxs-lookup"><span data-stu-id="4efd1-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="4efd1-137">Genel olarak, kullanın `::` ad alanı diğer ada başvuru yapmak veya `global::` genel ad başvurmak için ve `.` türleri veya üyeleri nitelemek için.</span><span class="sxs-lookup"><span data-stu-id="4efd1-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="4efd1-138">Kullanılacak bir hata olduğunu `::` bir ad alanı yerine bir türe başvuran bir takma ad ile.</span><span class="sxs-lookup"><span data-stu-id="4efd1-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="4efd1-139">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4efd1-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="4efd1-140">Unutmayın word `global` önceden tanımlanmış bir değil diğer adı; bu nedenle `global.X` özel bir anlamı yok.</span><span class="sxs-lookup"><span data-stu-id="4efd1-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="4efd1-141">Yalnızca ile kullanıldığında, özel bir anlamı edinme `::`.</span><span class="sxs-lookup"><span data-stu-id="4efd1-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="4efd1-142">Bir diğer ad tanımlarsanız CS0440 oluşturulan uyarı derleyici adlı genel çünkü `global::` her zaman genel ad ve bir diğer başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="4efd1-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="4efd1-143">Örneğin, aşağıdaki satırı uyarıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4efd1-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="4efd1-144">Kullanarak `::` diğer adları ile iyi bir uygulamadır ve ek türleri beklenmeyen giriş karşı korur.</span><span class="sxs-lookup"><span data-stu-id="4efd1-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="4efd1-145">Örneğin, bu örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4efd1-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="4efd1-146">Adlı bir tür, ancak bu, çalışan `Alias` sonradan tanıtılmak üzere olduğunuz `Alias.` bunun yerine o türüne bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4efd1-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="4efd1-147">Kullanarak `Alias::Exception` , oluşturmasını sağlar `Alias` bir ad alanı diğer ad olarak kabul edilir ve mistaken için bir tür değil.</span><span class="sxs-lookup"><span data-stu-id="4efd1-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="4efd1-148">Konusuna [nasıl yapılır: Genel Namespace diğer adlarını kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) daha fazla bilgi için ilgili `global` diğer adı.</span><span class="sxs-lookup"><span data-stu-id="4efd1-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4efd1-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4efd1-149">See also</span></span>

- [<span data-ttu-id="4efd1-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4efd1-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4efd1-151">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="4efd1-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="4efd1-152">. İşleç</span><span class="sxs-lookup"><span data-stu-id="4efd1-152">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="4efd1-153">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="4efd1-153">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="4efd1-154">extern</span><span class="sxs-lookup"><span data-stu-id="4efd1-154">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
