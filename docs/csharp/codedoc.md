---
title: Kodunuzu XML yorumlarıyla belgeleme
description: Kodunuzu XML dokümantasyon yorumlarıyla nasıl belgeleyacağınızı ve derleme zamanında bir XML dokümantasyon dosyası oluşturmayı öğrenin.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1ed39c4733c36b3932fcb85bf50d4f4c0e53aa6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146323"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="e2287-103">Kodunuzu XML yorumlarıyla belgele</span><span class="sxs-lookup"><span data-stu-id="e2287-103">Document your code with XML comments</span></span>

<span data-ttu-id="e2287-104">XML dokümantasyon yorumları, kullanıcı tarafından tanımlanan herhangi bir tür veya üyetanımının üzerine eklenen özel bir yorum türüdür.</span><span class="sxs-lookup"><span data-stu-id="e2287-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="e2287-105">Derleyici tarafından derleyici tarafından derleme zamanında bir XML dokümantasyon dosyası oluşturmak için işlenebileceğinden özeldirler.</span><span class="sxs-lookup"><span data-stu-id="e2287-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="e2287-106">Derleyici tarafından oluşturulan XML dosyası .NET derlemenizin yanında dağıtılabilir, böylece Visual Studio ve diğer IDA'lar türleri veya üyeleri hakkında hızlı bilgi göstermek için IntelliSense'i kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-106">The compiler-generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="e2287-107">Ayrıca, XML dosyası API başvuru web siteleri oluşturmak için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) gibi araçlar aracılığıyla çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="e2287-108">XML dokümantasyon yorumları, diğer tüm yorumlar gibi derleyici tarafından yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e2287-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="e2287-109">Aşağıdakilerden birini yaparak XML dosyasını derleme zamanında oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e2287-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="e2287-110">Komut satırından .NET Core içeren bir uygulama geliştiriyorsanız, `GenerateDocumentationFile` .csproj proje dosyanızın bölümüne `<PropertyGroup>` bir öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="e2287-111">Ayrıca, [ `DocumentationFile` öğeyi](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak doğrudan dokümantasyon dosyasına giden yolu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="e2287-112">Aşağıdaki örnek, proje dizininde derlemeyle aynı kök dosya adına sahip bir XML dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e2287-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   <span data-ttu-id="e2287-113">Bu, aşağıdakilere eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="e2287-113">This is equivalent to the following:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="e2287-114">Visual Studio'yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="e2287-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="e2287-115">Özellikler iletişim kutusunda, **Yapı** sekmesini seçin ve **XML belge dosyasını**denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e2287-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="e2287-116">Derleyicinin dosyayı yazdığı konumu da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="e2287-117">Komut satırından bir .NET Framework uygulaması derliyorsanız, derleme yaparken [-doc derleyici seçeneğini](language-reference/compiler-options/doc-compiler-option.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2287-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="e2287-118">XML dokümantasyon yorumları üçlü`///`ileri eğik çizgiler ( ) ve XML biçimlendirilmiş yorum gövdesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2287-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="e2287-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e2287-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="e2287-120">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="e2287-120">Walkthrough</span></span>

<span data-ttu-id="e2287-121">Yeni geliştiricilerin anlamasını/katkıda bulunmasını ve üçüncü taraf geliştiricilerin kullanmasını kolaylaştırmak için çok temel bir matematik kitaplığını belgeleme konusunda yürüyelim.</span><span class="sxs-lookup"><span data-stu-id="e2287-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="e2287-122">Burada basit matematik kitaplığı için kod:</span><span class="sxs-lookup"><span data-stu-id="e2287-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="e2287-123">Örnek kitaplık dört ana aritmetik `subtract` `multiply`işlemleri `divide`destekler `int` ( `double` `add`, , , ve ) ve veri türleri.</span><span class="sxs-lookup"><span data-stu-id="e2287-123">The sample library supports four major arithmetic operations (`add`, `subtract`, `multiply`, and `divide`) on `int` and `double` data types.</span></span>

<span data-ttu-id="e2287-124">Artık kitaplığınızı kullanan ancak kaynak koduna erişimi olmayan üçüncü taraf geliştiriciler için kodunuzdan bir API başvuru belgesi oluşturmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e2287-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="e2287-125">Daha önce belirtildiği gibi XML belge etiketleri bunu başarmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="e2287-126">Şimdi C# derleyicisinin desteklediği standart XML etiketleri ile tanışır.</span><span class="sxs-lookup"><span data-stu-id="e2287-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="e2287-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="e2287-127">\<summary></span></span>

<span data-ttu-id="e2287-128">Etiket, `<summary>` bir tür veya üye hakkında kısa bilgiler ekler.</span><span class="sxs-lookup"><span data-stu-id="e2287-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="e2287-129">Ben `Math` sınıf tanımı ve ilk `Add` yöntem ekleyerek kullanımını göstereceğim.</span><span class="sxs-lookup"><span data-stu-id="e2287-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="e2287-130">Kodunuzun geri kalanına uygulamadan çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="e2287-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="e2287-131">Etiket `<summary>` önemlidir ve içeriği IntelliSense'deki tür veya üye bilgilerinin birincil kaynağı veya API başvuru belgesi olduğundan etiketlemeyi eklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="e2287-131">The `<summary>` tag is important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2287-132">\<açıklamalar></span><span class="sxs-lookup"><span data-stu-id="e2287-132">\<remarks></span></span>

<span data-ttu-id="e2287-133">Etiket, `<remarks>` `<summary>` etiketin sağladığı türveya üyeler hakkındaki bilgileri tamamlar.</span><span class="sxs-lookup"><span data-stu-id="e2287-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="e2287-134">Bu örnekte, sınıfa eklemeniz gereken bir örnek.</span><span class="sxs-lookup"><span data-stu-id="e2287-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="e2287-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="e2287-135">\<returns></span></span>

<span data-ttu-id="e2287-136">Etiket, `<returns>` yöntem bildiriminin dönüş değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2287-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="e2287-137">Daha önce olduğu gibi, `<returns>` aşağıdaki örnekte `Add` ilk yöntemdeki etiket gösterin.</span><span class="sxs-lookup"><span data-stu-id="e2287-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="e2287-138">Aynı şeyi diğer yöntemlerde de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="e2287-139">\<value></span><span class="sxs-lookup"><span data-stu-id="e2287-139">\<value></span></span>

<span data-ttu-id="e2287-140">Etiket, `<value>` özellikleri için `<returns>` kullanmanız dışında etikete benzer.</span><span class="sxs-lookup"><span data-stu-id="e2287-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="e2287-141">Kitaplığınızın `Math` statik `PI`bir özelliği olduğunu varsayarsak, bu etiketi şu şekilde kullanırdınız:</span><span class="sxs-lookup"><span data-stu-id="e2287-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="e2287-142">\<örnek></span><span class="sxs-lookup"><span data-stu-id="e2287-142">\<example></span></span>

<span data-ttu-id="e2287-143">`<example>` Etiketi XML belgelerinize bir örnek eklemek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2287-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="e2287-144">Bu, alt `<code>` etiketini kullanmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="e2287-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="e2287-145">Etiket, `code` satır sonları ve girintiyi daha uzun örnekler için korur.</span><span class="sxs-lookup"><span data-stu-id="e2287-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="e2287-146">\<para></span><span class="sxs-lookup"><span data-stu-id="e2287-146">\<para></span></span>

<span data-ttu-id="e2287-147">`<para>` Etiketi, ana etiketindeki içeriği biçimlendirmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2287-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="e2287-148">`<para>`genellikle bir etiket içinde kullanılır, gibi `<remarks>` veya `<returns>`, paragraflara metin bölmek için.</span><span class="sxs-lookup"><span data-stu-id="e2287-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="e2287-149">Sınıf tanımınız için `<remarks>` etiketin içeriğini biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="e2287-150">\<c></span><span class="sxs-lookup"><span data-stu-id="e2287-150">\<c></span></span>

<span data-ttu-id="e2287-151">Biçimlendirme konusunda hala, metnin `<c>` bir bölümünü kod olarak işaretlemek için etiketi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2287-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="e2287-152">Bu `<code>` etiket gibi ama satır içinde.</span><span class="sxs-lookup"><span data-stu-id="e2287-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="e2287-153">Bir etiketin içeriğinin bir parçası olarak hızlı bir kod örneği göstermek istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e2287-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="e2287-154">Sınıfın belgelerini `Math` güncelleyelim.</span><span class="sxs-lookup"><span data-stu-id="e2287-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="e2287-155">\<özel durum></span><span class="sxs-lookup"><span data-stu-id="e2287-155">\<exception></span></span>

<span data-ttu-id="e2287-156">`<exception>` Etiketi kullanarak, geliştiricilerinize bir yöntemin belirli özel durumlar atabileceğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="e2287-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="e2287-157">Kitaplığınıza `Math` baktığınızda, belirli bir `Add` koşul yerine getirildiğinde her iki yöntemin de özel bir durum ortaya çıkardığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="e2287-158">O kadar açık değil, ancak, `Divide` `b` parametre sıfır ise tamsayı yöntemi de atar.</span><span class="sxs-lookup"><span data-stu-id="e2287-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="e2287-159">Şimdi bu yönteme özel durum belgeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2287-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="e2287-160">Öznitelik, `cref` geçerli derleme ortamından kullanılabilen bir özel durum için bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e2287-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="e2287-161">Bu, projede tanımlanan herhangi bir tür veya başvurulan bir derleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="e2287-162">Derleyici, değeri çözülemiyorsa bir uyarı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="e2287-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="e2287-163">\<bkz.></span><span class="sxs-lookup"><span data-stu-id="e2287-163">\<see></span></span>

<span data-ttu-id="e2287-164">Etiket, `<see>` başka bir kod öğesi için bir belgesayfasına tıklanabilir bir bağlantı oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e2287-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="e2287-165">Bir sonraki örneğimizde, iki `Add` yöntem arasında tıklanabilir bir bağlantı oluştururuz.</span><span class="sxs-lookup"><span data-stu-id="e2287-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="e2287-166">Bu, `cref` geçerli derleme ortamından kullanılabilen bir türe veya üyesine yapılan başvuruyu temsil eden **gerekli** bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="e2287-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="e2287-167">Bu, projede tanımlanan herhangi bir tür veya başvurulan bir derleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="e2287-168">\<seealso></span><span class="sxs-lookup"><span data-stu-id="e2287-168">\<seealso></span></span>

<span data-ttu-id="e2287-169">`<seealso>` Etiketi, `<see>` etiketi yaptığınız gibi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2287-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="e2287-170">Tek fark, içeriğinin genellikle bir "Ayrıca Bak" bölümüne yerleştirilmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e2287-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="e2287-171">Burada tamsayı parametrelerini kabul eden `Add` sınıftaki diğer yöntemlere başvurmak için tamsayı yöntemine bir `seealso` etiket ekleyeceğiz:</span><span class="sxs-lookup"><span data-stu-id="e2287-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="e2287-172">Öznitelik, `cref` geçerli derleme ortamından kullanılabilen bir türe veya üyesine yapılan başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e2287-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="e2287-173">Bu, projede tanımlanan herhangi bir tür veya başvurulan bir derleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="e2287-174">\<param></span><span class="sxs-lookup"><span data-stu-id="e2287-174">\<param></span></span>

<span data-ttu-id="e2287-175">Bir yöntemin parametrelerini `<param>` açıklamak için etiketi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2287-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="e2287-176">Çift `Add` yöntemle ilgili bir örnek aşağıda verilmiştir: Etiketin açıkladığı parametre **gerekli** `name` öznitelikte belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="e2287-177">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="e2287-177">\<typeparam></span></span>

<span data-ttu-id="e2287-178">Etiketi etiket gibi, ancak genel bir parametreyi açıklamak için genel tür veya yöntem bildirimleri için kullanırsınız. `<typeparam>` `<param>`</span><span class="sxs-lookup"><span data-stu-id="e2287-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="e2287-179">Bir miktarın diğerinden `Math` büyük olup olmadığını denetlemek için sınıfınıza hızlı bir genel yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2287-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="e2287-180">\<paramref></span><span class="sxs-lookup"><span data-stu-id="e2287-180">\<paramref></span></span>

<span data-ttu-id="e2287-181">Bazen bir yöntemin `<summary>` etiket olabilecek bir şeyde ne yaptığını açıklamanın ortasında olabilirsiniz ve bir parametreye başvuruda bulunmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="e2287-182">Etiket `<paramref>` sadece bu için harika.</span><span class="sxs-lookup"><span data-stu-id="e2287-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="e2287-183">Çift tabanlı `Add` yöntemimizin özetini güncelleyelim.</span><span class="sxs-lookup"><span data-stu-id="e2287-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="e2287-184">`<param>` Etiket gibi, parametre adı da **gerekli** `name` öznitelikte belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-184">Like the `<param>` tag, the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="e2287-185">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="e2287-185">\<typeparamref></span></span>

<span data-ttu-id="e2287-186">Etiketi etiket gibi, ancak genel bir parametreyi açıklamak için genel tür veya yöntem bildirimleri için kullanırsınız. `<typeparamref>` `<paramref>`</span><span class="sxs-lookup"><span data-stu-id="e2287-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="e2287-187">Daha önce oluşturduğunuz genel yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="e2287-188">\<liste></span><span class="sxs-lookup"><span data-stu-id="e2287-188">\<list></span></span>

<span data-ttu-id="e2287-189">Etiketi, `<list>` belge bilgilerini sıralı bir liste, sıralanmamış liste veya tablo olarak biçimlendirmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2287-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list, or table.</span></span> <span data-ttu-id="e2287-190">Kitaplığınızın `Math` desteklediği her matematik işleminin sıralanmamış bir listesini yapın.</span><span class="sxs-lookup"><span data-stu-id="e2287-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="e2287-191">Sırasıyla özniteliği değiştirerek `type` sıralı bir liste `number` `table`veya tablo yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

## <a name="inheritdoc"></a><span data-ttu-id="e2287-192">\<kalıtsal doc></span><span class="sxs-lookup"><span data-stu-id="e2287-192">\<inheritdoc></span></span>

<span data-ttu-id="e2287-193">`<inheritdoc>` Etiketi, temel sınıflardan, arabirimlerden ve benzer yöntemlerden XML yorumlarını devralmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-193">You can use the `<inheritdoc>` tag to inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="e2287-194">Bu, yinelenen XML yorumlarının istenmeyen kopyalanması ve yapıştırMasını ortadan kaldırır ve XML yorumlarını otomatik olarak senkronize eder.</span><span class="sxs-lookup"><span data-stu-id="e2287-194">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a><span data-ttu-id="e2287-195">Hepsini bir araya getirin</span><span class="sxs-lookup"><span data-stu-id="e2287-195">Put it all together</span></span>

<span data-ttu-id="e2287-196">Bu öğreticiyi takip ettiyseniz ve etiketleri gerektiğinde kodunuza uyguladıysanız, kodunuz artık aşağıdakilere benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e2287-196">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="e2287-197">Kodunuzdan, tıklanabilir çapraz referanslarla birlikte ayrıntılı bir dokümantasyon web sitesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2287-197">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="e2287-198">Ama başka bir sorunla karşı karşıyasınız: kodunuzu okumak zor laştı.</span><span class="sxs-lookup"><span data-stu-id="e2287-198">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="e2287-199">Bu koda katkıda bulunmak isteyen herhangi bir geliştirici için bir kabus olacak bu elemek için çok fazla bilgi var.</span><span class="sxs-lookup"><span data-stu-id="e2287-199">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="e2287-200">Neyse ki bu başa yardımcı olabilecek bir XML etiketi var:</span><span class="sxs-lookup"><span data-stu-id="e2287-200">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="e2287-201">\<> dahil</span><span class="sxs-lookup"><span data-stu-id="e2287-201">\<include></span></span>

<span data-ttu-id="e2287-202">Etiket, `<include>` belge yorumlarını doğrudan kaynak kod dosyanıza yerleştirmek yerine kaynak kodunuzdaki türleri ve üyeleri açıklayan ayrı bir XML dosyasındaki yorumlara başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2287-202">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="e2287-203">Şimdi tüm XML etiketlerinizi ayrı bir XML dosyasına `docs.xml`taşıyacaksın.</span><span class="sxs-lookup"><span data-stu-id="e2287-203">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="e2287-204">Dosyaya istediğiniz ismi vermekte çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="e2287-204">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="e2287-205">Yukarıdaki XML'de, her üyenin dokümantasyon yorumları doğrudan yaptıklarından sonra bir etiketin içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="e2287-205">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="e2287-206">Kendi stratejini seçebilirsin.</span><span class="sxs-lookup"><span data-stu-id="e2287-206">You can choose your own strategy.</span></span>
<span data-ttu-id="e2287-207">Artık XML yorumlarınızı ayrı bir dosyada gördüğünüze göre, `<include>` etiketi kullanarak kodunuzun nasıl daha okunabilir hale getirebileceğini görelim:</span><span class="sxs-lookup"><span data-stu-id="e2287-207">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="e2287-208">Ve işte burada: kodumuz tekrar okunabilir hale döndü ve hiçbir belge bilgisi kaybedilmedi.</span><span class="sxs-lookup"><span data-stu-id="e2287-208">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="e2287-209">Öznitelik belgeleri `file` içeren XML dosyasının adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e2287-209">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="e2287-210">Öznitelik `path` belirtilen `tag name` bugünü bir [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) sorgusu `file`temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e2287-210">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="e2287-211">Öznitelik, `name` yorumlardan önce etiketteki adı belirtici temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e2287-211">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="e2287-212">`id` Yerine `name`kullanılabilen öznitelik, yorumlardan önce gelen etiketin kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e2287-212">The `id` attribute, which can be used in place of `name`, represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="e2287-213">Kullanıcı tanımlı etiketler</span><span class="sxs-lookup"><span data-stu-id="e2287-213">User-defined tags</span></span>

<span data-ttu-id="e2287-214">Yukarıda özetlenen tüm etiketler, C# derleyicisi tarafından tanınan etiketleri temsil elerdir.</span><span class="sxs-lookup"><span data-stu-id="e2287-214">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="e2287-215">Ancak, bir kullanıcı kendi etiketlerini tanımlamakta özgürdür.</span><span class="sxs-lookup"><span data-stu-id="e2287-215">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="e2287-216">Sandcastle gibi araçlar [ \<olay>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) ve [ \<not>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm)gibi ekstra etiketler için destek getirmek ve hatta ad alanlarını [belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)desteği.</span><span class="sxs-lookup"><span data-stu-id="e2287-216">Tools like Sandcastle bring support for extra tags like [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) and [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="e2287-217">Özel veya şirket içi dokümantasyon oluşturma araçları da standart etiketlerle kullanılabilir ve HTML'den PDF'ye birden fazla çıkış biçimi desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-217">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="e2287-218">Öneriler</span><span class="sxs-lookup"><span data-stu-id="e2287-218">Recommendations</span></span>

<span data-ttu-id="e2287-219">Kodu belgeleme birçok nedenden dolayı önerilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-219">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="e2287-220">C# kodunuzda XML belge etiketleri kullanırken bilmeniz gereken bazı en iyi uygulamalar, genel kullanım durumu senaryoları ve bilmeniz gereken şeyler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2287-220">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="e2287-221">Tutarlılık adına, herkesin önünde görülebilen tüm türler ve üyeleri belgelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e2287-221">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="e2287-222">Eğer yapmak zorundaysan, hepsini yap.</span><span class="sxs-lookup"><span data-stu-id="e2287-222">If you must do it, do it all.</span></span>
- <span data-ttu-id="e2287-223">Özel üyeler xml yorumları kullanılarak da belgelenebilir.</span><span class="sxs-lookup"><span data-stu-id="e2287-223">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="e2287-224">Ancak bu, kitaplığınızın iç (potansiyel olarak gizli) çalışmasını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e2287-224">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="e2287-225">En azından, intelliSense için `<summary>` içeriği gerektiğinden, türleri ve üyeleri bir etikete sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2287-225">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="e2287-226">Dokümantasyon metni tam duraklarla biten tam cümleler kullanılarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2287-226">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="e2287-227">Kısmi sınıflar tam olarak desteklenir ve belge bilgileri bu tür için tek bir girişe dönüştürülecektir.</span><span class="sxs-lookup"><span data-stu-id="e2287-227">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="e2287-228">`<exception>`Derleyici, `<include>`, , `<param>` `<see>`, `<seealso>`, , ve `<typeparam>` etiketlerin sözdizimini doğrular.</span><span class="sxs-lookup"><span data-stu-id="e2287-228">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`, and `<typeparam>` tags.</span></span>
- <span data-ttu-id="e2287-229">Derleyici, dosya yolları ve kodun diğer bölümlerine başvurular içeren parametreleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="e2287-229">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2287-230">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2287-230">See also</span></span>

- [<span data-ttu-id="e2287-231">XML Belgeleri Yorumları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e2287-231">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="e2287-232">Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e2287-232">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
