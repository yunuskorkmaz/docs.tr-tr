---
title: C#Kodlama kuralları- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: c56d673de958f49a9ace60350442e89039e1d69f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712110"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="447de-102">C# Kodlama Kuralları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="447de-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="447de-103">Kodlama kuralları aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="447de-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="447de-104">Bunlar, koda tutarlı bir görünüm oluşturur, böylece okuyucular düzene göre değil, içeriğe odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="447de-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="447de-105">Bu kullanıcılar, önceki deneyimle dayalı varsayımlar yaparak okuyucuların kodu daha hızlı anlamasına imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="447de-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="447de-106">Kodu kopyalama, değiştirme ve sürdürme işlemlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="447de-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="447de-107">En iyi C# uygulamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="447de-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="447de-108">Bu konudaki yönergeler, Microsoft tarafından örnek ve belge geliştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="447de-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="447de-109">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="447de-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="447de-110">[Using yönergeleri](../../language-reference/keywords/using-directive.md)dahil olmayan kısa örneklerde ad alanı nitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-110">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="447de-111">Bir ad alanının bir projede varsayılan olarak içeri aktarıldığını biliyorsanız, adları bu ad alanından tam olarak nitelemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="447de-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="447de-112">Nitelenmiş adlar, aşağıdaki örnekte gösterildiği gibi, tek bir satırda çok uzunsa bir nokta (.) sonrasında bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="447de-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="447de-113">Visual Studio tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını, diğer yönergelere uyum sağlamak için değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="447de-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="447de-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="447de-114">Layout Conventions</span></span>  
 <span data-ttu-id="447de-115">İyi düzen, kodunuzun yapısını vurgulamak ve kodun daha kolay okunmasını sağlamak için biçimlendirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="447de-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="447de-116">Microsoft örnekleri ve örnekleri aşağıdaki kurallara uygun şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="447de-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="447de-117">Varsayılan kod Düzenleyicisi ayarlarını (akıllı girintileme, dört karakterlik girintiler, sekmeler boşluk olarak kaydedilir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="447de-118">Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici C#,, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="447de-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="447de-119">Her satırda yalnızca bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="447de-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="447de-120">Her satırda yalnızca bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="447de-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="447de-121">Devamlılık satırları otomatik olarak girintili değilse, bir sekme durağı (dört boşluk) için girinti yapın.</span><span class="sxs-lookup"><span data-stu-id="447de-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="447de-122">Yöntem tanımları ve özellik tanımları arasına en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="447de-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="447de-123">Aşağıdaki kodda gösterildiği gibi, bir ifadedeki tümceleri görünür hale getirmek için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="447de-124">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="447de-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="447de-125">Yorumu bir kod satırının sonuna değil, ayrı bir satıra yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="447de-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="447de-126">Açıklama metnini büyük harfle Başlat.</span><span class="sxs-lookup"><span data-stu-id="447de-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="447de-127">Açıklama metnini noktayla bitirin.</span><span class="sxs-lookup"><span data-stu-id="447de-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="447de-128">Aşağıdaki örnekte gösterildiği gibi açıklama sınırlayıcısı (//) ve açıklama metni arasına bir boşluk ekleyin.</span><span class="sxs-lookup"><span data-stu-id="447de-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="447de-129">Açıklamaların etrafında, biçimli yıldız işaretleri oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="447de-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="447de-130">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="447de-130">Language Guidelines</span></span>  
 <span data-ttu-id="447de-131">Aşağıdaki bölümlerde, C# takımın kod örneklerini ve örnekleri hazırlamak için izlediği uygulamalar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="447de-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="447de-132">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="447de-132">String Data Type</span></span>  
  
- <span data-ttu-id="447de-133">Aşağıdaki kodda gösterildiği gibi, kısa dizeleri birleştirmek için [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="447de-134">Döngülerde dizeleri eklemek için, özellikle büyük miktarlarda metinle çalışırken bir <xref:System.Text.StringBuilder> nesnesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="447de-135">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="447de-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="447de-136">Değişkenin türü atamanın sağ tarafından açık olduğunda veya kesin tür önemli olmadığında yerel değişkenler için [örtülü yazma](../classes-and-structs/implicitly-typed-local-variables.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-136">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="447de-137">Tür atamanın sağ tarafından görünmüyorsa, [yok kullanmayın.](../../language-reference/keywords/var.md)</span><span class="sxs-lookup"><span data-stu-id="447de-137">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="447de-138">Değişkenin türünü belirtmek için değişken adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="447de-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="447de-139">Doğru olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="447de-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="447de-140">[Dinamik](../../language-reference/builtin-types/reference-types.md)yerine `var` kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="447de-140">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="447de-141">[For](../../language-reference/keywords/for.md) ve [foreach](../../language-reference/keywords/foreach-in.md) döngüleri içindeki döngü değişkeninin türünü öğrenmek için örtük yazma kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-141">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) and [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="447de-142">Aşağıdaki örnek, `for` bildiriminde örtük yazma kullanır.</span><span class="sxs-lookup"><span data-stu-id="447de-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
     <span data-ttu-id="447de-143">Aşağıdaki örnek, `foreach` bildiriminde örtük yazma kullanır.</span><span class="sxs-lookup"><span data-stu-id="447de-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="447de-144">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="447de-144">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="447de-145">Genel olarak, işaretsiz türler yerine `int` kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="447de-146">`int` kullanımı genelinde C#yaygındır ve `int`kullandığınızda diğer kitaplıklarla etkileşim kurmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="447de-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="447de-147">Diziler</span><span class="sxs-lookup"><span data-stu-id="447de-147">Arrays</span></span>  
  
- <span data-ttu-id="447de-148">Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="447de-149">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="447de-149">Delegates</span></span>  
  
- <span data-ttu-id="447de-150">Bir temsilci türünün örneklerini oluşturmak için kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="447de-151">try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="447de-151">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="447de-152">Çoğu özel durum işleme için [try-catch](../../language-reference/keywords/try-catch.md) ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-152">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="447de-153">C# [Using ifadesini](../../language-reference/keywords/using-statement.md)kullanarak kodunuzu kolaylaştırın.</span><span class="sxs-lookup"><span data-stu-id="447de-153">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="447de-154">Yalnızca `finally` bloğundaki kodun <xref:System.IDisposable.Dispose%2A> yöntemine yönelik bir çağrı olduğu bir [try-finally](../../language-reference/keywords/try-finally.md) deyiminiz varsa, bunun yerine bir `using` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-154">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="447de-155">& & ve &#124; &#124; işleçler</span><span class="sxs-lookup"><span data-stu-id="447de-155">&& and &#124;&#124; Operators</span></span>  
  
- <span data-ttu-id="447de-156">Gereksiz karşılaştırmaları atlayarak özel durumları önlemek ve performansı artırmak için, aşağıdaki örnekte gösterildiği gibi [](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) , karşılaştırmaları [ &#124; ](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) gerçekleştirirken&[&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) yerine [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="447de-157">Yeni İşleç</span><span class="sxs-lookup"><span data-stu-id="447de-157">New Operator</span></span>  
  
- <span data-ttu-id="447de-158">Aşağıdaki bildirimde gösterildiği gibi örtük olarak yazılan nesne örneğinin kısa biçimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="447de-159">Önceki satır aşağıdaki bildirime eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="447de-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="447de-160">Nesne oluşturma işlemini basitleştirmek için nesne başlatıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="447de-161">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="447de-161">Event Handling</span></span>  
  
- <span data-ttu-id="447de-162">Daha sonra kaldırmanız gerekmeyen bir olay işleyicisi tanımlıyorsanız, bir lambda ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="447de-163">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="447de-163">Static Members</span></span>  
  
- <span data-ttu-id="447de-164">[Statik](../../language-reference/keywords/static.md) üyeleri, sınıf adı: *ClassName. staticmember*' i kullanarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="447de-164">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="447de-165">Bu uygulama, statik erişim Temizleme yaparak kodu daha okunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="447de-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="447de-166">Türetilmiş bir sınıf adına sahip bir temel sınıfta tanımlanan statik bir üyeyi nitelemeyin.</span><span class="sxs-lookup"><span data-stu-id="447de-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="447de-167">Kod derlense de, kod okunurluğu yanıltıcı olur ve türetilmiş sınıfa aynı ada sahip bir statik üye eklerseniz kod daha sonra bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="447de-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="447de-168">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="447de-168">LINQ Queries</span></span>  
  
- <span data-ttu-id="447de-169">Sorgu değişkenleri için anlamlı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="447de-170">Aşağıdaki örnek, Seattle 'da bulunan müşteriler için `seattleCustomers` kullanır.</span><span class="sxs-lookup"><span data-stu-id="447de-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="447de-171">Anonim türlerin özellik adlarının, Pascal büyük küçük harf kullanarak doğru şekilde büyük harfli olduğundan emin olmak için diğer adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="447de-172">Sonuç içindeki Özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="447de-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="447de-173">Örneğin, sorgunuz bir müşteri adı ve bir dağıtıcı KIMLIĞI döndürürse, `Name` olarak bırakmak yerine `ID`, `Name` bir müşterinin adı olduğunu ve `ID` bir dağıtıcı KIMLIĞI olduğunu açıklığa kavuşturacak şekilde yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="447de-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="447de-174">Sorgu değişkenleri ve Aralık değişkenleri bildiriminde örtük yazma kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="447de-175">Önceki örneklerde gösterildiği gibi, [from](../../language-reference/keywords/from-clause.md) yan tümcesinin altındaki sorgu yan tümcelerini hizalayın.</span><span class="sxs-lookup"><span data-stu-id="447de-175">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="447de-176">Daha sonra sorgu yan tümcelerinin azaltılmış ve filtrelenmiş veri kümesi üzerinde çalışmasını sağlamak için diğer sorgu yan tümcelerinden önce [WHERE](../../language-reference/keywords/where-clause.md) yan tümceleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-176">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="447de-177">İç koleksiyonlara erişmek için [JOIN](../../language-reference/keywords/join-clause.md) yan tümcesi yerine birden çok `from` yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="447de-177">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="447de-178">Örneğin, `Student` nesnelerinin bir koleksiyonu, her biri bir test puanları koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="447de-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="447de-179">Aşağıdaki sorgu yürütüldüğünde, puanı alan öğrencinin son adıyla birlikte 90 ' ten fazla olan her puanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="447de-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="447de-180">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="447de-180">Security</span></span>  
 <span data-ttu-id="447de-181">[Güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="447de-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447de-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="447de-182">See also</span></span>

- [<span data-ttu-id="447de-183">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="447de-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="447de-184">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="447de-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
