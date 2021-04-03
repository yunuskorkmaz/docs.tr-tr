---
title: C# kodlama kuralları-C# Programlama Kılavuzu
description: C# ' de kodlama kuralları hakkında bilgi edinin. Kodlama kuralları koda tutarlı bir görünüm oluşturur ve kodun kopyalanmasını, değiştirilmesini ve bakımının yapılmasını kolaylaştırır.
ms.date: 03/31/2021
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.openlocfilehash: 019bf02ea3cdfec2c4ae0d73b5b375781c5fcd9a
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231329"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="d1c60-104">C# Kodlama Kuralları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d1c60-104">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="d1c60-105">Kodlama kuralları aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="d1c60-105">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="d1c60-106">Bunlar, koda tutarlı bir görünüm oluşturur, böylece okuyucular düzene göre değil, içeriğe odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="d1c60-107">Bu kullanıcılar, önceki deneyimle dayalı varsayımlar yaparak okuyucuların kodu daha hızlı anlamasına imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1c60-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="d1c60-108">Kodu kopyalama, değiştirme ve sürdürme işlemlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="d1c60-109">C# En Iyi yöntemlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-109">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="d1c60-110">Bu makaledeki yönergeler, Microsoft tarafından örnek ve belge geliştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-110">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="d1c60-111">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d1c60-111">Naming conventions</span></span>  
  
- <span data-ttu-id="d1c60-112">[Yönergeleri kullanarak](../../language-reference/keywords/using-directive.md)dahil olmayan kısa örneklerde ad alanı nitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-112">In short examples that don't include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="d1c60-113">Bir ad alanının bir projede varsayılan olarak içeri aktarıldığını biliyorsanız, adları bu ad alanından tam olarak nitelemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d1c60-113">If you know that a namespace is imported by default in a project, you don't have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="d1c60-114">Nitelenmiş adlar, aşağıdaki örnekte gösterildiği gibi, tek bir satırda çok uzunsa bir nokta (.) sonrasında bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-114">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet1":::

- <span data-ttu-id="d1c60-115">Visual Studio tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını, diğer yönergelere uyum sağlamak için değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d1c60-115">You don't have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="d1c60-116">Düzen kuralları</span><span class="sxs-lookup"><span data-stu-id="d1c60-116">Layout conventions</span></span>  

<span data-ttu-id="d1c60-117">İyi düzen, kodunuzun yapısını vurgulamak ve kodun daha kolay okunmasını sağlamak için biçimlendirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="d1c60-118">Microsoft örnekleri ve örnekleri aşağıdaki kurallara uygun şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="d1c60-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="d1c60-119">Varsayılan kod Düzenleyicisi ayarlarını (akıllı girintileme, dört karakterlik girintiler, sekmeler boşluk olarak kaydedilir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="d1c60-120">Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici, C#, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="d1c60-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="d1c60-121">Her satırda yalnızca bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-121">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="d1c60-122">Her satırda yalnızca bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-122">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="d1c60-123">Devamlılık satırları otomatik olarak girintili değilse, bir sekme durağı (dört boşluk) için girinti yapın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="d1c60-124">Yöntem tanımları ve özellik tanımları arasına en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1c60-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="d1c60-125">Aşağıdaki kodda gösterildiği gibi, bir ifadedeki tümceleri görünür hale getirmek için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet2":::

## <a name="commenting-conventions"></a><span data-ttu-id="d1c60-126">Yorum oluşturma kuralları</span><span class="sxs-lookup"><span data-stu-id="d1c60-126">Commenting conventions</span></span>  
  
- <span data-ttu-id="d1c60-127">Yorumu bir kod satırının sonuna değil, ayrı bir satıra yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d1c60-127">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="d1c60-128">Açıklama metnini büyük harfle Başlat.</span><span class="sxs-lookup"><span data-stu-id="d1c60-128">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="d1c60-129">Açıklama metnini noktayla bitirin.</span><span class="sxs-lookup"><span data-stu-id="d1c60-129">End comment text with a period.</span></span>  
  
- <span data-ttu-id="d1c60-130">Aşağıdaki örnekte gösterildiği gibi açıklama sınırlayıcısı (//) ve açıklama metni arasına bir boşluk ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1c60-130">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet3":::

- <span data-ttu-id="d1c60-131">Yorumlar etrafında yıldız işareti blokları oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-131">Don't create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="d1c60-132">Dil yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d1c60-132">Language guidelines</span></span>  

<span data-ttu-id="d1c60-133">Aşağıdaki bölümlerde, C# ekibinin kod örneklerini ve örnekleri hazırlamak için izlediği uygulamalar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-133">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="d1c60-134">Dize veri türü</span><span class="sxs-lookup"><span data-stu-id="d1c60-134">String data type</span></span>  
  
- <span data-ttu-id="d1c60-135">Aşağıdaki kodda gösterildiği gibi, kısa dizeleri birleştirmek için [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-135">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet6":::

- <span data-ttu-id="d1c60-136">Döngülerde dizeleri eklemek için, özellikle büyük miktarlarda metinle çalışırken bir <xref:System.Text.StringBuilder> nesnesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-136">To append strings in loops, especially when you're working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="d1c60-137">Örtülü olarak belirtilmiş yerel değişkenler</span><span class="sxs-lookup"><span data-stu-id="d1c60-137">Implicitly typed local variables</span></span>  
  
- <span data-ttu-id="d1c60-138">Değişkenin türü atamanın sağ tarafından açık olduğunda veya kesin tür önemli olmadığında yerel değişkenler için [örtülü yazma](../classes-and-structs/implicitly-typed-local-variables.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-138">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet8":::
  
- <span data-ttu-id="d1c60-139">Tür atamanın sağ tarafından görünmüyorsa, [yok kullanmayın.](../../language-reference/keywords/var.md)</span><span class="sxs-lookup"><span data-stu-id="d1c60-139">Don't use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span> <span data-ttu-id="d1c60-140">Türün bir yöntem adından temiz olduğunu varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-140">Don't assume the type is clear from a method name.</span></span> <span data-ttu-id="d1c60-141">Bir değişken türü, bir `new` işleç veya açık bir tür ise Clear olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-141">A variable type is considered clear if it's a `new` operator or an explicit cast.</span></span>
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet9":::

- <span data-ttu-id="d1c60-142">Değişkenin türünü belirtmek için değişken adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="d1c60-142">Don't rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="d1c60-143">Doğru olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-143">It might not be correct.</span></span> <span data-ttu-id="d1c60-144">Aşağıdaki örnekte, değişken adı `inputInt` yanıltıcıdır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-144">In the following example, the variable name `inputInt` is misleading.</span></span> <span data-ttu-id="d1c60-145">Bu bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-145">It's a string.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet10":::

- <span data-ttu-id="d1c60-146">Dinamik yerine kullanılmasını önleyin `var` . [](../../language-reference/builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="d1c60-146">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span> <span data-ttu-id="d1c60-147">`dynamic`Çalışma zamanı tür çıkarımı istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-147">Use `dynamic` when you want run-time type inference.</span></span> <span data-ttu-id="d1c60-148">Daha fazla bilgi için bkz. [dinamik tür kullanımı (C# Programlama Kılavuzu)](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="d1c60-148">For more information, see [Using type dynamic (C# Programming Guide)](../types/using-type-dynamic.md).</span></span>
  
- <span data-ttu-id="d1c60-149">Döngülerde içindeki döngü değişkeninin türünü [öğrenmek için örtük](../../language-reference/keywords/for.md) yazma kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-149">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
  <span data-ttu-id="d1c60-150">Aşağıdaki örnek, bir bildiriminde örtük yazma kullanır `for` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-150">The following example uses implicit typing in a `for` statement.</span></span>  

    :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

- <span data-ttu-id="d1c60-151">[Foreach](../../language-reference/keywords/foreach-in.md) Döngülerde döngü değişkeninin türünü anlamak için örtük yazma kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-151">Don't use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

  <span data-ttu-id="d1c60-152">Aşağıdaki örnek, bir bildiriminde açık bir yazma kullanır `foreach` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-152">The following example uses explicit typing in a `foreach` statement.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet12":::

  > [!NOTE]
  > <span data-ttu-id="d1c60-153">Yinelenebilir bir koleksiyonun öğe türünü yanlışlıkla değiştirmemeye dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d1c60-153">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="d1c60-154">Örneğin, bir <xref:System.Linq.IQueryable?displayProperty=nameWithType> <xref:System.Collections.IEnumerable?displayProperty=nameWithType> sorgunun yürütülmesini değiştiren bir ifadede öğesine geçiş yapmak kolaydır `foreach` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-154">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-types"></a><span data-ttu-id="d1c60-155">İmzasız veri türleri</span><span class="sxs-lookup"><span data-stu-id="d1c60-155">Unsigned data types</span></span>  
  
<span data-ttu-id="d1c60-156">Genel olarak, `int` imzasız türler yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-156">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="d1c60-157">Kullanımı `int` C# ' nin tamamında ortaktır ve kullandığınızda diğer kitaplıklarla etkileşim kurmak daha kolaydır `int` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-157">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="d1c60-158">Diziler</span><span class="sxs-lookup"><span data-stu-id="d1c60-158">Arrays</span></span>  
  
<span data-ttu-id="d1c60-159">Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-159">Use the concise syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="d1c60-160">Aşağıdaki örnekte yerine kullanmayacağınızı unutmayın `var` `string[]` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-160">In the following example, note that you can't use `var` instead of `string[]`.</span></span>  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13a":::

<span data-ttu-id="d1c60-161">Açık örnek oluşturma kullanıyorsanız, kullanabilirsiniz `var` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-161">If you use explicit instantiation, you can use `var`.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13b":::

<span data-ttu-id="d1c60-162">Bir dizi boyutu belirtirseniz, öğeleri birer birer başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="d1c60-162">If you specify an array size, you have to initialize the elements one at a time.</span></span>
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13c":::
  
### <a name="delegates"></a><span data-ttu-id="d1c60-163">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="d1c60-163">Delegates</span></span>  
  
<span data-ttu-id="d1c60-164">Temsilci türlerini tanımlamak yerine [ `Func<>` ve `Action<>` ](../../../standard/delegates-lambdas.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-164">Use [`Func<>` and `Action<>`](../../../standard/delegates-lambdas.md) instead of defining delegate types.</span></span> <span data-ttu-id="d1c60-165">Bir sınıfında, temsilci yöntemini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-165">In a class, define the delegate method.</span></span>  

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14a":::

<span data-ttu-id="d1c60-166">Veya temsilcisi tarafından tanımlanan imzayı kullanarak yöntemi çağırın `Func<>` `Action<>` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-166">Call the method using the signature defined by the `Func<>` or `Action<>` delegate.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15a":::

<span data-ttu-id="d1c60-167">Bir temsilci türünün örneklerini oluşturursanız, kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-167">If you create instances of a delegate type, use the concise syntax.</span></span> <span data-ttu-id="d1c60-168">Bir sınıfında, temsilci türünü ve eşleşen imzaya sahip bir yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-168">In a class, define the delegate type and a method that has a matching signature.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14b":::

<span data-ttu-id="d1c60-169">Temsilci türünün bir örneğini oluşturun ve çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-169">Create an instance of the delegate type and call it.</span></span> <span data-ttu-id="d1c60-170">Aşağıdaki bildirimde, sıkıştırılmış sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-170">The following declaration shows the condensed syntax.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15b":::

<span data-ttu-id="d1c60-171">Aşağıdaki bildirim tam sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-171">The following declaration uses the full syntax.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15c":::

### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="d1c60-172">`try`-`catch` ve `using` özel durum işlemede deyimleri</span><span class="sxs-lookup"><span data-stu-id="d1c60-172">`try`-`catch` and `using` statements in exception handling</span></span>  
  
- <span data-ttu-id="d1c60-173">Çoğu özel durum işleme için [try-catch](../../language-reference/keywords/try-catch.md) ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-173">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet16":::

- <span data-ttu-id="d1c60-174">C# [using ifadesini](../../language-reference/keywords/using-statement.md)kullanarak kodunuzu kolaylaştırın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-174">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="d1c60-175">Yalnızca bloktaki kodun yöntemine yönelik bir çağrı olduğu bir [try-finally](../../language-reference/keywords/try-finally.md) deyiminiz varsa `finally` <xref:System.IDisposable.Dispose%2A> , `using` bunun yerine bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-175">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>

  <span data-ttu-id="d1c60-176">Aşağıdaki örnekte, `try` - `finally` ifade yalnızca `Dispose` `finally` bloğunda çağırır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-176">In the following example, the `try`-`finally` statement only calls `Dispose` in the `finally` block.</span></span>
  
   :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17a":::

  <span data-ttu-id="d1c60-177">Deyimle aynı şeyi yapabilirsiniz `using` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-177">You can do the same thing with a `using` statement.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17b":::

  <span data-ttu-id="d1c60-178">C# 8 ve sonraki sürümlerinde, küme ayraçları gerektirmeyen yeni [ `using` sözdizimini](../../language-reference/keywords/using-statement.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="d1c60-178">In C# 8 and later versions, use the new [`using` syntax](../../language-reference/keywords/using-statement.md) that doesn't require braces:</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17c":::

### <a name="-and--operators"></a><span data-ttu-id="d1c60-179">`&&` ve `||` işleçleri</span><span class="sxs-lookup"><span data-stu-id="d1c60-179">`&&` and `||` operators</span></span>  
  
<span data-ttu-id="d1c60-180">Özel durumların önüne geçmek ve gereksiz karşılaştırmaları atlayarak performansı artırmak için, [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) [`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) Aşağıdaki örnekte gösterildiği gibi karşılaştırmaları gerçekleştirirken yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-180">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet18":::

<span data-ttu-id="d1c60-181">Bölen 0 ise, deyimdeki ikinci yan tümce `if` bir çalışma zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="d1c60-181">If the divisor is 0, the second clause in the `if` statement would cause a run-time error.</span></span> <span data-ttu-id="d1c60-182">Ancak ilk ifade false olduğunda && işleci kısa devredir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-182">But the && operator short-circuits when the first expression is false.</span></span> <span data-ttu-id="d1c60-183">Yani, ikinci ifadeyi değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="d1c60-183">That is, it doesn't evaluate the second expression.</span></span> <span data-ttu-id="d1c60-184">& işleci her ikisini de değerlendirir ve 0 olduğunda bir çalışma zamanı hatasına neden olur `divisor` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-184">The & operator would evaluate both, resulting in a run-time error when `divisor` is 0.</span></span>
  
### <a name="new-operator"></a><span data-ttu-id="d1c60-185">`new` işlecinde</span><span class="sxs-lookup"><span data-stu-id="d1c60-185">`new` operator</span></span>  
  
- <span data-ttu-id="d1c60-186">Aşağıdaki bildirimlerde gösterildiği gibi, nesne örneklemesinin kısa biçimlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-186">Use one of the concise forms of object instantiation, as shown in the following declarations.</span></span> <span data-ttu-id="d1c60-187">İkinci örnekte, C# 9 ' dan başlayarak kullanılabilir olan sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-187">The second example shows syntax that is available starting in C# 9.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet19":::
  
  ```csharp
  ExampleClass instance2 = new();
  ```
  
  <span data-ttu-id="d1c60-188">Önceki bildirimler aşağıdaki bildirime eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-188">The preceding declarations are equivalent to the following declaration.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet20":::

- <span data-ttu-id="d1c60-189">Aşağıdaki örnekte gösterildiği gibi, nesne oluşturma işlemini basitleştirmek için nesne başlatıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-189">Use object initializers to simplify object creation, as shown in the following example.</span></span>

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21a":::

  <span data-ttu-id="d1c60-190">Aşağıdaki örnek, önceki örnekle aynı özellikleri ayarlar, ancak başlatıcıları kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="d1c60-190">The following example sets the same properties as the preceding example but doesn't use initializers.</span></span>
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21b":::

### <a name="event-handling"></a><span data-ttu-id="d1c60-191">Olay işleme</span><span class="sxs-lookup"><span data-stu-id="d1c60-191">Event handling</span></span>  
  
<span data-ttu-id="d1c60-192">Daha sonra kaldırmanız gerekmeyen bir olay işleyicisi tanımlıyorsanız bir lambda ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-192">If you're defining an event handler that you don't need to remove later, use a lambda expression.</span></span>  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet22":::

<span data-ttu-id="d1c60-193">Lambda ifadesi aşağıdaki geleneksel tanımı kısaltır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-193">The lambda expression shortens the following traditional definition.</span></span>

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet23":::

### <a name="static-members"></a><span data-ttu-id="d1c60-194">Statik üyeler</span><span class="sxs-lookup"><span data-stu-id="d1c60-194">Static members</span></span>  
  
<span data-ttu-id="d1c60-195">[Statik](../../language-reference/keywords/static.md) üyeleri, sınıf adı: *ClassName. staticmember*' i kullanarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-195">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="d1c60-196">Bu uygulama, statik erişim Temizleme yaparak kodu daha okunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-196">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="d1c60-197">Türetilmiş bir sınıf adına sahip bir temel sınıfta tanımlanan statik bir üyeyi niteleme.</span><span class="sxs-lookup"><span data-stu-id="d1c60-197">Don't qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="d1c60-198">Kod derlense de, kod okunurluğu yanıltıcı olur ve türetilmiş sınıfa aynı ada sahip bir statik üye eklerseniz kod daha sonra bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-198">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="d1c60-199">LINQ sorguları</span><span class="sxs-lookup"><span data-stu-id="d1c60-199">LINQ queries</span></span>  
  
- <span data-ttu-id="d1c60-200">Sorgu değişkenleri için anlamlı adlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-200">Use meaningful names for query variables.</span></span> <span data-ttu-id="d1c60-201">Aşağıdaki örnek `seattleCustomers` Seattle 'da bulunan müşteriler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1c60-201">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- <span data-ttu-id="d1c60-202">Anonim türlerin özellik adlarının, Pascal büyük küçük harf kullanarak doğru şekilde büyük harfli olduğundan emin olmak için diğer adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-202">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet26":::

- <span data-ttu-id="d1c60-203">Sonuç içindeki Özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-203">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="d1c60-204">Örneğin, sorgunuz bir müşteri adı ve bir dağıtıcı KIMLIĞI döndürürse, ve sonuç olarak bırakmak yerine, `Name` `ID` `Name` bir müşterinin adı olduğunu ve bır dağıtıcının kimliğini açıklığa kavuşturacak şekilde yeniden adlandırın `ID` .</span><span class="sxs-lookup"><span data-stu-id="d1c60-204">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet27":::

- <span data-ttu-id="d1c60-205">Sorgu değişkenleri ve Aralık değişkenleri bildiriminde örtük yazma kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-205">Use implicit typing in the declaration of query variables and range variables.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- <span data-ttu-id="d1c60-206">Önceki örneklerde gösterildiği gibi, [from](../../language-reference/keywords/from-clause.md) yan tümcesinin altındaki sorgu yan tümcelerini hizalayın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-206">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  

- <span data-ttu-id="d1c60-207">Daha sonra sorgu yan tümcelerinin azaltılmış ve filtrelenmiş veri kümesi üzerinde çalışmasını sağlamak için diğer sorgu yan tümcelerinden önce [WHERE](../../language-reference/keywords/where-clause.md) yan tümceleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-207">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet29":::

- <span data-ttu-id="d1c60-208">`from`İç koleksiyonlara erişmek için [JOIN](../../language-reference/keywords/join-clause.md) yan tümcesi yerine birden çok yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c60-208">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="d1c60-209">Örneğin, bir `Student` nesne koleksiyonu her biri bir test puanları koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d1c60-209">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="d1c60-210">Aşağıdaki sorgu yürütüldüğünde, puanı alan öğrencinin son adıyla birlikte 90 ' ten fazla olan her puanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1c60-210">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet30":::

## <a name="security"></a><span data-ttu-id="d1c60-211">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="d1c60-211">Security</span></span>  

<span data-ttu-id="d1c60-212">[Güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d1c60-212">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c60-213">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c60-213">See also</span></span>

- [<span data-ttu-id="d1c60-214">.NET çalışma zamanı kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d1c60-214">.NET runtime coding guidelines</span></span>](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
- [<span data-ttu-id="d1c60-215">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="d1c60-215">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="d1c60-216">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d1c60-216">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
