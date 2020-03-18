---
title: C# Kodlama Kuralları - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399737"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="c4495-102">C# Kodlama Kuralları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c4495-102">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="c4495-103">Kodlama kuralları aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="c4495-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="c4495-104">Okuyucuların düzene değil içeriğe odaklanabilmesi için koda tutarlı bir görünüm oluştururlar.</span><span class="sxs-lookup"><span data-stu-id="c4495-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="c4495-105">Okuyucuların önceki deneyimlere dayalı varsayımlar yaparak kodu daha hızlı anlamalarını sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="c4495-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="c4495-106">Kodun kopyalanması, değiştirilmesi ve korunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c4495-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="c4495-107">C# en iyi uygulamaları gösteriyorlar.</span><span class="sxs-lookup"><span data-stu-id="c4495-107">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="c4495-108">Bu makaledeki yönergeler Microsoft tarafından örnekler ve belgeler geliştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4495-108">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="c4495-109">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="c4495-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="c4495-110">[Yönergeleri kullanmayı](../../language-reference/keywords/using-directive.md)içermeyen kısa örneklerde, ad alanı niteliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-110">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="c4495-111">Bir projede varsayılan olarak bir ad alanının alındığını biliyorsanız, bu ad alanından adları tam olarak nitelemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c4495-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="c4495-112">Aşağıdaki örnekte gösterildiği gibi, tek bir satır için çok uzunsa, nitelikli adlar bir nokta (.) sonra kırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4495-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="c4495-113">Visual Studio tasarımcı araçlarını kullanarak oluşturulan nesnelerin adlarını diğer yönergelere uygun hale getirmek için değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c4495-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="c4495-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="c4495-114">Layout Conventions</span></span>  

<span data-ttu-id="c4495-115">İyi düzen, kodunuzu vurgulamak ve kodun okunmasını kolaylaştırmak için biçimlendirmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4495-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="c4495-116">Microsoft örnekleri ve örnekleri aşağıdaki kurallara uygundur:</span><span class="sxs-lookup"><span data-stu-id="c4495-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="c4495-117">Varsayılan Kod Düzenleyicisi ayarlarını (akıllı girinti, dört karakterli girintiler, boşluk olarak kaydedilen sekmeler) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="c4495-118">Daha fazla bilgi için [seçenekler, Metin Düzenleyicisi, C#, Biçimlendirme'ye](/visualstudio/ide/reference/options-text-editor-csharp-formatting)bakın.</span><span class="sxs-lookup"><span data-stu-id="c4495-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="c4495-119">Satır başına yalnızca bir deyim yazın.</span><span class="sxs-lookup"><span data-stu-id="c4495-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="c4495-120">Satır başına yalnızca bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="c4495-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="c4495-121">Devam satırları otomatik olarak girintisi değilse, bir sekme durağı (dört boşluk) girintisi girintisi.</span><span class="sxs-lookup"><span data-stu-id="c4495-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="c4495-122">Yöntem tanımları ve özellik tanımları arasında en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4495-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="c4495-123">Aşağıdaki kodda gösterildiği gibi, bir ifadedeki yan tümceleri görünür hale getirmek için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="c4495-124">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="c4495-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="c4495-125">Yorumu kod satırının sonuna değil, ayrı bir satıra yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c4495-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="c4495-126">Açıklama metnini büyük harfle başlayın.</span><span class="sxs-lookup"><span data-stu-id="c4495-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="c4495-127">Açıklama metnini bir dönemle sonla.</span><span class="sxs-lookup"><span data-stu-id="c4495-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="c4495-128">Aşağıdaki örnekte gösterildiği gibi, açıklama delimiter (//) ile açıklama metni arasına bir boşluk ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4495-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="c4495-129">Yorumların etrafında biçimlendirilmiş yıldız taşları oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="c4495-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="c4495-130">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="c4495-130">Language Guidelines</span></span>  

<span data-ttu-id="c4495-131">Aşağıdaki bölümlerde C# ekibinin kod örnekleri ve örnekleri hazırlamak için izlediği uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4495-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="c4495-132">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c4495-132">String Data Type</span></span>  
  
- <span data-ttu-id="c4495-133">Aşağıdaki kodda gösterildiği gibi kısa dizeleri birleştirmek için [dize enterpolasyonunu](../../language-reference/tokens/interpolated.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="c4495-134">Özellikle büyük miktarda metinle çalışıyorsanız, döngüler halinde dizeleri eklemek için bir <xref:System.Text.StringBuilder> nesne kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="c4495-135">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c4495-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="c4495-136">Değişkenin türü atamanın sağ tarafından belirgin olduğunda veya kesin tür önemli olmadığında yerel değişkenler için [örtük yazma](../classes-and-structs/implicitly-typed-local-variables.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-136">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="c4495-137">Tür atamanın sağ tarafından belirgin olmadığında [var](../../language-reference/keywords/var.md) kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c4495-137">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="c4495-138">Değişkenin türünü belirtmek için değişken adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="c4495-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="c4495-139">Doğru olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c4495-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="c4495-140">[Dinamik](../../language-reference/builtin-types/reference-types.md)yerine `var` kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="c4495-140">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="c4495-141">Döngüler için döngü değişkeninin türünü belirlemek [için](../../language-reference/keywords/for.md) örtük yazıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-141">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
     <span data-ttu-id="c4495-142">Aşağıdaki örnekte bir `for` deyimde örtük yazma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4495-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- <span data-ttu-id="c4495-143">[Foreach](../../language-reference/keywords/foreach-in.md) döngülerde döngü değişkeninin türünü belirlemek için örtük yazma kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c4495-143">Do not use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

     <span data-ttu-id="c4495-144">Aşağıdaki örnekte bir `foreach` deyimde açık yazım kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4495-144">The following example uses explicit typing in a `foreach` statement.</span></span>

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > <span data-ttu-id="c4495-145">Yinelenebilir koleksiyonun bir öğesini yanlışlıkla değiştirmemeye dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c4495-145">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="c4495-146">Örneğin, sorgunun yürütülmesini <xref:System.Linq.IQueryable?displayProperty=nameWithType> değiştiren <xref:System.Collections.IEnumerable?displayProperty=nameWithType> bir `foreach` deyimde geçiş yapmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="c4495-146">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-type"></a><span data-ttu-id="c4495-147">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c4495-147">Unsigned Data Type</span></span>  
  
<span data-ttu-id="c4495-148">Genel olarak, `int` imzasız türler yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-148">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="c4495-149">Kullanımı `int` C# boyunca yaygındır ve kullandığınızda `int`diğer kitaplıklarla etkileşim kurmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="c4495-149">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="c4495-150">Diziler</span><span class="sxs-lookup"><span data-stu-id="c4495-150">Arrays</span></span>  
  
<span data-ttu-id="c4495-151">Bildirim satırındaki dizileri baş harfe aldığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-151">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="c4495-152">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c4495-152">Delegates</span></span>  
  
<span data-ttu-id="c4495-153">Temsilci türü örnekleri oluşturmak için kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-153">Use the concise syntax to create instances of a delegate type.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="c4495-154">try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c4495-154">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="c4495-155">Çoğu özel durum işleme için [try-catch](../../language-reference/keywords/try-catch.md) deyimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-155">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="c4495-156">[C# deyimini kullanarak](../../language-reference/keywords/using-statement.md)kodunuzu basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="c4495-156">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="c4495-157">Bloktaki tek kodun <xref:System.IDisposable.Dispose%2A> yönteme çağrı olduğu bir `using` [try-finally](../../language-reference/keywords/try-finally.md) deyiminiz varsa, bunun yerine bir deyim kullanın. `finally`</span><span class="sxs-lookup"><span data-stu-id="c4495-157">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="c4495-158">&& ve &#124;&#124; Operatörleri</span><span class="sxs-lookup"><span data-stu-id="c4495-158">&& and &#124;&#124; Operators</span></span>  
  
<span data-ttu-id="c4495-159">İstisnaları önlemek ve gereksiz karşılaştırmaları atlayarak [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) performansı [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) artırmak için, aşağıdaki örnekte gösterildiği gibi karşılaştırmalar yaparken [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) yerine yerine kullanın ve [&#124;&#124;.](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="c4495-159">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="c4495-160">Yeni İşleç</span><span class="sxs-lookup"><span data-stu-id="c4495-160">New Operator</span></span>  
  
- <span data-ttu-id="c4495-161">Aşağıdaki bildirimde gösterildiği gibi, örtük yazım la nesne anlık kısa formu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-161">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="c4495-162">Önceki satır aşağıdaki bildirime eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c4495-162">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="c4495-163">Nesne oluşturmayı kolaylaştırmak için nesne baş harflerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-163">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="c4495-164">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="c4495-164">Event Handling</span></span>  
  
<span data-ttu-id="c4495-165">Daha sonra kaldırmanız gerekmeyen bir olay işleyicisi tanımlıyorsanız, lambda ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-165">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="c4495-166">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="c4495-166">Static Members</span></span>  
  
<span data-ttu-id="c4495-167">Sınıf adını kullanarak [statik](../../language-reference/keywords/static.md) üyeleri arayın: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="c4495-167">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="c4495-168">Bu uygulama, statik erişimi net hale getirerek kodu daha okunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c4495-168">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="c4495-169">Taban sınıfta tanımlanan statik bir üyeyi türetilmiş sınıf adıyla nitelemayın.</span><span class="sxs-lookup"><span data-stu-id="c4495-169">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="c4495-170">Bu kod derlenirken, kod okunabilirliği yanıltıcıdır ve türemiş sınıfa aynı ada sahip statik bir üye eklerseniz kod gelecekte kırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4495-170">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="c4495-171">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="c4495-171">LINQ Queries</span></span>  
  
- <span data-ttu-id="c4495-172">Sorgu değişkenleri için anlamlı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-172">Use meaningful names for query variables.</span></span> <span data-ttu-id="c4495-173">Aşağıdaki örnek, `seattleCustomers` Seattle'da bulunan müşteriler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4495-173">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="c4495-174">Pascal kasasını kullanarak anonim türdeki özellik adlarının doğru şekilde büyük harfle yazdığından emin olmak için takma adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-174">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="c4495-175">Sonuç taki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c4495-175">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="c4495-176">Örneğin, sorgunuz bir müşteri adı ve bir distribütör kimliği `Name` döndürürse, sonuç olarak ve `ID` sonuç olarak bırakmak `ID` yerine, müşterinin adı olduğunu ve bir distribütörün kimliği olduğunu `Name` açıklığa kavuşturmak için bunları yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c4495-176">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="c4495-177">Sorgu değişkenleri ve aralık değişkenleri bildiriminde örtük yazıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-177">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="c4495-178">Önceki örneklerde gösterildiği [gibi, sorgu](../../language-reference/keywords/from-clause.md) yan tümcelerini from yan tümcesinin altında hizala.</span><span class="sxs-lookup"><span data-stu-id="c4495-178">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="c4495-179">Daha sonraki sorgu yan tümcelerinin azaltılmış, filtre uygulanmış veri kümesinde çalışmasını sağlamak için diğer sorgu yan tümcelerinden önce [nerede](../../language-reference/keywords/where-clause.md) yan tümcelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-179">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="c4495-180">İç `from` koleksiyonlara erişmek için [birleştirme](../../language-reference/keywords/join-clause.md) yan tümcesi yerine birden çok yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4495-180">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="c4495-181">Örneğin, nesnelerin bir `Student` koleksiyonu her test puanları bir koleksiyon içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c4495-181">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="c4495-182">Aşağıdaki sorgu yürütüldüğünde, 90'ın üzerindeki her puanı, puanı alan öğrencinin soyadıyla birlikte döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4495-182">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="c4495-183">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c4495-183">Security</span></span>  

<span data-ttu-id="c4495-184">Güvenli Kodlama [Yönergeleri'ndeki](../../../standard/security/secure-coding-guidelines.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c4495-184">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4495-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4495-185">See also</span></span>

- [<span data-ttu-id="c4495-186">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="c4495-186">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="c4495-187">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c4495-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
