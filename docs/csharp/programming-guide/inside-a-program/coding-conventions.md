---
title: "C# Kodlama Kuralları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84ddc2b3cebb6bad95f5076889de11f12624b4de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="23613-102">C# Kodlama Kuralları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="23613-102">C# Coding Conventions (C# Programming Guide)</span></span>
<span data-ttu-id="23613-103">[C# dil belirtimi](http://go.microsoft.com/fwlink/?LinkId=199552) kodlama standart tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="23613-103">The [C# Language Specification](http://go.microsoft.com/fwlink/?LinkId=199552) does not define a coding standard.</span></span> <span data-ttu-id="23613-104">Ancak, bu konudaki yönergeleri, örnekler ve belgeler geliştirmek için Microsoft tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23613-104">However, the guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
 <span data-ttu-id="23613-105">Kodlama kuralları aşağıdaki amaca hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="23613-105">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="23613-106">Okuyucular içeriğine değil düzeni odaklanabilmeniz bunlar kodu tutarlı bir görünüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23613-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="23613-107">Bunlar, önceki deneyimleri temel varsayımları yaparak kodu daha hızlı bir şekilde anlaşılması okuyucular etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="23613-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="23613-108">Bunlar, kopyalama, değiştirme ve kod bakımı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="23613-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="23613-109">Bunlar, C# en iyi uygulamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="23613-109">They demonstrate C# best practices.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="23613-110">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="23613-110">Naming Conventions</span></span>  
  
-   <span data-ttu-id="23613-111">İçermeyen kısa örneklerde [yönergeleri kullanarak](../../../csharp/language-reference/keywords/using-directive.md), ad alanı nitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-111">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="23613-112">Bir ad alanı varsayılan projede alınır biliyorsanız, bu ad alanı adlarından tam olarak nitelemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="23613-112">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="23613-113">Aşağıdaki örnekte gösterildiği gibi tek bir satır için çok uzun olmaları durumunda nitelenmiş adlar bir nokta (.) sonra bozuk olabilir.</span><span class="sxs-lookup"><span data-stu-id="23613-113">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   <span data-ttu-id="23613-114">Bunları diğer yönergelerine uygun hale getirmek için Visual Studio Tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını değiştirmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="23613-114">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="23613-115">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="23613-115">Layout Conventions</span></span>  
 <span data-ttu-id="23613-116">Kodunuzu yapısını vurgulamak ve kod okunmasını kolaylaştırmak için iyi düzenini biçimlendirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="23613-116">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="23613-117">Microsoft örnekleri ve örnekler için aşağıdaki kurallara uygun:</span><span class="sxs-lookup"><span data-stu-id="23613-117">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="23613-118">Varsayılan kod düzenleyicisinde ayarları (Akıllı Girintileme, dört karakter girintileri, alanları olarak kaydedilen sekmeleri) kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-118">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="23613-119">Daha fazla bilgi için bkz: [seçenekler, metin düzenleyici, C++, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="23613-119">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="23613-120">Satır başına yalnızca bir deyim yazma.</span><span class="sxs-lookup"><span data-stu-id="23613-120">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="23613-121">Satır başına yalnızca bir bildirimini yazma.</span><span class="sxs-lookup"><span data-stu-id="23613-121">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="23613-122">Devamlılık satırlarının otomatik olarak girinti değil, bunları bir sekme durağı (dört alanları) girinti.</span><span class="sxs-lookup"><span data-stu-id="23613-122">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="23613-123">Yöntem tanımlarını ve özellik tanımları arasında en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="23613-123">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="23613-124">Yan tümceleri bir ifadede görünür, aşağıdaki kodda gösterildiği gibi yapma ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-124">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="23613-125">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="23613-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="23613-126">Kod satırının sonunda değil ayrı bir satırda açıklama yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="23613-126">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="23613-127">Açıklama metni büyük harfe ile başlar.</span><span class="sxs-lookup"><span data-stu-id="23613-127">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="23613-128">Açıklama metni noktayla bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="23613-128">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="23613-129">Açıklama sınırlayıcısı arasında bir boşluk (/ /) ve aşağıdaki örnekte gösterildiği gibi açıklama metni.</span><span class="sxs-lookup"><span data-stu-id="23613-129">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   <span data-ttu-id="23613-130">Yorumlar geçici yıldızlar biçimlendirilmiş bloklarını oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="23613-130">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="23613-131">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="23613-131">Language Guidelines</span></span>  
 <span data-ttu-id="23613-132">Aşağıdaki bölümlerde C# takım kod örnekleri ve örnekleri hazırlamak için aşağıdaki yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="23613-132">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="23613-133">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="23613-133">String Data Type</span></span>  
  
-   <span data-ttu-id="23613-134">Kullanım `+` aşağıdaki kodda gösterildiği gibi kısa dizeyi birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="23613-134">Use the `+` operator to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   <span data-ttu-id="23613-135">Özellikle büyük miktarlarda metin ile çalışırken döngüler, dizelerde eklemek için kullanın bir <xref:System.Text.StringBuilder> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="23613-135">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="23613-136">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="23613-136">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="23613-137">Kullanım [örtülü yazma](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) değişkeninin türü sağından atama veya kesin türü önemli olmadığında açık olduğunda, yerel değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="23613-137">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   <span data-ttu-id="23613-138">Kullanmayın [var](../../../csharp/language-reference/keywords/var.md) türü olmadığında atama sağ tarafında görünür.</span><span class="sxs-lookup"><span data-stu-id="23613-138">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   <span data-ttu-id="23613-139">Değişken türünü belirtmek için değişken adını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="23613-139">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="23613-140">Doğru olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="23613-140">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   <span data-ttu-id="23613-141">Kullanmaktan kaçının `var` yerine [dinamik](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="23613-141">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="23613-142">Örtük yazarak döngü değişken türünü belirlemek için kullanın [için](../../../csharp/language-reference/keywords/for.md) ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md) döngüler.</span><span class="sxs-lookup"><span data-stu-id="23613-142">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="23613-143">Aşağıdaki örnek, örtük yazarak kullanır bir `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="23613-143">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="23613-144">Aşağıdaki örnek, örtük yazarak kullanır bir `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="23613-144">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="23613-145">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="23613-145">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="23613-146">Genel olarak, kullanın `int` imzasız türler yerine.</span><span class="sxs-lookup"><span data-stu-id="23613-146">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="23613-147">Kullanımını `int` C# yaygın bir durumdur ve diğer kitaplıklarla birlikte kullandığınızda etkileşim daha kolaydır `int`.</span><span class="sxs-lookup"><span data-stu-id="23613-147">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="23613-148">Diziler</span><span class="sxs-lookup"><span data-stu-id="23613-148">Arrays</span></span>  
  
-   <span data-ttu-id="23613-149">Diziler bildirimi satırındaki başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-149">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="23613-150">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="23613-150">Delegates</span></span>  
  
-   <span data-ttu-id="23613-151">Bir temsilci türü örnekleri oluşturmak için kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-151">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="23613-152">try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="23613-152">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="23613-153">Kullanım bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) çoğu özel durum işleme için bildirimi.</span><span class="sxs-lookup"><span data-stu-id="23613-153">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   <span data-ttu-id="23613-154">C# kullanarak kodunuzu basitleştiren [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23613-154">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="23613-155">Varsa bir [try-finally](../../../csharp/language-reference/keywords/try-finally.md) hangi deyiminde yalnızca kodda `finally` blok çağrıdır <xref:System.IDisposable.Dispose%2A> yöntemi, kullanım bir `using` deyimi yerine.</span><span class="sxs-lookup"><span data-stu-id="23613-155">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="23613-156">& & ve &#124; &#124; İşleçler</span><span class="sxs-lookup"><span data-stu-id="23613-156">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="23613-157">Özel durumlar önlemek ve gereksiz karşılaştırmaları atlayarak performansı artırmak için kullanmak [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) yerine [ & ](../../../csharp/language-reference/operators/and-operator.md) ve [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) yerine [&#124;](../../../csharp/language-reference/operators/or-operator.md) gerçekleştirdiğinizde karşılaştırmaları, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="23613-157">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="23613-158">Yeni İşleç</span><span class="sxs-lookup"><span data-stu-id="23613-158">New Operator</span></span>  
  
-   <span data-ttu-id="23613-159">Nesne oluşturmada kısa biçiminde örtülü yazma ile aşağıdaki bildiriminde gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-159">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="23613-160">Önceki satıra aşağıdaki bildirimine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="23613-160">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   <span data-ttu-id="23613-161">Nesne başlatıcıları nesne oluşturma işlemini basitleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-161">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="23613-162">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="23613-162">Event Handling</span></span>  
  
-   <span data-ttu-id="23613-163">Daha sonra kaldırmanız gerekmez bir olay işleyicisi tanımlıyorsanız, lambda ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-163">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="23613-164">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="23613-164">Static Members</span></span>  
  
-   <span data-ttu-id="23613-165">Çağrı [statik](../../../csharp/language-reference/keywords/static.md) sınıf adını kullanarak üyeleri: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="23613-165">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="23613-166">Bu yöntem, temizleyin statik erişim sağlayarak kodunu daha okunabilir yapar.</span><span class="sxs-lookup"><span data-stu-id="23613-166">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="23613-167">Türetilmiş bir sınıf adı ile temel bir sınıf içinde tanımlanan statik bir üyenin uygun değil.</span><span class="sxs-lookup"><span data-stu-id="23613-167">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="23613-168">Bu kodu derlenir kodun okunabilirliğini yanıltıcı ve türetilmiş sınıf aynı ada sahip statik bir üyenin eklerseniz, kodu gelecekte kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="23613-168">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="23613-169">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="23613-169">LINQ Queries</span></span>  
  
-   <span data-ttu-id="23613-170">Sorgu değişkenleri için anlamlı adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-170">Use meaningful names for query variables.</span></span> <span data-ttu-id="23613-171">Aşağıdaki örnek kullanır `seattleCustomers` Seattle'da bulunan müşteriler için.</span><span class="sxs-lookup"><span data-stu-id="23613-171">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="23613-172">Anonim türdeki özellik adları düzgün, Pascal kullanarak olduğundan emin emin olmak için diğer adlar kullanın büyük/küçük harf.</span><span class="sxs-lookup"><span data-stu-id="23613-172">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   <span data-ttu-id="23613-173">Özellik adlarının sonuç belirsiz kullanırken özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="23613-173">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="23613-174">Sorgunuz bir müşteri adı ve bunları olarak bırakarak yerine bir dağıtıcı kimliği döndürürse, örneğin, `Name` ve `ID` sonucunda açıklamak için yeniden adlandırma `Name` bir müşteri adıdır ve `ID` dağıtıcı kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="23613-174">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   <span data-ttu-id="23613-175">Örtük sorgu değişkenleri ve aralık değişkeni bildiriminde yazarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="23613-175">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="23613-176">Sorgu yan tümceleri altında Hizala [gelen](../../../csharp/language-reference/keywords/from-clause.md) önceki örneklerde gösterildiği gibi yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="23613-176">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="23613-177">Kullanım [burada](../../../csharp/language-reference/keywords/where-clause.md) yan tümceleri sonraki sorgu yan tümceleri azaltılmış üzerinde çalışmasını sağlamak için diğer sorgu yan tümceleri önce filtrelenmiş veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="23613-177">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   <span data-ttu-id="23613-178">Birden çok kullanın `from` yan tümceleri yerine bir [birleştirme](../../../csharp/language-reference/keywords/join-clause.md) iç koleksiyonları erişmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="23613-178">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="23613-179">Örneğin, bir koleksiyonu `Student` nesneleri her içerebilir test puanları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="23613-179">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="23613-180">Aşağıdaki sorgu çalıştırıldığında, Soyadı puanı alınan Öğrenci birlikte üzerinde 90 her puan döndürür.</span><span class="sxs-lookup"><span data-stu-id="23613-180">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="23613-181">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="23613-181">Security</span></span>  
 <span data-ttu-id="23613-182">Alan yönergeleri izleyin [güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="23613-182">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23613-183">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23613-183">See Also</span></span>  
 [<span data-ttu-id="23613-184">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="23613-184">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [<span data-ttu-id="23613-185">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="23613-185">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
