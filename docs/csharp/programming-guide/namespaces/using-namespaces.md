---
title: Ad Boşluklarını Kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 0947e597da93d6db1c5965b3685a509961778586
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507054"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="5a3a9-102">Ad alanlarını kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5a3a9-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="5a3a9-103">Ad boşlukları C# programlarında iki şekilde yoğun olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="5a3a9-104">İlk olarak, .NET Framework sınıfları birçok sınıflarını düzenlemek için ad boşluklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="5a3a9-105">İkinci olarak, kendi ad alanlarınızı bildirmek, daha büyük programlama projelerinde sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="5a3a9-106">Ad alanlarına erişim</span><span class="sxs-lookup"><span data-stu-id="5a3a9-106">Accessing namespaces</span></span>

 <span data-ttu-id="5a3a9-107">Çoğu C# uygulaması yönergelerin `using` bir bölümüyle başlar.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="5a3a9-108">Bu bölümde, uygulamanın sık sık kullanılacağı ad alanları listelenir ve programcının içinde bulunan bir yöntemin her kullanıldığında tam nitelikli bir ad belirtilmesinden kurtarılır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="5a3a9-109">Örneğin, satırı ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="5a3a9-110">Programın başlangıcında, programcı kodu kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="5a3a9-111">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="5a3a9-112">Ad alanı takma adları</span><span class="sxs-lookup"><span data-stu-id="5a3a9-112">Namespace aliases</span></span>

 <span data-ttu-id="5a3a9-113">Ayrıca, ad alanı için bir takma ad oluşturmak için yönergeyi de kullanabilirsiniz. [ `using` ](../../language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="5a3a9-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="5a3a9-114">Diğer ad alanının üyelerine erişmek için [ad alanı diğer ad niteleyicisini `::` ](../../language-reference/operators/namespace-alias-qualifier.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="5a3a9-115">Aşağıdaki örnek, ad alanı diğer adının nasıl oluşturulup kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="5a3a9-116">Kapsamı denetlemek için ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="5a3a9-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="5a3a9-117">Anahtar `namespace` kelime bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="5a3a9-118">Projenizde kapsam oluşturma olanağı, kodun düzenlenmesine yardımcı olur ve genel olarak benzersiz türler oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="5a3a9-119">Aşağıdaki örnekte, başlıklı `SampleClass` bir sınıf, biri diğerinin iç içe olduğu iki ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="5a3a9-120">[ `.` Belirteç,](../../language-reference/operators/member-access-operators.md#member-access-expression-) hangi yöntemin çağrıldığını ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-120">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="5a3a9-121">Tam nitelikli isimler</span><span class="sxs-lookup"><span data-stu-id="5a3a9-121">Fully qualified names</span></span>

 <span data-ttu-id="5a3a9-122">Ad alanları ve türleri, mantıksal bir hiyerarşiyi gösteren tam nitelikli adlarla açıklanan benzersiz başlıklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="5a3a9-123">Örneğin, deyim, `A.B` ad `A` alanının veya türün adı `B` olduğunu ve içinde iç içe olduğunu ima eder.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="5a3a9-124">Aşağıdaki örnekte, iç içe ayrılmış sınıflar ve ad alanları vardır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="5a3a9-125">Tam nitelikli ad, her varlığı izleyen bir yorum olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="5a3a9-126">Önceki kod segmentinde:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="5a3a9-127">Ad alanı, `N1` genel ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="5a3a9-128">Onun tam nitelikli `N1`adıdır .</span><span class="sxs-lookup"><span data-stu-id="5a3a9-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="5a3a9-129">Ad alanı. `N2` `N1`</span><span class="sxs-lookup"><span data-stu-id="5a3a9-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="5a3a9-130">Onun tam nitelikli `N1.N2`adıdır .</span><span class="sxs-lookup"><span data-stu-id="5a3a9-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="5a3a9-131">`C1` Sınıf bir `N1`üyesidir.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="5a3a9-132">Onun tam nitelikli `N1.C1`adıdır .</span><span class="sxs-lookup"><span data-stu-id="5a3a9-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="5a3a9-133">Sınıf adı `C2` bu kodda iki kez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="5a3a9-134">Ancak, tam nitelikli adlar benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="5a3a9-135">İlk örneği `C2` içinde `C1`ilan edilir; bu nedenle, tam nitelikli `N1.C1.C2`adı: .</span><span class="sxs-lookup"><span data-stu-id="5a3a9-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="5a3a9-136">İkinci örnek `C2` bir ad alanı `N2`içinde bildirilir; bu nedenle, tam `N1.N2.C2`nitelikli adıdır .</span><span class="sxs-lookup"><span data-stu-id="5a3a9-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="5a3a9-137">Önceki kod kesimini kullanarak, `C3`ad alanına `N1.N2` aşağıdaki gibi yeni bir sınıf üyesi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="5a3a9-138">Genel olarak, ad alanı diğer adını başvurmak veya `global::` genel ad alanına başvurmak `.` ve türleri veya üyeleri nitelemek için [ad alanı diğer adını `::` ](../../language-reference/operators/namespace-alias-qualifier.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-138">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="5a3a9-139">Ad alanı yerine `::` bir türe başvuruyapan bir takma adla kullanmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="5a3a9-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="5a3a9-141">Sözcüğün `global` önceden tanımlanmış bir takma ad olmadığını unutmayın; bu `global.X` nedenle, herhangi bir özel anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="5a3a9-142">Sadece . `::`</span><span class="sxs-lookup"><span data-stu-id="5a3a9-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="5a3a9-143">Derleyici uyarısı CS0440, her zaman bir takma `global::` ad değil, genel ad alanına başvurulduğundan, global adlı bir takma ad tanımlarsanız oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="5a3a9-144">Örneğin, aşağıdaki satır uyarı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="5a3a9-145">Takma `::` adlarla kullanmak iyi bir fikirdir ve ek türlerin beklenmeyen girişine karşı koruma dır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="5a3a9-146">Örneğin, şu örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5a3a9-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="5a3a9-147">Bu çalışır, ancak adlandırılmış `Alias` bir tür daha `Alias.` sonra tanıtılacak olsaydı, bunun yerine bu türe bağlanır.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="5a3a9-148">Bir `Alias::Exception` ad `Alias` alanı diğer adı olarak kabul edilen ve bir türle karıştırılmayan bir sözcük kullanmak,</span><span class="sxs-lookup"><span data-stu-id="5a3a9-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="5a3a9-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a3a9-149">See also</span></span>

- [<span data-ttu-id="5a3a9-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5a3a9-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5a3a9-151">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="5a3a9-151">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="5a3a9-152">Üye erişim ifadesi</span><span class="sxs-lookup"><span data-stu-id="5a3a9-152">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="5a3a9-153">:: operatör</span><span class="sxs-lookup"><span data-stu-id="5a3a9-153">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="5a3a9-154">extern alias</span><span class="sxs-lookup"><span data-stu-id="5a3a9-154">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
