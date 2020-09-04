---
title: Kodunuzu XML açıklamalarıyla belgeleme
description: Kodunuzu XML belge açıklamalarıyla belgeleme ve derleme zamanında bir XML belge dosyası oluşturma hakkında bilgi edinin.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 91de11c610ea17999dabff6d0552de9440f532e6
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465305"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="8f118-103">Kodunuzu XML açıklamalarıyla belgeleme</span><span class="sxs-lookup"><span data-stu-id="8f118-103">Document your code with XML comments</span></span>

<span data-ttu-id="8f118-104">XML belge açıklamaları, Kullanıcı tanımlı herhangi bir tür veya üyenin tanımının üzerine eklenen özel bir açıklama türüdür.</span><span class="sxs-lookup"><span data-stu-id="8f118-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="8f118-105">Bunlar, derleme zamanında bir XML belge dosyası oluşturmak için derleyici tarafından işlenebilecekleri için özeldir.</span><span class="sxs-lookup"><span data-stu-id="8f118-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="8f118-106">Derleyici tarafından oluşturulan XML dosyası, Visual Studio ve diğer IDE 'Ler, türler veya üyeler hakkında hızlı bilgi göstermek için IntelliSense kullanabilmesi için .NET derlemenizin yanı sıra dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-106">The compiler-generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="8f118-107">Ayrıca, XML dosyası, API başvuru Web siteleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi araçlar aracılığıyla çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="8f118-108">Tüm diğer yorumlar gibi XML belgesi açıklamaları derleyici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="8f118-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="8f118-109">XML dosyasını, derleme zamanında aşağıdakilerden birini yaparak oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f118-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="8f118-110">Komut satırından .NET Core ile bir uygulama geliştiriyorsanız, `GenerateDocumentationFile` `<PropertyGroup>` . csproj proje dosyanızın bölümüne bir öğesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="8f118-111">Ayrıca, belge dosyasının yolunu doğrudan [ `DocumentationFile` öğesini](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="8f118-112">Aşağıdaki örnek, derleme ile aynı kök dosya adına sahip proje dizininde bir XML dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8f118-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   <span data-ttu-id="8f118-113">Bu, aşağıdaki gibi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="8f118-113">This is equivalent to the following:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="8f118-114">Visual Studio 'Yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayıp **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="8f118-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="8f118-115">Özellikler iletişim kutusunda **derleme** sekmesini seçin ve **XML belge dosyasını**denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8f118-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="8f118-116">Derleyicinin dosyayı yazdıkları konumu da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="8f118-117">Komut satırından bir .NET uygulaması derlerken, derlerken [-doc derleyici seçeneğini](language-reference/compiler-options/doc-compiler-option.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8f118-117">If you are compiling a .NET application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="8f118-118">XML belge açıklamaları Üçlü eğik çizgi ( `///` ) ve XML biçimli bir açıklama gövdesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f118-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="8f118-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8f118-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="8f118-120">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="8f118-120">Walkthrough</span></span>

<span data-ttu-id="8f118-121">Yeni geliştiricilerin, üçüncü taraf geliştiricilerin kullanması için ve katkıda bulunmak üzere çok basit bir matematik kitaplığını belgeleme konusunda bilgi vereceğiz.</span><span class="sxs-lookup"><span data-stu-id="8f118-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="8f118-122">Basit matematik kitaplığı için kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8f118-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="8f118-123">Örnek kitaplık, ve veri türlerini dört ana aritmetik işlemi ( `add` , `subtract` , `multiply` , ve `divide` ) destekler `int` `double` .</span><span class="sxs-lookup"><span data-stu-id="8f118-123">The sample library supports four major arithmetic operations (`add`, `subtract`, `multiply`, and `divide`) on `int` and `double` data types.</span></span>

<span data-ttu-id="8f118-124">Şimdi kitaplığınızı kullanan üçüncü taraf geliştiriciler için kodunuzda bir API başvuru belgesi oluşturabilmek, ancak kaynak koda erişiminiz yok.</span><span class="sxs-lookup"><span data-stu-id="8f118-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="8f118-125">Daha önce bahsedilen XML belge etiketleri bunu elde etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="8f118-126">Artık C# derleyicisinin desteklediği standart XML etiketlerine tanıtılcaksınız.</span><span class="sxs-lookup"><span data-stu-id="8f118-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## \<summary>

<span data-ttu-id="8f118-127">`<summary>`Etiketi, bir tür veya üye hakkında kısa bilgiler ekler.</span><span class="sxs-lookup"><span data-stu-id="8f118-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="8f118-128">Kendi kullanımını `Math` sınıf tanımına ve ilk yönteme ekleyerek göstereceğim `Add` .</span><span class="sxs-lookup"><span data-stu-id="8f118-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="8f118-129">Kodunuzu geri kalanına uygulamayı ücretsiz olarak hissetmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="8f118-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="8f118-130">`<summary>`Etiketi önemlidir ve içeriği, IntelliSense 'de veya BIR API başvuru belgesinde bulunan içerik veya üye bilgilerinin birincil kaynağı olduğundan, bunu dahil etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="8f118-130">The `<summary>` tag is important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## \<remarks>

<span data-ttu-id="8f118-131">`<remarks>`Etiketi, etiketin sağladığı türler veya Üyeler hakkındaki bilgileri tamamlar `<summary>` .</span><span class="sxs-lookup"><span data-stu-id="8f118-131">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="8f118-132">Bu örnekte, bunu yalnızca sınıfına eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-132">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## \<returns>

<span data-ttu-id="8f118-133">`<returns>`Etiket, bir yöntem bildiriminin dönüş değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f118-133">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="8f118-134">Daha önce olduğu gibi, aşağıdaki örnek `<returns>` İlk yöntemde etiketini gösterir `Add` .</span><span class="sxs-lookup"><span data-stu-id="8f118-134">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="8f118-135">Diğer yöntemlerle aynı şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-135">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## \<value>

<span data-ttu-id="8f118-136">`<value>`Etiketi, bu etiketle benzerdir `<returns>` , ancak bunları özellikler için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f118-136">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="8f118-137">`Math`Kitaplığınızın bir statik özelliği olduğu varsayıldığında `PI` , bu etiketi şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f118-137">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## \<example>

<span data-ttu-id="8f118-138">`<example>`XML belgelerinize bir örnek eklemek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f118-138">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="8f118-139">Bunun için alt etiketi kullanılması gerekir `<code>` .</span><span class="sxs-lookup"><span data-stu-id="8f118-139">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="8f118-140">`code`Etiket, daha uzun örnekler için satır sonlarını ve girintiyi korur.</span><span class="sxs-lookup"><span data-stu-id="8f118-140">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## \<para>

<span data-ttu-id="8f118-141">`<para>`İçeriğini üst etiketi içinde biçimlendirmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f118-141">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="8f118-142">`<para>` genellikle `<remarks>` `<returns>` metin paragraflarına bölmek için veya gibi bir etiket içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f118-142">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="8f118-143">`<remarks>`Sınıf tanımınız için etiketin içeriğini biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-143">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## \<c>

<span data-ttu-id="8f118-144">Biçimlendirme konusunda hala, `<c>` metnin bir kısmını kod olarak işaretlemek için etiketini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8f118-144">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="8f118-145">`<code>`Etiket, ancak satır içi gibi.</span><span class="sxs-lookup"><span data-stu-id="8f118-145">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="8f118-146">Bir etiketin içeriğinin bir parçası olarak hızlı bir kod örneği göstermek istediğinizde yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="8f118-146">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="8f118-147">Sınıfın belgelerini güncelleştirelim `Math` .</span><span class="sxs-lookup"><span data-stu-id="8f118-147">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## \<exception>

<span data-ttu-id="8f118-148">`<exception>`Etiketini kullanarak, geliştiricilerin bir yöntemin belirli özel durumlar oluşturduğunu bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f118-148">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="8f118-149">`Math`Kitaplığınıza bakarak, `Add` belirli bir koşul karşılanırsa her iki yöntemin de bir özel durum oluşturmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-149">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="8f118-150">Öyle değildir, ancak `Divide` parametrenin sıfır olması durumunda tamsayı yöntemi de oluşturulur `b` .</span><span class="sxs-lookup"><span data-stu-id="8f118-150">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="8f118-151">Şimdi bu yönteme özel durum belgeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8f118-151">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="8f118-152">`cref`Öznitelik, geçerli derleme ortamında kullanılabilir olan bir özel duruma başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f118-152">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="8f118-153">Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-153">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="8f118-154">Değeri çözülemezse, derleyici bir uyarı verebilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-154">The compiler will issue a warning if its value cannot be resolved.</span></span>

## \<see>

<span data-ttu-id="8f118-155">`<see>`Etiketi, başka bir kod öğesi için bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f118-155">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="8f118-156">Sonraki örnekte, iki yöntem arasında tıklatılabilir bir bağlantı oluşturacağız `Add` .</span><span class="sxs-lookup"><span data-stu-id="8f118-156">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="8f118-157">, `cref` Geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eden **gerekli** bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="8f118-157">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="8f118-158">Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-158">This can be any type defined in the project or a referenced assembly.</span></span>

## \<seealso>

<span data-ttu-id="8f118-159">`<seealso>`Etiketi, etiketi yaptığınız şekilde kullanırsınız `<see>` .</span><span class="sxs-lookup"><span data-stu-id="8f118-159">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="8f118-160">Tek fark, içeriğinin genellikle bir "Ayrıca bkz." bölümüne yerleştirilme nedendir.</span><span class="sxs-lookup"><span data-stu-id="8f118-160">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="8f118-161">Burada, tamsayı `seealso` `Add` parametrelerini kabul eden sınıftaki diğer yöntemlere başvurmak için tamsayı yöntemine bir etiket ekleyeceğiz:</span><span class="sxs-lookup"><span data-stu-id="8f118-161">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="8f118-162">`cref`Öznitelik, geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f118-162">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="8f118-163">Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-163">This can be any type defined in the project or a referenced assembly.</span></span>

## \<param>

<span data-ttu-id="8f118-164">`<param>`Bir yöntemin parametrelerini anlatmak için etiketini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8f118-164">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="8f118-165">Double yöntemine bir örnek aşağıda verilmiştir `Add` : etiketin açıkladığı parametre, **gerekli** `name` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-165">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## \<typeparam>

<span data-ttu-id="8f118-166">Etiketi `<typeparam>` tıpkı etiketi gibi kullanırsınız, `<param>` ancak genel tür veya yöntem bildirimlerinin genel bir parametreyi tanımlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f118-166">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="8f118-167">`Math`Bir miktarın diğerinden daha büyük olup olmadığını denetlemek için sınıfınıza hızlı genel bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8f118-167">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## \<paramref>

<span data-ttu-id="8f118-168">Bazen bir yöntemin hangi bir etiketle ne olduğunu açıklayan ortasında olabilirsiniz `<summary>` ve bir parametreye başvuru yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-168">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="8f118-169">`<paramref>`Etiketi yalnızca bunun için harika.</span><span class="sxs-lookup"><span data-stu-id="8f118-169">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="8f118-170">Double tabanlı yönteminizin özetini güncelleştirelim `Add` .</span><span class="sxs-lookup"><span data-stu-id="8f118-170">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="8f118-171">Etiketi gibi `<param>` , parametre adı **gerekli** `name` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-171">Like the `<param>` tag, the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## \<typeparamref>

<span data-ttu-id="8f118-172">Etiketi `<typeparamref>` tıpkı etiketi gibi kullanırsınız, `<paramref>` ancak genel tür veya yöntem bildirimlerinin genel bir parametreyi tanımlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f118-172">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="8f118-173">Daha önce oluşturduğunuz genel yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-173">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## \<list>

<span data-ttu-id="8f118-174">`<list>`Belge bilgilerini sıralı liste, sırasız liste veya tablo olarak biçimlendirmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f118-174">You use the `<list>` tag to format documentation information as an ordered list, unordered list, or table.</span></span> <span data-ttu-id="8f118-175">Kitaplığınızın desteklediği her matematik işleminin sıralanmamış bir listesini oluşturun `Math` .</span><span class="sxs-lookup"><span data-stu-id="8f118-175">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="8f118-176">`type`Özniteliği sırasıyla veya olarak değiştirerek sıralı bir liste veya tablo yapabilirsiniz `number` `table` .</span><span class="sxs-lookup"><span data-stu-id="8f118-176">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

## \<inheritdoc>

<span data-ttu-id="8f118-177">`<inheritdoc>`Temel sınıflardan, arabirimlerden ve benzer metotlardan XML açıklamalarını devralacak şekilde etiketini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-177">You can use the `<inheritdoc>` tag to inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="8f118-178">Bu, yinelenen XML açıklamalarını istenmeyen kopyalama ve yapıştırmayı ortadan kaldırır ve otomatik olarak XML açıklamalarını eşitlenmiş halde tutar.</span><span class="sxs-lookup"><span data-stu-id="8f118-178">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a><span data-ttu-id="8f118-179">Hepsini bir araya getirin</span><span class="sxs-lookup"><span data-stu-id="8f118-179">Put it all together</span></span>

<span data-ttu-id="8f118-180">Bu öğreticiyi takip ediyorsanız ve gereken yere etiketleri kodunuza uyguladıysanız, kodunuzun aşağıdakine benzer şekilde görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f118-180">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="8f118-181">Kodınızdan, tıklatılabilir çapraz başvurularla ayrıntılı bir belge Web sitesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-181">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="8f118-182">Ancak başka bir sorunla karşılaşıyoruz: kodunuzun okunması zor oldu.</span><span class="sxs-lookup"><span data-stu-id="8f118-182">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="8f118-183">Bu koda katkıda bulunmak isteyen herhangi bir geliştirici için bu bir gece olacak şekilde, bu kadar çok bilgi vardır.</span><span class="sxs-lookup"><span data-stu-id="8f118-183">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="8f118-184">Bu konuda size yardımcı olabilecek bir XML etiketi vardı:</span><span class="sxs-lookup"><span data-stu-id="8f118-184">Thankfully there's an XML tag that can help you deal with this:</span></span>

## \<include>

<span data-ttu-id="8f118-185">`<include>`Etiketi, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeyi aksine, kaynak kodunuzda türleri ve üyeleri tanımlayan ayrı bır XML dosyasındaki açıklamalara başvurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f118-185">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="8f118-186">Artık tüm XML etiketlerinizi adlı ayrı bir XML dosyasına taşıyacağız `docs.xml` .</span><span class="sxs-lookup"><span data-stu-id="8f118-186">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="8f118-187">Dosyayı istediğiniz şekilde adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-187">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="8f118-188">Yukarıdaki XML 'de, her üyenin belge yorumu, ne yapacaklarıyla doğrudan adlı bir etiketin içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="8f118-188">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="8f118-189">Kendi stratejinizi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f118-189">You can choose your own strategy.</span></span>
<span data-ttu-id="8f118-190">XML açıklamalarınız ayrı bir dosyada olduğuna göre, şu etiketi kullanarak kodunuzun daha okunaklı hale getirilme biçimini görelim `<include>` :</span><span class="sxs-lookup"><span data-stu-id="8f118-190">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="8f118-191">Bu durumda: kodunuz okunabilir hale getirilir ve belge bilgisi kaybedilmiyor.</span><span class="sxs-lookup"><span data-stu-id="8f118-191">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="8f118-192">`file`Öznitelik, belgeleri IÇEREN XML dosyasının adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f118-192">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="8f118-193">`path`Öznitelik, belirtilen öğesinde var olan bir [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) sorgusunu temsil eder `tag name` `file` .</span><span class="sxs-lookup"><span data-stu-id="8f118-193">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="8f118-194">`name`Öznitelik, yorumlarla önce gelen etiketteki ad belirticisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f118-194">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="8f118-195">Yerine `id` kullanılabilecek özniteliği, `name` yorumların ÖNÜNDEKI etiketin kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f118-195">The `id` attribute, which can be used in place of `name`, represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="8f118-196">Kullanıcı tanımlı Etiketler</span><span class="sxs-lookup"><span data-stu-id="8f118-196">User-defined tags</span></span>

<span data-ttu-id="8f118-197">Yukarıda özetlenen tüm Etiketler, C# derleyicisi tarafından tanınan olanları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f118-197">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="8f118-198">Ancak, bir Kullanıcı kendi etiketlerini tanımlayaücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="8f118-198">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="8f118-199">Sandrole gibi araçlar, ve gibi ekstra Etiketler için destek getirme [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) ve hatta [ad alanlarını belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)desteği.</span><span class="sxs-lookup"><span data-stu-id="8f118-199">Tools like Sandcastle bring support for extra tags like [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) and [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="8f118-200">Özel veya şirket içi belge oluşturma araçları ayrıca standart Etiketler ve HTML 'den PDF 'ye birden çok çıktı biçimi ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-200">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="8f118-201">Öneriler</span><span class="sxs-lookup"><span data-stu-id="8f118-201">Recommendations</span></span>

<span data-ttu-id="8f118-202">Kodu belgeleme pek çok nedenden dolayı önerilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-202">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="8f118-203">Aşağıda, bazı en iyi yöntemler, genel kullanım örneği senaryoları ve C# kodunuzda XML belge etiketlerini kullanırken bilmeniz gereken noktalar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f118-203">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="8f118-204">Tutarlılık açısından, herkese açık olarak görünen tüm türler ve üyeleri açıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f118-204">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="8f118-205">Bunu yapmanız gerekiyorsa, bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="8f118-205">If you must do it, do it all.</span></span>
- <span data-ttu-id="8f118-206">Özel Üyeler ayrıca XML açıklamaları kullanılarak Belgelenebilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-206">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="8f118-207">Ancak bu, kitaplığınızın iç (potansiyel olarak gizli) işleyişini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8f118-207">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="8f118-208">En azından, türler ve üyeleri, `<summary>` IntelliSense için içerik gerektiğinden bir etikete sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f118-208">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="8f118-209">Belge metni tam uyarılarla biten tam tümceler kullanılarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f118-209">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="8f118-210">Kısmi sınıflar tam olarak desteklenir ve belge bilgileri bu tür için tek bir girişte birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8f118-210">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="8f118-211">Derleyici,,,, `<exception>` `<include>` `<param>` `<see>` `<seealso>` ve `<typeparam>` etiketlerinin sözdizimini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8f118-211">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`, and `<typeparam>` tags.</span></span>
- <span data-ttu-id="8f118-212">Derleyici dosya yolları içeren parametreleri ve kodun diğer bölümlerine başvuruları doğrular.</span><span class="sxs-lookup"><span data-stu-id="8f118-212">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f118-213">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f118-213">See also</span></span>

- [<span data-ttu-id="8f118-214">XML Belgeleri Yorumları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8f118-214">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="8f118-215">Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8f118-215">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
