---
title: Kodunuzu XML açıklamalarıyla belgeleme
description: Kodunuzu XML belge açıklamalarıyla belgeleme ve derleme zamanında bir XML belge dosyası oluşturma hakkında bilgi edinin.
ms.date: 02/14/2017
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: c858a92309710a0ac6b68e9194f2d7ef4c9577a0
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140671"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="c8e85-103">Kodunuzu XML açıklamalarıyla belgeleme</span><span class="sxs-lookup"><span data-stu-id="c8e85-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="c8e85-104">XML belge açıklamaları, Kullanıcı tanımlı herhangi bir tür veya üyenin tanımının üzerine eklenen özel bir açıklama türüdür.</span><span class="sxs-lookup"><span data-stu-id="c8e85-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="c8e85-105">Bunlar, derleme zamanında bir XML belge dosyası oluşturmak için derleyici tarafından işlenebilecekleri için özeldir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="c8e85-106">Derleyici tarafından oluşturulan XML dosyası, .NET derlemenizin yanı sıra, Visual Studio ve diğer IDE 'Ler, türler veya üyeler hakkında hızlı bilgileri göstermek için IntelliSense kullanabilmesi için birlikte dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="c8e85-107">Ayrıca, XML dosyası, API başvuru Web siteleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi araçlar aracılığıyla çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="c8e85-108">Tüm diğer yorumlar gibi XML belgesi açıklamaları derleyici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c8e85-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="c8e85-109">XML dosyasını, derleme zamanında aşağıdakilerden birini yaparak oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8e85-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="c8e85-110">Komut satırından .NET Core ile bir uygulama geliştiriyorsanız,. csproj proje dosyanızın `<PropertyGroup>` bölümüne `GenerateDocumentationFile` öğesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="c8e85-111">Belge dosyasının yolunu doğrudan [`DocumentationFile` öğesi](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="c8e85-112">Aşağıdaki örnek, derleme ile aynı kök dosya adına sahip proje dizininde bir XML dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c8e85-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   <span data-ttu-id="c8e85-113">Bu, aşağıdaki gibi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="c8e85-113">This is equivalent to the following:</span></span>
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="c8e85-114">Visual Studio 'Yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayıp **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c8e85-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="c8e85-115">Özellikler iletişim kutusunda **derleme** sekmesini seçin ve **XML belge dosyasını**denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c8e85-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="c8e85-116">Derleyicinin dosyayı yazdıkları konumu da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="c8e85-117">Komut satırından bir .NET Framework uygulaması derlerken, derlerken [-doc derleyici seçeneğini](language-reference/compiler-options/doc-compiler-option.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8e85-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="c8e85-118">XML belge açıklamaları Üçlü eğik çizgi (`///`) ve XML biçimli bir açıklama gövdesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8e85-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="c8e85-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c8e85-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="c8e85-120">Gidiş</span><span class="sxs-lookup"><span data-stu-id="c8e85-120">Walkthrough</span></span>

<span data-ttu-id="c8e85-121">Yeni geliştiricilerin, üçüncü taraf geliştiricilerin kullanması için ve katkıda bulunmak amacıyla çok basit bir matematik kitaplığını belgeleme konusunda bilgi verlim.</span><span class="sxs-lookup"><span data-stu-id="c8e85-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="c8e85-122">Basit matematik kitaplığı için kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c8e85-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="c8e85-123">Örnek kitaplık, `int` ve `double` veri türlerinde `add`, `subtract`, `multiply` ve `divide` dört önemli aritmetik işlemi destekler.</span><span class="sxs-lookup"><span data-stu-id="c8e85-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="c8e85-124">Şimdi, kitaplığınızı kullanan ancak kaynak koda erişiminiz olmayan üçüncü taraf geliştiriciler için kodınızdan bir API başvuru belgesi oluşturabiliyor olmanız istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="c8e85-125">Daha önce bahsedilen XML belge etiketleri bunu elde etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="c8e85-126">Artık C# derleyicinin DESTEKLEDIĞI standart XML etiketlerine tanıtılıcaksınız.</span><span class="sxs-lookup"><span data-stu-id="c8e85-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="c8e85-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="c8e85-127">\<summary></span></span>

<span data-ttu-id="c8e85-128">`<summary>` etiketi, bir tür veya üye hakkında kısa bilgiler ekler.</span><span class="sxs-lookup"><span data-stu-id="c8e85-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="c8e85-129">`Math` sınıf tanımına ve ilk `Add` yöntemine ekleyerek kullanımını göstereceğim.</span><span class="sxs-lookup"><span data-stu-id="c8e85-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="c8e85-130">Kodunuzu geri kalanına uygulamayı ücretsiz olarak hissetmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="c8e85-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="c8e85-131">`<summary>` etiketi çok önemlidir ve içeriği, IntelliSense 'de veya bir API başvuru belgesinde bulunan içerik veya üye bilgilerinin birincil kaynağı olduğundan, bunu dahil etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-131">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8e85-132">\<remarks ></span><span class="sxs-lookup"><span data-stu-id="c8e85-132">\<remarks></span></span>

<span data-ttu-id="c8e85-133">`<remarks>` etiketi, `<summary>` etiketinin sağladığı türler veya Üyeler hakkındaki bilgileri tamamlar.</span><span class="sxs-lookup"><span data-stu-id="c8e85-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="c8e85-134">Bu örnekte, bunu yalnızca sınıfına eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="c8e85-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="c8e85-135">\<returns></span></span>

<span data-ttu-id="c8e85-136">`<returns>` etiketi bir yöntem bildiriminin dönüş değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8e85-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="c8e85-137">Daha önce olduğu gibi, aşağıdaki örnek ilk `Add` yönteminde `<returns>` etiketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="c8e85-138">Diğer yöntemlerle aynı şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="c8e85-139">\<value></span><span class="sxs-lookup"><span data-stu-id="c8e85-139">\<value></span></span>

<span data-ttu-id="c8e85-140">`<value>` etiketi, özellikler için kullanmanız dışında `<returns>` etiketine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="c8e85-141">`Math` kitaplığınızın `PI`adında bir statik özelliği olduğunu varsayarsak, bu etiketi nasıl kullanacağınızı aşağıda bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8e85-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="c8e85-142">\<example ></span><span class="sxs-lookup"><span data-stu-id="c8e85-142">\<example></span></span>

<span data-ttu-id="c8e85-143">XML belgelerinize bir örnek eklemek için `<example>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8e85-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="c8e85-144">Bu, alt `<code>` etiketinin kullanılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="c8e85-145">`code` etiketi, daha uzun örnekler için satır sonlarını ve girintiyi korur.</span><span class="sxs-lookup"><span data-stu-id="c8e85-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="c8e85-146">\<para ></span><span class="sxs-lookup"><span data-stu-id="c8e85-146">\<para></span></span>

<span data-ttu-id="c8e85-147">İçeriği üst etiketi içinde biçimlendirmek için `<para>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8e85-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="c8e85-148">`<para>`, genellikle metni paragraflarına bölmek için `<remarks>` veya `<returns>` gibi bir etiket içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8e85-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="c8e85-149">Sınıf tanımınız için `<remarks>` etiketinin içeriğini biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="c8e85-150">\<c ></span><span class="sxs-lookup"><span data-stu-id="c8e85-150">\<c></span></span>

<span data-ttu-id="c8e85-151">Biçimlendirme konusunda hala, metnin bir kısmını kod olarak işaretlemek için `<c>` etiketini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c8e85-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="c8e85-152">`<code>` etiketi, ancak satır içi gibi.</span><span class="sxs-lookup"><span data-stu-id="c8e85-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="c8e85-153">Bir etiketin içeriğinin bir parçası olarak hızlı bir kod örneği göstermek istediğinizde yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="c8e85-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="c8e85-154">`Math` sınıfının belgelerini güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="c8e85-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="c8e85-155">\<exception ></span><span class="sxs-lookup"><span data-stu-id="c8e85-155">\<exception></span></span>

<span data-ttu-id="c8e85-156">`<exception>` etiketini kullanarak, geliştiricilerinizin bir yöntemin belirli özel durumları oluşturduğunu bilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="c8e85-157">`Math` kitaplığınıza baktığınızda, her iki `Add` yönteminin da belirli bir koşul karşılanırsa bir özel durum oluşturmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="c8e85-158">Öyle değildir, ancak `b` parametresi sıfır ise tamsayı `Divide` yöntemi de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8e85-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="c8e85-159">Şimdi bu yönteme özel durum belgeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8e85-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="c8e85-160">`cref` özniteliği geçerli derleme ortamında kullanılabilir bir özel duruma bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8e85-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="c8e85-161">Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="c8e85-162">Değeri çözülemezse, derleyici bir uyarı verebilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="c8e85-163">\<see ></span><span class="sxs-lookup"><span data-stu-id="c8e85-163">\<see></span></span>

<span data-ttu-id="c8e85-164">`<see>` etiketi, başka bir kod öğesi için bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8e85-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="c8e85-165">Sonraki örnekte, iki `Add` yöntemi arasında tıklatılabilir bir bağlantı oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="c8e85-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="c8e85-166">`cref`, geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eden **gerekli** bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="c8e85-167">Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="c8e85-168">\<seealso ></span><span class="sxs-lookup"><span data-stu-id="c8e85-168">\<seealso></span></span>

<span data-ttu-id="c8e85-169">`<seealso>` etiketini `<see>` etiketiyle aynı şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c8e85-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="c8e85-170">Tek fark, içeriğinin genellikle bir "Ayrıca bkz." bölümüne yerleştirilme nedendir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="c8e85-171">Burada, tamsayı parametrelerini kabul eden sınıftaki diğer yöntemlere başvurmak için tamsayı `Add` yöntemine bir `seealso` etiketi ekleyeceğiz:</span><span class="sxs-lookup"><span data-stu-id="c8e85-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="c8e85-172">`cref` özniteliği, geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8e85-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="c8e85-173">Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="c8e85-174">\<param></span><span class="sxs-lookup"><span data-stu-id="c8e85-174">\<param></span></span>

<span data-ttu-id="c8e85-175">Metodun parametrelerini anlatmak için `<param>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8e85-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="c8e85-176">Double `Add` yöntemine bir örnek aşağıda verilmiştir: etiketin açıkladığı parametre, **gerekli** `name` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="c8e85-177">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="c8e85-177">\<typeparam></span></span>

<span data-ttu-id="c8e85-178">`<typeparam>` etiketini `<param>` etiketi gibi kullanırsınız, ancak genel tür veya yöntem bildirimlerinde genel bir parametreyi betimleyelim.</span><span class="sxs-lookup"><span data-stu-id="c8e85-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="c8e85-179">Bir miktarın diğerinden daha büyük olup olmadığını denetlemek için `Math` sınıfınıza hızlı genel bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8e85-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="c8e85-180">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="c8e85-180">\<paramref></span></span>

<span data-ttu-id="c8e85-181">Bazen, bir yöntemin `<summary>` bir etiketle ne olduğunu açıklayan ortasında olabilirsiniz ve bir parametreye başvuru yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="c8e85-182">`<paramref>` etiketi yalnızca bunun için harika.</span><span class="sxs-lookup"><span data-stu-id="c8e85-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="c8e85-183">Double tabanlı `Add` yönteminizin özetini güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="c8e85-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="c8e85-184">`<param>` etiketi gibi, **gerekli** `name` özniteliğinde parametre adı belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-184">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="c8e85-185">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="c8e85-185">\<typeparamref></span></span>

<span data-ttu-id="c8e85-186">`<typeparamref>` etiketini `<paramref>` etiketi gibi kullanırsınız, ancak genel tür veya yöntem bildirimlerinde genel bir parametreyi betimleyelim.</span><span class="sxs-lookup"><span data-stu-id="c8e85-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="c8e85-187">Daha önce oluşturduğunuz genel yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="c8e85-188">\<list ></span><span class="sxs-lookup"><span data-stu-id="c8e85-188">\<list></span></span>

<span data-ttu-id="c8e85-189">Belge bilgilerini sıralı liste, sırasız liste veya tablo olarak biçimlendirmek için `<list>` etiketini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c8e85-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="c8e85-190">`Math` kitaplığınızın desteklediği her matematik işleminin sıralanmamış bir listesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8e85-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="c8e85-191">`type` özniteliğini sırasıyla `number` veya `table`olarak değiştirerek sıralı bir liste veya tablo yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="c8e85-192">Tümünü bir araya getirme</span><span class="sxs-lookup"><span data-stu-id="c8e85-192">Putting it all together</span></span>

<span data-ttu-id="c8e85-193">Bu öğreticiyi takip ediyorsanız ve gereken yere etiketleri kodunuza uyguladıysanız, kodunuzun aşağıdakine benzer şekilde görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="c8e85-193">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="c8e85-194">Kodınızdan, tıklatılabilir çapraz başvurularla ayrıntılı bir belge Web sitesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-194">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="c8e85-195">Ancak başka bir sorunla karşılaşıyoruz: kodunuzun okunması zor oldu.</span><span class="sxs-lookup"><span data-stu-id="c8e85-195">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="c8e85-196">Bu koda katkıda bulunmak isteyen herhangi bir geliştirici için bu bir gece olacak şekilde, bu kadar çok bilgi vardır.</span><span class="sxs-lookup"><span data-stu-id="c8e85-196">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="c8e85-197">Bu konuda size yardımcı olabilecek bir XML etiketi vardı:</span><span class="sxs-lookup"><span data-stu-id="c8e85-197">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="c8e85-198">\<include ></span><span class="sxs-lookup"><span data-stu-id="c8e85-198">\<include></span></span>

<span data-ttu-id="c8e85-199">`<include>` etiketi, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeyi tersine, kaynak kodunuzda türleri ve üyeleri tanımlayan ayrı bir XML dosyasındaki açıklamalara başvurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8e85-199">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="c8e85-200">Artık tüm XML etiketlerinizi `docs.xml` adlı ayrı bir XML dosyasına taşıyacağız.</span><span class="sxs-lookup"><span data-stu-id="c8e85-200">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="c8e85-201">Dosyayı istediğiniz şekilde adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-201">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="c8e85-202">Yukarıdaki XML 'de, her üyenin belge yorumu, ne yapacaklarıyla doğrudan adlı bir etiketin içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="c8e85-202">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="c8e85-203">Kendi stratejinizi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-203">You can choose your own strategy.</span></span>
<span data-ttu-id="c8e85-204">XML yorumlarınıza artık ayrı bir dosyada sahip olduğunuza göre, kodunuzun `<include>` etiketi kullanılarak nasıl daha okunaklı hale getirildikimi görelim:</span><span class="sxs-lookup"><span data-stu-id="c8e85-204">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="c8e85-205">Bu durumda: kodunuz okunabilir hale getirilir ve belge bilgisi kaybedilmiyor.</span><span class="sxs-lookup"><span data-stu-id="c8e85-205">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="c8e85-206">`file` öznitelik, belgeleri içeren XML dosyasının adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8e85-206">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="c8e85-207">`path` öznitelik, belirtilen `file`mevcut `tag name` bir [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) sorgusunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8e85-207">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="c8e85-208">`name` özniteliği, etiketteki açıklamaların önündeki ad belirticisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8e85-208">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="c8e85-209">`name` yerine kullanılabilecek `id` özniteliği, yorumların önündeki etiketin KIMLIĞINI temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8e85-209">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="c8e85-210">Kullanıcı tanımlı Etiketler</span><span class="sxs-lookup"><span data-stu-id="c8e85-210">User Defined Tags</span></span>

<span data-ttu-id="c8e85-211">Yukarıda özetlenen tüm Etiketler, C# derleyici tarafından tanınan olanları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8e85-211">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="c8e85-212">Ancak, bir Kullanıcı kendi etiketlerini tanımlayaücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-212">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="c8e85-213">Sandrole gibi Araçlar [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) gibi ek Etiketler için destek getirme ve hatta [ad alanlarını belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)desteği.</span><span class="sxs-lookup"><span data-stu-id="c8e85-213">Tools like Sandcastle bring support for extra tags like [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="c8e85-214">Özel veya şirket içi belge oluşturma araçları ayrıca standart Etiketler ve HTML 'den PDF 'ye birden çok çıktı biçimi ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-214">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="c8e85-215">Öneri</span><span class="sxs-lookup"><span data-stu-id="c8e85-215">Recommendations</span></span>

<span data-ttu-id="c8e85-216">Kodu belgeleme pek çok nedenden dolayı önerilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-216">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="c8e85-217">Aşağıda, bazı en iyi yöntemler, genel kullanım örneği senaryoları ve C# kodunuzda XML belge etiketlerini kullanırken bilmeniz gereken noktalar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-217">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="c8e85-218">Tutarlılık açısından, herkese açık olarak görünen tüm türler ve üyeleri açıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8e85-218">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="c8e85-219">Bunu yapmanız gerekiyorsa, bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="c8e85-219">If you must do it, do it all.</span></span>
- <span data-ttu-id="c8e85-220">Özel Üyeler ayrıca XML açıklamaları kullanılarak Belgelenebilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-220">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="c8e85-221">Ancak bu, kitaplığınızın iç (potansiyel olarak gizli) işleyişini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c8e85-221">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="c8e85-222">İçerik IntelliSense için gerekli olduğundan, en azından, türlerin ve üyelerinin `<summary>` bir etiketi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8e85-222">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="c8e85-223">Belge metni tam uyarılarla biten tam tümceler kullanılarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8e85-223">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="c8e85-224">Kısmi sınıflar tam olarak desteklenir ve belge bilgileri bu tür için tek bir girişte birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8e85-224">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="c8e85-225">Derleyici `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` ve `<typeparam>` etiketlerinin sözdizimini doğrular.</span><span class="sxs-lookup"><span data-stu-id="c8e85-225">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="c8e85-226">Derleyici dosya yolları içeren parametreleri ve kodun diğer bölümlerine başvuruları doğrular.</span><span class="sxs-lookup"><span data-stu-id="c8e85-226">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8e85-227">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e85-227">See also</span></span>

- [<span data-ttu-id="c8e85-228">XML belge açıklamaları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c8e85-228">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="c8e85-229">Belge açıklamaları için önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c8e85-229">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
