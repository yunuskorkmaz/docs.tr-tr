---
title: Ad alanlarını kullanma-C# Programlama Kılavuzu
description: Ad alanlarını, ad alanı diğer adlarına erişme ve kapsamı denetlemek için ad alanlarını kullanma gibi C# programlamada ad alanlarını nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 86892f50e059c16ee9c133d7ba9f2716e11a8e56
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381703"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="e61c5-103">Ad alanlarını kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e61c5-103">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="e61c5-104">Ad alanları C# programları içinde çok fazla iki şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-104">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="e61c5-105">İlk olarak, .NET sınıfları birçok sınıfını düzenlemek için ad alanlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-105">Firstly, the .NET classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="e61c5-106">İkinci olarak, kendi ad alanlarınızı bildirmek, sınıf ve yöntem adlarının kapsamını daha büyük programlama projelerinde denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e61c5-106">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="e61c5-107">Ad alanlarına erişme</span><span class="sxs-lookup"><span data-stu-id="e61c5-107">Accessing namespaces</span></span>

 <span data-ttu-id="e61c5-108">C# uygulamalarının çoğu yönergelerin bir bölümüyle başlar `using` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-108">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="e61c5-109">Bu bölüm, uygulamanın sıklıkla kullanacağı ad alanlarını listeler ve içinde yer alan bir yöntemin kullanıldığı her seferinde her defasında tam nitelikli bir ad belirtmekten tasarruf eder.</span><span class="sxs-lookup"><span data-stu-id="e61c5-109">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="e61c5-110">Örneğin, satırını dahil ederek:</span><span class="sxs-lookup"><span data-stu-id="e61c5-110">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="e61c5-111">Program başlangıcında, Programcı kodu kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="e61c5-111">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="e61c5-112">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="e61c5-112">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="e61c5-113">Ad uzayı diğer adları</span><span class="sxs-lookup"><span data-stu-id="e61c5-113">Namespace aliases</span></span>

 <span data-ttu-id="e61c5-114">Bir ad alanı için bir diğer ad oluşturmak için [ `using` yönergesini](../../language-reference/keywords/using-directive.md) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e61c5-114">You can also use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="e61c5-115">Diğer ad alanının üyelerine erişmek için [ad alanı diğer adı niteleyicisi `::` ](../../language-reference/operators/namespace-alias-qualifier.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e61c5-115">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="e61c5-116">Aşağıdaki örnek, bir ad alanı diğer adının nasıl oluşturulduğunu ve kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e61c5-116">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="e61c5-117">Kapsamı denetlemek için ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="e61c5-117">Using namespaces to control scope</span></span>

 <span data-ttu-id="e61c5-118">`namespace`Anahtar sözcüğü bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-118">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="e61c5-119">Projenizin içinde kapsam oluşturma özelliği, kodun düzenlenmesine yardımcı olur ve küresel olarak benzersiz türler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e61c5-119">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="e61c5-120">Aşağıdaki örnekte, başlıklı bir sınıf, diğeri `SampleClass` içinde iç içe iki ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-120">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="e61c5-121">[ `.` Belirteç](../../language-reference/operators/member-access-operators.md#member-access-expression-) , hangi yöntemin çağrıldığını ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-121">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="e61c5-122">Tam nitelikli adlar</span><span class="sxs-lookup"><span data-stu-id="e61c5-122">Fully qualified names</span></span>

 <span data-ttu-id="e61c5-123">Ad alanları ve türler, bir mantıksal hiyerarşiyi gösteren tam nitelikli adlarla tanımlanan benzersiz başlıklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e61c5-123">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="e61c5-124">Örneğin, ifade, `A.B` `A` ad alanının veya türün adı olduğunu ve `B` içinde iç içe geçmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e61c5-124">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="e61c5-125">Aşağıdaki örnekte, iç içe geçmiş sınıflar ve ad alanları vardır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-125">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="e61c5-126">Tam nitelikli ad her bir varlıktan sonra bir yorum olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e61c5-126">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="e61c5-127">Önceki kod segmentinde:</span><span class="sxs-lookup"><span data-stu-id="e61c5-127">In the previous code segment:</span></span>  
  
- <span data-ttu-id="e61c5-128">Ad alanı, `N1` genel ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="e61c5-128">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="e61c5-129">Tam nitelikli adı `N1` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-129">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="e61c5-130">Ad alanı `N2` bir üyesidir `N1` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-130">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="e61c5-131">Tam nitelikli adı `N1.N2` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-131">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="e61c5-132">Sınıfı `C1` öğesinin üyesidir `N1` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-132">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="e61c5-133">Tam nitelikli adı `N1.C1` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-133">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="e61c5-134">Sınıf adı `C2` Bu kodda iki kez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-134">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="e61c5-135">Ancak, tam nitelikli adlar benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="e61c5-135">However, the fully qualified names are unique.</span></span> <span data-ttu-id="e61c5-136">İlk örneği içinde, `C2` `C1` Bu nedenle tam adı: `N1.C1.C2` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-136">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="e61c5-137">İkinci örneği `C2` bir ad alanı içinde bildirilmiştir `N2` ; Bu nedenle tam adı ' dir `N1.N2.C2` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-137">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="e61c5-138">Önceki kod segmentini kullanarak, ad alanına yeni bir sınıf üyesini `C3` `N1.N2` aşağıdaki şekilde ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e61c5-138">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="e61c5-139">Genel olarak, ad alanı diğer adına başvurmak için ad [alanı diğer adı niteleyicisi `::` ](../../language-reference/operators/namespace-alias-qualifier.md) kullanın veya `global::` genel ad alanına başvurmak ve `.` türleri veya üyeleri nitelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e61c5-139">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="e61c5-140">`::`Ad alanı yerine bir türe başvuran diğer adla birlikte kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-140">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="e61c5-141">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e61c5-141">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="e61c5-142">Sözcüğün `global` önceden tanımlanmış bir diğer ad olmadığını unutmayın; bu nedenle, `global.X` özel bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="e61c5-142">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="e61c5-143">Yalnızca ile kullanıldığında özel bir anlam elde edin `::` .</span><span class="sxs-lookup"><span data-stu-id="e61c5-143">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="e61c5-144">Bir diğer ad `global::` değil genel ad alanına başvurduğu için, genel adlı bir diğer ad tanımlarsanız derleyici uyarısı CS0440 oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e61c5-144">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="e61c5-145">Örneğin, aşağıdaki satır uyarı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e61c5-145">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="e61c5-146">`::`Diğer adlarla kullanmak iyi bir fikirdir ve ek türlerin beklenmedik şekilde tanıtılmasıyla karşı koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e61c5-146">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="e61c5-147">Örneğin, şu örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e61c5-147">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="e61c5-148">Bu işe yarar, ancak adlandırılmış bir tür `Alias` daha sonra tanıtılmışsa, `Alias.` bunun yerine bu türe bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e61c5-148">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="e61c5-149">Kullanmak `Alias::Exception` , bir `Alias` ad alanı diğer adı olarak değerlendirilip bir tür için hatalı alınmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e61c5-149">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e61c5-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e61c5-150">See also</span></span>

- [<span data-ttu-id="e61c5-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e61c5-151">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e61c5-152">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="e61c5-152">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="e61c5-153">Üye erişim ifadesi</span><span class="sxs-lookup"><span data-stu-id="e61c5-153">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="e61c5-154">:: işleci</span><span class="sxs-lookup"><span data-stu-id="e61c5-154">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="e61c5-155">extern alias</span><span class="sxs-lookup"><span data-stu-id="e61c5-155">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
