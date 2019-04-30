---
title: C#Kodlama kuralları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 55716a9955d12ef3a926efe352a0078044de9990
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709958"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="626f1-102">C# Kodlama Kuralları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="626f1-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="626f1-103">Kodlama kuralları aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="626f1-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="626f1-104">Böylece okuyucular düzene değil içeriğe göre koda tutarlı bir görünüm oluştururlar.</span><span class="sxs-lookup"><span data-stu-id="626f1-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="626f1-105">Bunlar, okuyucular kodunuzu daha hızlı bir şekilde önceki deneyime dayanan varsayımlar yaparak anlamanız etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="626f1-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="626f1-106">Bunlar, kopyalama, değiştirme ve kodun bakımını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="626f1-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="626f1-107">Bunlar, C# en iyi uygulamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="626f1-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="626f1-108">Bu konudaki yönergeleri, örnekler ve belgeler geliştirmek için Microsoft tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="626f1-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="626f1-109">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="626f1-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="626f1-110">Dahil etmezseniz kısa örneklerde [yönergeleri kullanarak](../../../csharp/language-reference/keywords/using-directive.md), ad alanı nitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-110">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="626f1-111">Bir ad alanı, bir projedeki varsayılan olarak içeri aktarılır biliyorsanız, bu ad alanı adlarından tam olarak nitelemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="626f1-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="626f1-112">Aşağıdaki örnekte gösterildiği gibi tek bir satır için çok uzun olmaları durumunda tam adları nokta (.) sonra bozuk olabilir.</span><span class="sxs-lookup"><span data-stu-id="626f1-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="626f1-113">Diğer yönergelerine uygun olacak şekilde Visual Studio Tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="626f1-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="626f1-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="626f1-114">Layout Conventions</span></span>  
 <span data-ttu-id="626f1-115">İyi Düzen biçimlendirme, kod yapısını vurgulamak ve kodun okunmasını kolaylaştırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="626f1-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="626f1-116">Microsoft örnekleri ve örnek için aşağıdaki kurallara uygun:</span><span class="sxs-lookup"><span data-stu-id="626f1-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="626f1-117">Varsayılan Kod Düzenleyicisi ayarları (Akıllı girintileme dört karakterlik girintileri, sekmeleri boşluk olarak kaydedilen) kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="626f1-118">Daha fazla bilgi için [seçenekler, metin düzenleyici, C#, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="626f1-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="626f1-119">Her satırda yalnızca bir deyim yazın.</span><span class="sxs-lookup"><span data-stu-id="626f1-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="626f1-120">Her satırda yalnızca bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="626f1-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="626f1-121">Bir sekme durağı (dört alanları), devamlılık satırlarını otomatik olarak girinti değil, bunları girinti.</span><span class="sxs-lookup"><span data-stu-id="626f1-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="626f1-122">Yöntem tanımlarını ve özellik tanımları arasına en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="626f1-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="626f1-123">Yan tümceleri bir ifadede görünür, aşağıdaki kodda gösterildiği gibi hale getirmek için ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="626f1-124">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="626f1-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="626f1-125">Bir kod satırının sonunda değil ayrı bir satırda açıklama yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="626f1-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="626f1-126">Büyük harfle yorum metni başlatın.</span><span class="sxs-lookup"><span data-stu-id="626f1-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="626f1-127">Yorum metnini noktayla sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="626f1-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="626f1-128">Açıklama sınırlayıcısı arasında bir boşluk (/ /) ve aşağıdaki örnekte gösterildiği gibi açıklama metni.</span><span class="sxs-lookup"><span data-stu-id="626f1-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="626f1-129">Biçimlendirilmiş yıldız açıklamaları etrafında bloklarını oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="626f1-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="626f1-130">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="626f1-130">Language Guidelines</span></span>  
 <span data-ttu-id="626f1-131">Aşağıdaki bölümlerde, C# ekip kod örnekleri ve örnek hazırlamak için aşağıdaki yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="626f1-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="626f1-132">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="626f1-132">String Data Type</span></span>  
  
- <span data-ttu-id="626f1-133">Kullanım [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) kısa dizeler, aşağıdaki kodda gösterildiği gibi birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="626f1-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="626f1-134">Döngülere diziler, özellikle büyük miktarlarda metini çalışırken eklemek için kullanmak bir <xref:System.Text.StringBuilder> nesne.</span><span class="sxs-lookup"><span data-stu-id="626f1-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="626f1-135">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="626f1-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="626f1-136">Kullanım [örtülü yazma](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) değişkeninin türünü atama veya kesin türü önemli olmadığı durumlarda sağından belirgin olduğunda yerel değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="626f1-136">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="626f1-137">Kullanmayın [var](../../../csharp/language-reference/keywords/var.md) türü olmadığında ataması sağ taraftan görünür.</span><span class="sxs-lookup"><span data-stu-id="626f1-137">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="626f1-138">Değişken türünü belirtmek için değişken adını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="626f1-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="626f1-139">Doğru olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="626f1-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="626f1-140">Kullanmaktan kaçının `var` yerine [dinamik](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="626f1-140">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
- <span data-ttu-id="626f1-141">Örtülü yazma Döngü değişkeninin içinde türünü belirlemek için kullanın [için](../../../csharp/language-reference/keywords/for.md) ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md) döngüleri.</span><span class="sxs-lookup"><span data-stu-id="626f1-141">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="626f1-142">Aşağıdaki örnek örtük yazarak kullanan bir `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="626f1-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="626f1-143">Aşağıdaki örnek örtük yazarak kullanan bir `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="626f1-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="626f1-144">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="626f1-144">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="626f1-145">Genel olarak, kullanın `int` imzasız türler yerine.</span><span class="sxs-lookup"><span data-stu-id="626f1-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="626f1-146">Kullanımını `int` C# yaygın bir durumdur ve diğer kitaplıklarla birlikte kullandığınızda etkileşim kolaydır `int`.</span><span class="sxs-lookup"><span data-stu-id="626f1-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="626f1-147">Diziler</span><span class="sxs-lookup"><span data-stu-id="626f1-147">Arrays</span></span>  
  
- <span data-ttu-id="626f1-148">Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="626f1-149">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="626f1-149">Delegates</span></span>  
  
- <span data-ttu-id="626f1-150">Bir temsilci türünün örneğini oluşturmak için kısa sözdizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="626f1-151">try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="626f1-151">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="626f1-152">Kullanım bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) çoğu özel durum işleme için bildirimi.</span><span class="sxs-lookup"><span data-stu-id="626f1-152">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="626f1-153">C# kullanarak kodunuzu basitleştirerek [using deyimi](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="626f1-153">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="626f1-154">Varsa bir [try-finally](../../../csharp/language-reference/keywords/try-finally.md) deyimi, yalnızca kod `finally` blok çağrısı ise <xref:System.IDisposable.Dispose%2A> yöntemini kullanmak bir `using` deyimi yerine.</span><span class="sxs-lookup"><span data-stu-id="626f1-154">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="626f1-155">& & ve &#124; &#124; işleçleri</span><span class="sxs-lookup"><span data-stu-id="626f1-155">&& and &#124;&#124; Operators</span></span>  
  
- <span data-ttu-id="626f1-156">Özel durumlar önlemek ve gereksiz karşılaştırmalar atlayarak performansı artırmak için kullandığınız [ && ](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) yerine [ & ](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) ve [ &#124; &#124; ](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)yerine [ &#124; ](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) gerçekleştirirken karşılaştırmalar, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="626f1-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="626f1-157">Yeni İşleç</span><span class="sxs-lookup"><span data-stu-id="626f1-157">New Operator</span></span>  
  
- <span data-ttu-id="626f1-158">Nesne örneklemesini kısa biçiminde örtülü yazma için aşağıdaki bildirimde gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="626f1-159">Önceki satıra aşağıdaki bildirime eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="626f1-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="626f1-160">Nesne oluşturma işlemini basitleştirmek için nesne başlatıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="626f1-161">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="626f1-161">Event Handling</span></span>  
  
- <span data-ttu-id="626f1-162">Daha sonra kaldırmanız gerekmez bir olay işleyicisi tanımlıyorsanız, bir lambda ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="626f1-163">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="626f1-163">Static Members</span></span>  
  
- <span data-ttu-id="626f1-164">Çağrı [statik](../../../csharp/language-reference/keywords/static.md) üyeleri sınıf adını kullanarak: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="626f1-164">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="626f1-165">Bu yöntem kod daha okunabilir Temizle statik erişim sağlayarak yapar.</span><span class="sxs-lookup"><span data-stu-id="626f1-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="626f1-166">Bir temel sınıfta türetilmiş bir sınıfın adıyla tanımlanan statik bir üye için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="626f1-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="626f1-167">Bu kod derlenir, kodun okunabilirliğini yanıltıcı ve türetilmiş sınıf için aynı ada sahip bir statik üye ekleme kodu gelecekte bozabilir.</span><span class="sxs-lookup"><span data-stu-id="626f1-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="626f1-168">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="626f1-168">LINQ Queries</span></span>  
  
- <span data-ttu-id="626f1-169">Sorgu değişkenleri için anlamlı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="626f1-170">Aşağıdaki örnekte `seattleCustomers` müşteriler Seattle'dadır.</span><span class="sxs-lookup"><span data-stu-id="626f1-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="626f1-171">Anonim türlerinin özellik adlarının doğru Pascal kullanarak emin olmak için diğer adları kullanın. büyük/küçük harf.</span><span class="sxs-lookup"><span data-stu-id="626f1-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="626f1-172">Sonuçtaki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="626f1-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="626f1-173">Örneğin, sorgunuz bir müşteri adı ve olarak bırakmak yerine bir dağıtıcı kimliği döndürür `Name` ve `ID` sonucunda açıklamak için yeniden adlandırma `Name` bir müşteri adı ve `ID` bir dağıtıcıyı kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="626f1-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="626f1-174">Sorgu değişkenleri ve aralık değişkenleri bildiriminde örtülü yazma kullanın.</span><span class="sxs-lookup"><span data-stu-id="626f1-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="626f1-175">Altında sorgu yan tümcelerini hizalayın [gelen](../../../csharp/language-reference/keywords/from-clause.md) yan tümcesi, önceki örneklerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="626f1-175">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="626f1-176">Kullanım [burada](../../../csharp/language-reference/keywords/where-clause.md) yan tümceleri önce sonraki sorgu yan tümcelerinin azaltılmış üzerinde çalışmasını sağlamak için diğer sorgu yan tümcelerinin filtrelenmiş veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="626f1-176">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="626f1-177">Birden çok kullanın `from` yan tümceleri yerine bir [birleştirme](../../../csharp/language-reference/keywords/join-clause.md) yan tümcesi iç koleksiyonlara erişmek için.</span><span class="sxs-lookup"><span data-stu-id="626f1-177">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="626f1-178">Örneğin, bir koleksiyonunu `Student` nesneleri her içerebilir test puanlarını koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="626f1-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="626f1-179">Aşağıdaki sorgu yürütüldüğünde, üzerinde birlikte puana Öğrenci Soyadı 90 her bir puan döndürür.</span><span class="sxs-lookup"><span data-stu-id="626f1-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="626f1-180">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="626f1-180">Security</span></span>  
 <span data-ttu-id="626f1-181">Bölümündeki yönergeleri uygulayın [güvenli kodlama kılavuzları](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="626f1-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626f1-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="626f1-182">See also</span></span>

- [<span data-ttu-id="626f1-183">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="626f1-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="626f1-184">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="626f1-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
