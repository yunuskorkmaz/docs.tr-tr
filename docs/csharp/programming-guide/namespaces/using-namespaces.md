---
title: Ad alanlarını kullanma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 32e36a3ebc0de3e5f4a850e0af0261c1e7fd5a07
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039467"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="4b2e1-102">Ad alanlarını kullanmaC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4b2e1-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="4b2e1-103">Ad alanları programlar içinde C# yoğun olarak iki şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="4b2e1-104">İlk olarak, .NET Framework sınıfları, birçok sınıfını düzenlemek için ad alanlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="4b2e1-105">İkinci olarak, kendi ad alanlarınızı bildirmek, sınıf ve yöntem adlarının kapsamını daha büyük programlama projelerinde denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="4b2e1-106">Ad alanlarına erişme</span><span class="sxs-lookup"><span data-stu-id="4b2e1-106">Accessing namespaces</span></span>

 <span data-ttu-id="4b2e1-107">Çoğu C# uygulama, `using` yönergelerin bir bölümüyle başlar.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="4b2e1-108">Bu bölüm, uygulamanın sıklıkla kullanacağı ad alanlarını listeler ve içinde yer alan bir yöntemin kullanıldığı her seferinde her defasında tam nitelikli bir ad belirtmekten tasarruf eder.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="4b2e1-109">Örneğin, satırını dahil ederek:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="4b2e1-110">Program başlangıcında, Programcı kodu kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="4b2e1-111">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="4b2e1-112">Ad uzayı diğer adları</span><span class="sxs-lookup"><span data-stu-id="4b2e1-112">Namespace aliases</span></span>

 <span data-ttu-id="4b2e1-113">Bir ad alanı için bir diğer ad oluşturmak için [ `using` yönergesini](../../language-reference/keywords/using-directive.md) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="4b2e1-114">Diğer ad alanının üyelerine erişmek için [ad alanı diğer `::` adı niteleyicisi](../../language-reference/operators/namespace-alias-qualifier.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="4b2e1-115">Aşağıdaki örnek, bir ad alanı diğer adının nasıl oluşturulduğunu ve kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="4b2e1-116">Kapsamı denetlemek için ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="4b2e1-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="4b2e1-117">`namespace` Anahtar sözcüğü bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="4b2e1-118">Projenizin içinde kapsam oluşturma özelliği, kodun düzenlenmesine yardımcı olur ve küresel olarak benzersiz türler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="4b2e1-119">Aşağıdaki örnekte, başlıklı `SampleClass` bir sınıf, diğeri içinde iç içe iki ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="4b2e1-120">[ `.` Üye erişim işleci](../../language-reference/operators/member-access-operators.md#member-access-operator-) , hangi yöntemin çağracağını ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-120">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="4b2e1-121">Tam nitelikli adlar</span><span class="sxs-lookup"><span data-stu-id="4b2e1-121">Fully qualified names</span></span>

 <span data-ttu-id="4b2e1-122">Ad alanları ve türler, bir mantıksal hiyerarşiyi gösteren tam nitelikli adlarla tanımlanan benzersiz başlıklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="4b2e1-123">Örneğin, ifade `A.B` , ad alanının veya `A` türün adı olduğunu ve `B` içinde iç içe geçmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="4b2e1-124">Aşağıdaki örnekte, iç içe geçmiş sınıflar ve ad alanları vardır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="4b2e1-125">Tam nitelikli ad her bir varlıktan sonra bir yorum olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="4b2e1-126">Önceki kod segmentinde:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="4b2e1-127">Ad alanı `N1` , genel ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="4b2e1-128">Tam nitelikli adı `N1`.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="4b2e1-129">Ad alanı `N2` bir `N1`üyesidir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="4b2e1-130">Tam nitelikli adı `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="4b2e1-131">Sınıfı `C1` öğesinin`N1`üyesidir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="4b2e1-132">Tam nitelikli adı `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="4b2e1-133">Sınıf adı `C2` Bu kodda iki kez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="4b2e1-134">Ancak, tam nitelikli adlar benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="4b2e1-135">İlk örneği `C2` içinde `C1`, bu nedenle tam adı: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="4b2e1-136">İkinci örneği `C2` bir ad alanı `N2`içinde bildirilmiştir; bu nedenle tam adı ' dir `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="4b2e1-137">Önceki kod segmentini kullanarak, ad alanına `C3` `N1.N2` yeni bir sınıf üyesini aşağıdaki şekilde ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="4b2e1-138">Genel olarak, ad alanı diğer adına başvurmak için ad [alanı diğer `::` ](../../language-reference/operators/namespace-alias-qualifier.md) adı niteleyicisi `global::` kullanın veya genel ad alanına başvurmak `.` ve türleri veya üyeleri nitelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-138">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="4b2e1-139">Ad alanı yerine bir türe başvuran `::` diğer adla birlikte kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="4b2e1-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="4b2e1-141">Sözcüğün `global` önceden tanımlanmış bir diğer ad olmadığını unutmayın; bu nedenle, `global.X` özel bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="4b2e1-142">Yalnızca ile `::`kullanıldığında özel bir anlam elde edin.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="4b2e1-143">Bir diğer ad değil genel ad alanına başvurduğu için, genel `global::` adlı bir diğer ad tanımlarsanız derleyici uyarısı CS0440 oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="4b2e1-144">Örneğin, aşağıdaki satır uyarı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="4b2e1-145">Diğer `::` adlarla kullanmak iyi bir fikirdir ve ek türlerin beklenmedik şekilde tanıtılmasıyla karşı koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="4b2e1-146">Örneğin, şu örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4b2e1-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="4b2e1-147">Bu işe yarar, ancak adlandırılmış `Alias` bir tür daha sonra tanıtılmışsa, `Alias.` bunun yerine bu türe bağlanır.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="4b2e1-148">Kullanmak `Alias::Exception` `Alias` , bir ad alanı diğer adı olarak değerlendirilip bir tür için hatalı alınmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4b2e1-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b2e1-149">See also</span></span>

- [<span data-ttu-id="4b2e1-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4b2e1-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4b2e1-151">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="4b2e1-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="4b2e1-152">. işlecinde</span><span class="sxs-lookup"><span data-stu-id="4b2e1-152">. operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="4b2e1-153">:: işleci</span><span class="sxs-lookup"><span data-stu-id="4b2e1-153">:: operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="4b2e1-154">extern diğer adı</span><span class="sxs-lookup"><span data-stu-id="4b2e1-154">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
