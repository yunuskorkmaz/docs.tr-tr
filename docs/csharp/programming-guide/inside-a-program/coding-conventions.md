---
title: C# Kodlama Kuralları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 697c3df3d418c57d58c42dc3cfb900de02146c80
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="573ee-102">C# Kodlama Kuralları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="573ee-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="573ee-103">Kodlama kuralları aşağıdaki amaca hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="573ee-103">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="573ee-104">Okuyucular içeriğine değil düzeni odaklanabilmeniz bunlar kodu tutarlı bir görünüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="573ee-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="573ee-105">Bunlar, önceki deneyimleri temel varsayımları yaparak kodu daha hızlı bir şekilde anlaşılması okuyucular etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="573ee-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="573ee-106">Bunlar, kopyalama, değiştirme ve kod bakımı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="573ee-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="573ee-107">Bunlar, C# en iyi uygulamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="573ee-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="573ee-108">Bu konudaki yönergeleri, örnekler ve belgeler geliştirmek için Microsoft tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="573ee-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="573ee-109">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="573ee-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="573ee-110">İçermeyen kısa örneklerde [yönergeleri kullanarak](../../../csharp/language-reference/keywords/using-directive.md), ad alanı nitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-110">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="573ee-111">Bir ad alanı varsayılan projede alınır biliyorsanız, bu ad alanı adlarından tam olarak nitelemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="573ee-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="573ee-112">Aşağıdaki örnekte gösterildiği gibi tek bir satır için çok uzun olmaları durumunda nitelenmiş adlar bir nokta (.) sonra bozuk olabilir.</span><span class="sxs-lookup"><span data-stu-id="573ee-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   <span data-ttu-id="573ee-113">Bunları diğer yönergelerine uygun hale getirmek için Visual Studio Tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını değiştirmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="573ee-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="573ee-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="573ee-114">Layout Conventions</span></span>  
 <span data-ttu-id="573ee-115">Kodunuzu yapısını vurgulamak ve kod okunmasını kolaylaştırmak için iyi düzenini biçimlendirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="573ee-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="573ee-116">Microsoft örnekleri ve örnekler için aşağıdaki kurallara uygun:</span><span class="sxs-lookup"><span data-stu-id="573ee-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="573ee-117">Varsayılan kod düzenleyicisinde ayarları (Akıllı Girintileme, dört karakter girintileri, alanları olarak kaydedilen sekmeleri) kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="573ee-118">Daha fazla bilgi için bkz: [seçenekler, metin düzenleyici, C++, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="573ee-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="573ee-119">Satır başına yalnızca bir deyim yazma.</span><span class="sxs-lookup"><span data-stu-id="573ee-119">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="573ee-120">Satır başına yalnızca bir bildirimini yazma.</span><span class="sxs-lookup"><span data-stu-id="573ee-120">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="573ee-121">Devamlılık satırlarının otomatik olarak girinti değil, bunları bir sekme durağı (dört alanları) girinti.</span><span class="sxs-lookup"><span data-stu-id="573ee-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="573ee-122">Yöntem tanımlarını ve özellik tanımları arasında en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="573ee-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="573ee-123">Yan tümceleri bir ifadede görünür, aşağıdaki kodda gösterildiği gibi yapma ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="573ee-124">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="573ee-124">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="573ee-125">Kod satırının sonunda değil ayrı bir satırda açıklama yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="573ee-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="573ee-126">Açıklama metni büyük harfe ile başlar.</span><span class="sxs-lookup"><span data-stu-id="573ee-126">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="573ee-127">Açıklama metni noktayla bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="573ee-127">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="573ee-128">Açıklama sınırlayıcısı arasında bir boşluk (/ /) ve aşağıdaki örnekte gösterildiği gibi açıklama metni.</span><span class="sxs-lookup"><span data-stu-id="573ee-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   <span data-ttu-id="573ee-129">Yorumlar geçici yıldızlar biçimlendirilmiş bloklarını oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="573ee-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="573ee-130">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="573ee-130">Language Guidelines</span></span>  
 <span data-ttu-id="573ee-131">Aşağıdaki bölümlerde C# takım kod örnekleri ve örnekleri hazırlamak için aşağıdaki yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="573ee-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="573ee-132">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="573ee-132">String Data Type</span></span>  
  
-   <span data-ttu-id="573ee-133">Kullanım [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) aşağıdaki kodda gösterildiği gibi kısa dizeyi birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="573ee-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   <span data-ttu-id="573ee-134">Özellikle büyük miktarlarda metin ile çalışırken döngüler, dizelerde eklemek için kullanın bir <xref:System.Text.StringBuilder> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="573ee-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="573ee-135">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="573ee-135">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="573ee-136">Kullanım [örtülü yazma](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) değişkeninin türü sağından atama veya kesin türü önemli olmadığında açık olduğunda, yerel değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="573ee-136">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   <span data-ttu-id="573ee-137">Kullanmayın [var](../../../csharp/language-reference/keywords/var.md) türü olmadığında atama sağ tarafında görünür.</span><span class="sxs-lookup"><span data-stu-id="573ee-137">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   <span data-ttu-id="573ee-138">Değişken türünü belirtmek için değişken adını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="573ee-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="573ee-139">Doğru olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="573ee-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   <span data-ttu-id="573ee-140">Kullanmaktan kaçının `var` yerine [dinamik](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="573ee-140">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="573ee-141">Örtük yazarak döngü değişken türünü belirlemek için kullanın [için](../../../csharp/language-reference/keywords/for.md) ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md) döngüler.</span><span class="sxs-lookup"><span data-stu-id="573ee-141">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="573ee-142">Aşağıdaki örnek, örtük yazarak kullanır bir `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="573ee-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="573ee-143">Aşağıdaki örnek, örtük yazarak kullanır bir `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="573ee-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="573ee-144">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="573ee-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="573ee-145">Genel olarak, kullanın `int` imzasız türler yerine.</span><span class="sxs-lookup"><span data-stu-id="573ee-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="573ee-146">Kullanımını `int` C# yaygın bir durumdur ve diğer kitaplıklarla birlikte kullandığınızda etkileşim daha kolaydır `int`.</span><span class="sxs-lookup"><span data-stu-id="573ee-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="573ee-147">Diziler</span><span class="sxs-lookup"><span data-stu-id="573ee-147">Arrays</span></span>  
  
-   <span data-ttu-id="573ee-148">Diziler bildirimi satırındaki başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="573ee-149">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="573ee-149">Delegates</span></span>  
  
-   <span data-ttu-id="573ee-150">Bir temsilci türü örnekleri oluşturmak için kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="573ee-151">try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="573ee-151">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="573ee-152">Kullanım bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) çoğu özel durum işleme için bildirimi.</span><span class="sxs-lookup"><span data-stu-id="573ee-152">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   <span data-ttu-id="573ee-153">C# kullanarak kodunuzu basitleştiren [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="573ee-153">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="573ee-154">Varsa bir [try-finally](../../../csharp/language-reference/keywords/try-finally.md) hangi deyiminde yalnızca kodda `finally` blok çağrıdır <xref:System.IDisposable.Dispose%2A> yöntemi, kullanım bir `using` deyimi yerine.</span><span class="sxs-lookup"><span data-stu-id="573ee-154">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="573ee-155">& & ve &#124; &#124; işleçleri</span><span class="sxs-lookup"><span data-stu-id="573ee-155">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="573ee-156">Özel durumlar önlemek ve gereksiz karşılaştırmaları atlayarak performansı artırmak için kullanmak [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) yerine [ & ](../../../csharp/language-reference/operators/and-operator.md) ve [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)yerine [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) gerçekleştirdiğinizde karşılaştırmaları, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="573ee-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="573ee-157">Yeni İşleç</span><span class="sxs-lookup"><span data-stu-id="573ee-157">New Operator</span></span>  
  
-   <span data-ttu-id="573ee-158">Nesne oluşturmada kısa biçiminde örtülü yazma ile aşağıdaki bildiriminde gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="573ee-159">Önceki satıra aşağıdaki bildirimine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="573ee-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   <span data-ttu-id="573ee-160">Nesne başlatıcıları nesne oluşturma işlemini basitleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="573ee-161">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="573ee-161">Event Handling</span></span>  
  
-   <span data-ttu-id="573ee-162">Daha sonra kaldırmanız gerekmez bir olay işleyicisi tanımlıyorsanız, lambda ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="573ee-163">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="573ee-163">Static Members</span></span>  
  
-   <span data-ttu-id="573ee-164">Çağrı [statik](../../../csharp/language-reference/keywords/static.md) sınıf adını kullanarak üyeleri: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="573ee-164">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="573ee-165">Bu yöntem, temizleyin statik erişim sağlayarak kodunu daha okunabilir yapar.</span><span class="sxs-lookup"><span data-stu-id="573ee-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="573ee-166">Türetilmiş bir sınıf adı ile temel bir sınıf içinde tanımlanan statik bir üyenin uygun değil.</span><span class="sxs-lookup"><span data-stu-id="573ee-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="573ee-167">Bu kodu derlenir kodun okunabilirliğini yanıltıcı ve türetilmiş sınıf aynı ada sahip statik bir üyenin eklerseniz, kodu gelecekte kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="573ee-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="573ee-168">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="573ee-168">LINQ Queries</span></span>  
  
-   <span data-ttu-id="573ee-169">Sorgu değişkenleri için anlamlı adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="573ee-170">Aşağıdaki örnek kullanır `seattleCustomers` Seattle'da bulunan müşteriler için.</span><span class="sxs-lookup"><span data-stu-id="573ee-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="573ee-171">Anonim türdeki özellik adları düzgün, Pascal kullanarak olduğundan emin emin olmak için diğer adlar kullanın büyük/küçük harf.</span><span class="sxs-lookup"><span data-stu-id="573ee-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   <span data-ttu-id="573ee-172">Özellik adlarının sonuç belirsiz kullanırken özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="573ee-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="573ee-173">Sorgunuz bir müşteri adı ve bunları olarak bırakarak yerine bir dağıtıcı kimliği döndürürse, örneğin, `Name` ve `ID` sonucunda açıklamak için yeniden adlandırma `Name` bir müşteri adıdır ve `ID` dağıtıcı kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="573ee-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   <span data-ttu-id="573ee-174">Örtük sorgu değişkenleri ve aralık değişkeni bildiriminde yazarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="573ee-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="573ee-175">Sorgu yan tümceleri altında Hizala [gelen](../../../csharp/language-reference/keywords/from-clause.md) önceki örneklerde gösterildiği gibi yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="573ee-175">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="573ee-176">Kullanım [burada](../../../csharp/language-reference/keywords/where-clause.md) yan tümceleri sonraki sorgu yan tümceleri azaltılmış üzerinde çalışmasını sağlamak için diğer sorgu yan tümceleri önce filtrelenmiş veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="573ee-176">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   <span data-ttu-id="573ee-177">Birden çok kullanın `from` yan tümceleri yerine bir [birleştirme](../../../csharp/language-reference/keywords/join-clause.md) iç koleksiyonları erişmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="573ee-177">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="573ee-178">Örneğin, bir koleksiyonu `Student` nesneleri her içerebilir test puanları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="573ee-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="573ee-179">Aşağıdaki sorgu çalıştırıldığında, Soyadı puanı alınan Öğrenci birlikte üzerinde 90 her puan döndürür.</span><span class="sxs-lookup"><span data-stu-id="573ee-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="573ee-180">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="573ee-180">Security</span></span>  
 <span data-ttu-id="573ee-181">Alan yönergeleri izleyin [güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="573ee-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573ee-182">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="573ee-182">See Also</span></span>  
 [<span data-ttu-id="573ee-183">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="573ee-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [<span data-ttu-id="573ee-184">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="573ee-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
