---
title: C# kodlama kuralları-C# Programlama Kılavuzu
description: C# ' de kodlama kuralları hakkında bilgi edinin. Kodlama kuralları koda tutarlı bir görünüm oluşturur ve kodun kopyalanmasını, değiştirilmesini ve bakımının yapılmasını kolaylaştırır.
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 772aebff0b8c7aebe7c7d5c7634cd2931f4570b1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301859"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="2256d-104">C# Kodlama Kuralları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2256d-104">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="2256d-105">Kodlama kuralları aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="2256d-105">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="2256d-106">Bunlar, koda tutarlı bir görünüm oluşturur, böylece okuyucular düzene göre değil, içeriğe odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="2256d-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="2256d-107">Bu kullanıcılar, önceki deneyimle dayalı varsayımlar yaparak okuyucuların kodu daha hızlı anlamasına imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="2256d-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="2256d-108">Kodu kopyalama, değiştirme ve sürdürme işlemlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2256d-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="2256d-109">C# En Iyi yöntemlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2256d-109">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="2256d-110">Bu makaledeki yönergeler, Microsoft tarafından örnek ve belge geliştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2256d-110">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="2256d-111">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="2256d-111">Naming Conventions</span></span>  
  
- <span data-ttu-id="2256d-112">[Using yönergeleri](../../language-reference/keywords/using-directive.md)dahil olmayan kısa örneklerde ad alanı nitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-112">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="2256d-113">Bir ad alanının bir projede varsayılan olarak içeri aktarıldığını biliyorsanız, adları bu ad alanından tam olarak nitelemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2256d-113">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="2256d-114">Nitelenmiş adlar, aşağıdaki örnekte gösterildiği gibi, tek bir satırda çok uzunsa bir nokta (.) sonrasında bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="2256d-114">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="2256d-115">Visual Studio tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını, diğer yönergelere uyum sağlamak için değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2256d-115">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="2256d-116">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="2256d-116">Layout Conventions</span></span>  

<span data-ttu-id="2256d-117">İyi düzen, kodunuzun yapısını vurgulamak ve kodun daha kolay okunmasını sağlamak için biçimlendirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="2256d-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="2256d-118">Microsoft örnekleri ve örnekleri aşağıdaki kurallara uygun şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="2256d-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="2256d-119">Varsayılan kod Düzenleyicisi ayarlarını (akıllı girintileme, dört karakterlik girintiler, sekmeler boşluk olarak kaydedilir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="2256d-120">Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici, C#, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="2256d-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="2256d-121">Her satırda yalnızca bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="2256d-121">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="2256d-122">Her satırda yalnızca bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="2256d-122">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="2256d-123">Devamlılık satırları otomatik olarak girintili değilse, bir sekme durağı (dört boşluk) için girinti yapın.</span><span class="sxs-lookup"><span data-stu-id="2256d-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="2256d-124">Yöntem tanımları ve özellik tanımları arasına en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2256d-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="2256d-125">Aşağıdaki kodda gösterildiği gibi, bir ifadedeki tümceleri görünür hale getirmek için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="2256d-126">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="2256d-126">Commenting Conventions</span></span>  
  
- <span data-ttu-id="2256d-127">Yorumu bir kod satırının sonuna değil, ayrı bir satıra yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="2256d-127">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="2256d-128">Açıklama metnini büyük harfle Başlat.</span><span class="sxs-lookup"><span data-stu-id="2256d-128">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="2256d-129">Açıklama metnini noktayla bitirin.</span><span class="sxs-lookup"><span data-stu-id="2256d-129">End comment text with a period.</span></span>  
  
- <span data-ttu-id="2256d-130">Aşağıdaki örnekte gösterildiği gibi açıklama sınırlayıcısı (//) ve açıklama metni arasına bir boşluk ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2256d-130">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="2256d-131">Açıklamaların etrafında, biçimli yıldız işaretleri oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="2256d-131">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="2256d-132">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="2256d-132">Language Guidelines</span></span>  

<span data-ttu-id="2256d-133">Aşağıdaki bölümlerde, C# ekibinin kod örneklerini ve örnekleri hazırlamak için izlediği uygulamalar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2256d-133">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="2256d-134">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2256d-134">String Data Type</span></span>  
  
- <span data-ttu-id="2256d-135">Aşağıdaki kodda gösterildiği gibi, kısa dizeleri birleştirmek için [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-135">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="2256d-136">Özellikle büyük miktarlarda metinle çalışırken, Döngülerde dizeler eklemek için bir <xref:System.Text.StringBuilder> nesnesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-136">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="2256d-137">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2256d-137">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="2256d-138">Değişkenin türü atamanın sağ tarafından açık olduğunda veya kesin tür önemli olmadığında yerel değişkenler için [örtülü yazma](../classes-and-structs/implicitly-typed-local-variables.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-138">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="2256d-139">Tür atamanın sağ tarafından görünmüyorsa, [yok kullanmayın.](../../language-reference/keywords/var.md)</span><span class="sxs-lookup"><span data-stu-id="2256d-139">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="2256d-140">Değişkenin türünü belirtmek için değişken adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="2256d-140">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="2256d-141">Doğru olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2256d-141">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="2256d-142">Dinamik yerine kullanılmasını önleyin `var` . [dynamic](../../language-reference/builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="2256d-142">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="2256d-143">Döngülerde içindeki döngü değişkeninin türünü [öğrenmek için örtük](../../language-reference/keywords/for.md) yazma kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-143">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
     <span data-ttu-id="2256d-144">Aşağıdaki örnek, bir bildiriminde örtük yazma kullanır `for` .</span><span class="sxs-lookup"><span data-stu-id="2256d-144">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- <span data-ttu-id="2256d-145">[Foreach](../../language-reference/keywords/foreach-in.md) Döngülerde döngü değişkeninin türünü öğrenmek için örtük yazma kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2256d-145">Do not use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

     <span data-ttu-id="2256d-146">Aşağıdaki örnek, bir bildiriminde açık bir yazma kullanır `foreach` .</span><span class="sxs-lookup"><span data-stu-id="2256d-146">The following example uses explicit typing in a `foreach` statement.</span></span>

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > <span data-ttu-id="2256d-147">Yinelenebilir bir koleksiyonun öğe türünü yanlışlıkla değiştirmemeye dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2256d-147">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="2256d-148">Örneğin, bir <xref:System.Linq.IQueryable?displayProperty=nameWithType> <xref:System.Collections.IEnumerable?displayProperty=nameWithType> sorgunun yürütülmesini değiştiren bir ifadede öğesine geçiş yapmak kolaydır `foreach` .</span><span class="sxs-lookup"><span data-stu-id="2256d-148">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-type"></a><span data-ttu-id="2256d-149">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2256d-149">Unsigned Data Type</span></span>  
  
<span data-ttu-id="2256d-150">Genel olarak, `int` imzasız türler yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-150">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="2256d-151">Kullanımı `int` C# ' nin tamamında ortaktır ve kullandığınızda diğer kitaplıklarla etkileşim kurmak daha kolaydır `int` .</span><span class="sxs-lookup"><span data-stu-id="2256d-151">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="2256d-152">Diziler</span><span class="sxs-lookup"><span data-stu-id="2256d-152">Arrays</span></span>  
  
<span data-ttu-id="2256d-153">Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-153">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="2256d-154">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="2256d-154">Delegates</span></span>  
  
<span data-ttu-id="2256d-155">Bir temsilci türünün örneklerini oluşturmak için kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-155">Use the concise syntax to create instances of a delegate type.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="2256d-156">try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="2256d-156">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="2256d-157">Çoğu özel durum işleme için [try-catch](../../language-reference/keywords/try-catch.md) ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-157">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="2256d-158">C# [using ifadesini](../../language-reference/keywords/using-statement.md)kullanarak kodunuzu kolaylaştırın.</span><span class="sxs-lookup"><span data-stu-id="2256d-158">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="2256d-159">Yalnızca bloktaki kodun yöntemine yönelik bir çağrı olduğu bir [try-finally](../../language-reference/keywords/try-finally.md) deyiminiz varsa `finally` <xref:System.IDisposable.Dispose%2A> , `using` bunun yerine bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-159">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="2256d-160">&& ve &#124;&#124; Işleçleri</span><span class="sxs-lookup"><span data-stu-id="2256d-160">&& and &#124;&#124; Operators</span></span>  
  
<span data-ttu-id="2256d-161">Gereksiz karşılaştırmaları atlayarak özel durumların önüne geçmek ve performansı artırmak için, [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) Aşağıdaki örnekte gösterildiği gibi karşılaştırmaları gerçekleştirirken [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) yerine yerine [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-161">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="2256d-162">Yeni İşleç</span><span class="sxs-lookup"><span data-stu-id="2256d-162">New Operator</span></span>  
  
- <span data-ttu-id="2256d-163">Aşağıdaki bildirimde gösterildiği gibi örtük olarak yazılan nesne örneğinin kısa biçimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-163">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="2256d-164">Önceki satır aşağıdaki bildirime eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2256d-164">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="2256d-165">Nesne oluşturma işlemini basitleştirmek için nesne başlatıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-165">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="2256d-166">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="2256d-166">Event Handling</span></span>  
  
<span data-ttu-id="2256d-167">Daha sonra kaldırmanız gerekmeyen bir olay işleyicisi tanımlıyorsanız, bir lambda ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-167">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="2256d-168">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="2256d-168">Static Members</span></span>  
  
<span data-ttu-id="2256d-169">[Statik](../../language-reference/keywords/static.md) üyeleri, sınıf adı: *ClassName. staticmember*' i kullanarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="2256d-169">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="2256d-170">Bu uygulama, statik erişim Temizleme yaparak kodu daha okunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2256d-170">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="2256d-171">Türetilmiş bir sınıf adına sahip bir temel sınıfta tanımlanan statik bir üyeyi nitelemeyin.</span><span class="sxs-lookup"><span data-stu-id="2256d-171">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="2256d-172">Kod derlense de, kod okunurluğu yanıltıcı olur ve türetilmiş sınıfa aynı ada sahip bir statik üye eklerseniz kod daha sonra bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="2256d-172">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="2256d-173">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="2256d-173">LINQ Queries</span></span>  
  
- <span data-ttu-id="2256d-174">Sorgu değişkenleri için anlamlı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-174">Use meaningful names for query variables.</span></span> <span data-ttu-id="2256d-175">Aşağıdaki örnek `seattleCustomers` Seattle 'da bulunan müşteriler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2256d-175">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="2256d-176">Anonim türlerin özellik adlarının, Pascal büyük küçük harf kullanarak doğru şekilde büyük harfli olduğundan emin olmak için diğer adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-176">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="2256d-177">Sonuç içindeki Özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="2256d-177">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="2256d-178">Örneğin, sorgunuz bir müşteri adı ve bir dağıtıcı KIMLIĞI döndürürse, ve sonuç olarak bırakmak yerine, `Name` `ID` `Name` bir müşterinin adı olduğunu ve bır dağıtıcının kimliğini açıklığa kavuşturacak şekilde yeniden adlandırın `ID` .</span><span class="sxs-lookup"><span data-stu-id="2256d-178">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="2256d-179">Sorgu değişkenleri ve Aralık değişkenleri bildiriminde örtük yazma kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-179">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="2256d-180">Önceki örneklerde gösterildiği gibi, [from](../../language-reference/keywords/from-clause.md) yan tümcesinin altındaki sorgu yan tümcelerini hizalayın.</span><span class="sxs-lookup"><span data-stu-id="2256d-180">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="2256d-181">Daha sonra sorgu yan tümcelerinin azaltılmış ve filtrelenmiş veri kümesi üzerinde çalışmasını sağlamak için diğer sorgu yan tümcelerinden önce [WHERE](../../language-reference/keywords/where-clause.md) yan tümceleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-181">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="2256d-182">`from`İç koleksiyonlara erişmek için [JOIN](../../language-reference/keywords/join-clause.md) yan tümcesi yerine birden çok yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="2256d-182">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="2256d-183">Örneğin, bir `Student` nesne koleksiyonu her biri bir test puanları koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2256d-183">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="2256d-184">Aşağıdaki sorgu yürütüldüğünde, puanı alan öğrencinin son adıyla birlikte 90 ' ten fazla olan her puanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="2256d-184">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="2256d-185">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="2256d-185">Security</span></span>  

<span data-ttu-id="2256d-186">[Güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2256d-186">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2256d-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2256d-187">See also</span></span>

- [<span data-ttu-id="2256d-188">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="2256d-188">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="2256d-189">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2256d-189">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
