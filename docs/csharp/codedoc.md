---
title: XML açıklamalarıyla kodunuzu belgeleme
description: XML belgeleri yorumları ile kodunuzu belgeleme ve derleme zamanında XML belge dosyası oluşturma hakkında bilgi edinin.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: e211543a6a5cc5f6f29d8c195492b474eb24a38d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397065"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="06f9b-103">XML açıklamalarıyla kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="06f9b-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="06f9b-104">XML belgeleri yorumları herhangi bir kullanıcı tanımlı tür veya üye tanımı eklenen açıklama, özel bir tür var.</span><span class="sxs-lookup"><span data-stu-id="06f9b-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="06f9b-105">Derleme zamanında XML belge dosyası oluşturmak için derleyici tarafından işlenebilir çünkü bunlar özeldir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="06f9b-106">Böylece Visual Studio ve diğer Ide'leri IntelliSense türleri veya üyeleri hakkında hızlı bilgi göstermek için kullanabilirsiniz, derleyicinin ürettiği XML dosyasının yanı sıra .NET bütünleştirilmiş kodunuzda dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="06f9b-107">Ayrıca, XML dosyasını gibi araçlarla çalıştırılabilir [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) API Başvurusu Web siteleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="06f9b-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="06f9b-108">XML belgeleri yorumları, diğer açıklamaları gibi derleyici tarafından göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="06f9b-109">XML dosyası, aşağıdakilerden birini yaparak, bir derleme zamanında oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="06f9b-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="06f9b-110">Ekleyebileceğiniz komut satırından .NET Core ile bir uygulama varsa geliştiriyorsanız, bir [DocumentationFile öğesi](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) için `<PropertyGroup>` .csproj proje dosyanızın bölümü.</span><span class="sxs-lookup"><span data-stu-id="06f9b-110">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="06f9b-111">Aşağıdaki örnek, proje dizinine derleme olarak aynı kök dosya adına sahip bir XML dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="06f9b-111">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="06f9b-112">XML dosyasının adını ve tam mutlak veya göreli yolu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-112">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="06f9b-113">Aşağıdaki örnek, bir uygulamanın hata ayıklama sürümü ile aynı dizinde XML dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="06f9b-113">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="06f9b-114">Visual Studio kullanarak bir uygulama geliştiriyorsanız sağ tıklatın ve proje **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="06f9b-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="06f9b-115">Özellikler iletişim kutusunda, seçmek **derleme** sekmesini tıklatıp denetleyin **XML belge dosyası**.</span><span class="sxs-lookup"><span data-stu-id="06f9b-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="06f9b-116">Ayrıca, derleyici dosyayı yazacağı konum değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="06f9b-117">Bir .NET Framework uygulamasına komut satırından derleme yapıyorsanız ekleme [/doc derleyici seçeneği](language-reference/compiler-options/doc-compiler-option.md) derlenirken.</span><span class="sxs-lookup"><span data-stu-id="06f9b-117">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="06f9b-118">XML belgeleri yorumları üç eğik çizgi kullanın (`///`) ve bir XML biçimli yorum gövdesi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="06f9b-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="06f9b-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="06f9b-120">İzlenecek yol</span><span class="sxs-lookup"><span data-stu-id="06f9b-120">Walkthrough</span></span>

<span data-ttu-id="06f9b-121">Anlama ve katkıda yeni geliştiricilerin ve üçüncü taraf geliştiriciler için kolaylaştıran bir çok temel matematik kitaplığı belgeleme aracılığıyla atalım.</span><span class="sxs-lookup"><span data-stu-id="06f9b-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="06f9b-122">Kodu basit matematik kitaplığı şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="06f9b-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="06f9b-123">Örnek kitaplığı dört temel aritmetik işlemleri destekler `add`, `subtract`, `multiply` ve `divide` üzerinde `int` ve `double` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="06f9b-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="06f9b-124">Artık kitaplığınızı kullanan ancak kaynak koduna erişiminiz yoksa üçüncü taraf geliştiriciler için kodunuzdan bir API başvuru belgesi oluşturmak yönetebilmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="06f9b-125">Bunu başarmak için belirtilen önceki XML belge etiketleri kullanılabileceğinden, standart XML etiketlerini C# Derleyici destekler artık sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="06f9b-125">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="06f9b-126">&lt;Özeti&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-126">&lt;summary&gt;</span></span>

<span data-ttu-id="06f9b-127">`<summary>` Etiketi bir tür veya üye hakkında kısa bilgiler ekler.</span><span class="sxs-lookup"><span data-stu-id="06f9b-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="06f9b-128">Ben ekleyerek kullanımını kazandırabileceğinizi göstereceğiz `Math` sınıf tanımı ve ilk `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="06f9b-129">Kodunuzun geri kalanı için geçerli çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="06f9b-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="06f9b-130">`<summary>` Etiketi çok önemlidir ve içeriği IntelliSense ya da bir API başvuru belgesini türe veya üyeye bilgilerinin birincil kaynağı olduğundan, dahil öneririz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-130">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="06f9b-131">&lt;Açıklamalar&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-131">&lt;remarks&gt;</span></span>

<span data-ttu-id="06f9b-132">`<remarks>` Etiketi tamamlayan türleri veya üyeleri hakkında bilgi, `<summary>` etiketi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06f9b-132">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="06f9b-133">Bu örnekte, yalnızca bu sınıfa ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-133">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a><span data-ttu-id="06f9b-134">&lt;döndürür&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-134">&lt;returns&gt;</span></span>

<span data-ttu-id="06f9b-135">`<returns>` Etiketi dönüş değeri bir yöntem bildiriminde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06f9b-135">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="06f9b-136">Önce aşağıdaki örnekte gösterildiği gibi `<returns>` ilk etiket `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-136">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="06f9b-137">Diğer yöntemler hakkında aynısını yapabilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-137">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a><span data-ttu-id="06f9b-138">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-138">&lt;value&gt;</span></span>

<span data-ttu-id="06f9b-139">`<value>` Etiketi benzer `<returns>` özelliklerini kullanmasını dışında etiketleyin.</span><span class="sxs-lookup"><span data-stu-id="06f9b-139">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="06f9b-140">Varsayarak, `Math` kitaplığı adlı statik bir özellik olan `PI`, İşte bu etiketi nasıl kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="06f9b-140">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a><span data-ttu-id="06f9b-141">&lt;Örnek&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-141">&lt;example&gt;</span></span>

<span data-ttu-id="06f9b-142">Kullandığınız `<example>` örneği, XML belgelerinde dahil etmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="06f9b-142">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="06f9b-143">Bu alt kullanılmasına `<code>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-143">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="06f9b-144">`code` Etiketi satır sonu ve girinti uzun örnekleri için korur.</span><span class="sxs-lookup"><span data-stu-id="06f9b-144">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="06f9b-145">&lt;para&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-145">&lt;para&gt;</span></span>

<span data-ttu-id="06f9b-146">Kullandığınız `<para>` kendi üst etiketinin içinde içeriği biçimlendirmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="06f9b-146">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="06f9b-147">`<para>` genellikle gibi bir etiket içinde kullanılan `<remarks>` veya `<returns>`paragraflara metin ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="06f9b-147">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="06f9b-148">İçeriğini biçimlendirebilirsiniz `<remarks>` sınıfı tanımınız için etiket.</span><span class="sxs-lookup"><span data-stu-id="06f9b-148">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a><span data-ttu-id="06f9b-149">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-149">&lt;c&gt;</span></span>

<span data-ttu-id="06f9b-150">Biçimlendirme hala konusu, kullandığınız `<c>` metin olarak kod parçası olarak işaretlemek için etiket.</span><span class="sxs-lookup"><span data-stu-id="06f9b-150">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="06f9b-151">Nasıl olduğunu `<code>` etiketi ancak satır içi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-151">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="06f9b-152">Hızlı kod örneği bir etiketin içeriği bir parçası olarak göstermek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="06f9b-152">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="06f9b-153">Belgelerine güncelleştirelim `Math` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="06f9b-153">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a><span data-ttu-id="06f9b-154">&lt;özel durum&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-154">&lt;exception&gt;</span></span>

<span data-ttu-id="06f9b-155">Kullanarak `<exception>` etiketi, bir yöntemi özel durum oluşturabilecek, geliştiricilere sağlar.</span><span class="sxs-lookup"><span data-stu-id="06f9b-155">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="06f9b-156">Bakarak, `Math` kitaplığı, gördüğünüz gibi her ikisi de `Add` yöntemleri, belirli bir koşul karşılandığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06f9b-156">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="06f9b-157">Değil yine de o kadar belirgin tamsayıdır `Divide` yöntemi oluşturursa yanı, `b` parametresi sıfırsa.</span><span class="sxs-lookup"><span data-stu-id="06f9b-157">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="06f9b-158">Artık özel durum belgeleri bu yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06f9b-158">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="06f9b-159">`cref` Öznitelik geçerli derleme ortamdan kullanılabilir bir özel durum başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06f9b-159">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="06f9b-160">Bu proje ya da başvurulan bir derlemede tanımlanan herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-160">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="06f9b-161">Değerini çözümlenemezse, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-161">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="06f9b-162">&lt;Bkz:&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-162">&lt;see&gt;</span></span>

<span data-ttu-id="06f9b-163">`<see>` Etiketi başka bir kod öğesi için bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="06f9b-163">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="06f9b-164">Sonraki Örneğimizde, ikisi arasındaki tıklatılabilir bir bağlantı oluşturacağız `Add` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="06f9b-164">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="06f9b-165">`cref` Olduğu bir **gerekli** temsil eden bir tür veya geçerli derleme ortamdan kullanılabilir olan kendi üyesi başvuru özniteliği.</span><span class="sxs-lookup"><span data-stu-id="06f9b-165">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="06f9b-166">Bu proje ya da başvurulan bir derlemede tanımlanan herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-166">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="06f9b-167">&lt;SeeAlso&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-167">&lt;seealso&gt;</span></span>

<span data-ttu-id="06f9b-168">Kullandığınız `<seealso>` bunu aynı şekilde etiketi `<see>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-168">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="06f9b-169">Tek fark, içeriği genellikle "bir Ayrıca bkz:" bölümünde yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-169">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="06f9b-170">Buraya ekleyeceğiz bir `seealso` üzerinde tamsayı etiketi `Add` tamsayı parametre kabul eden diğer sınıfı yöntemleri başvurmak için yöntemi:</span><span class="sxs-lookup"><span data-stu-id="06f9b-170">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="06f9b-171">`cref` Öznitelik, bir tür veya geçerli derleme ortamdan kullanılabilir olan kendi üyesi başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06f9b-171">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="06f9b-172">Bu proje ya da başvurulan bir derlemede tanımlanan herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-172">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="06f9b-173">&lt;param&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-173">&lt;param&gt;</span></span>

<span data-ttu-id="06f9b-174">Kullandığınız `<param>` bir yöntemin parametre açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="06f9b-174">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="06f9b-175">İşte bir örnek üzerinde iki `Add` yöntemi: Etiket açıklar parametresi belirtildiğinden **gerekli** `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="06f9b-175">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a><span data-ttu-id="06f9b-176">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-176">&lt;typeparam&gt;</span></span>

<span data-ttu-id="06f9b-177">Kullandığınız `<typeparam>` tıpkı etiketi `<param>` etiketi ancak genel parametre açıklamak genel tür veya yöntem bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="06f9b-177">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="06f9b-178">Hızlı bir genel yöntem ekleme, `Math` bir miktar diğerinden daha büyük olup olmadığı denetlenecek sınıfı.</span><span class="sxs-lookup"><span data-stu-id="06f9b-178">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a><span data-ttu-id="06f9b-179">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-179">&lt;paramref&gt;</span></span>

<span data-ttu-id="06f9b-180">Bazen ne olabilir bir yöntem ne yaptığını açıklayan ortasında olabilir bir `<summary>` etiketi ve parametre başvurusu yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-180">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="06f9b-181">`<paramref>` Etikettir yalnızca bu harika.</span><span class="sxs-lookup"><span data-stu-id="06f9b-181">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="06f9b-182">Şimdi güncelleştirme özeti sayfamızda çift tabanlı `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-182">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="06f9b-183">Gibi `<param>` parametre adı belirtilen etiketi **gerekli** `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="06f9b-183">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a><span data-ttu-id="06f9b-184">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-184">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="06f9b-185">Kullandığınız `<typeparamref>` tıpkı etiketi `<paramref>` etiketi ancak genel parametre açıklamak genel tür veya yöntem bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="06f9b-185">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="06f9b-186">Daha önce oluşturduğunuz genel aynı yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-186">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a><span data-ttu-id="06f9b-187">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-187">&lt;list&gt;</span></span>

<span data-ttu-id="06f9b-188">Kullandığınız `<list>` etiket biçimi belgeleri bilgilerine bir sıralı liste, sırasız liste veya tablo.</span><span class="sxs-lookup"><span data-stu-id="06f9b-188">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="06f9b-189">Sırasız bir listesini her matematik işleminin olun, `Math` kitaplığı destekler.</span><span class="sxs-lookup"><span data-stu-id="06f9b-189">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="06f9b-190">Bir sıralı listeyi veya tabloyu değiştirerek yapabilirsiniz `type` özniteliğini `number` veya `table`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="06f9b-190">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="06f9b-191">Hepsini birleştirme</span><span class="sxs-lookup"><span data-stu-id="06f9b-191">Putting it all together</span></span>

<span data-ttu-id="06f9b-192">Bu öğreticiyi takip ve gerektiğinde etiketleri, koda uygulandı, kodunuzun aşağıdakine benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="06f9b-192">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="06f9b-193">Kodunuz aracılığıyla ayrıntılı belgeler Web sitesi ile tıklanabilir çapraz tam oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-193">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="06f9b-194">Ancak başka bir sorun yaşadığınız: kodunuzu okunması zor hale geldi.</span><span class="sxs-lookup"><span data-stu-id="06f9b-194">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="06f9b-195">Bu bir onarımı kabus bu koda katkıda bulunmak isteyen bir geliştirici olarak gittiği çalışılamayacak için çok fazla bilgi bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06f9b-195">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="06f9b-196">Ne yapmam yardımcı olabilecek bir XML etiket vardır:</span><span class="sxs-lookup"><span data-stu-id="06f9b-196">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="06f9b-197">&lt;İçerir&gt;</span><span class="sxs-lookup"><span data-stu-id="06f9b-197">&lt;include&gt;</span></span>

<span data-ttu-id="06f9b-198">`<include>` Etiket türleri açıklayan yorumlar ayrı bir XML dosyasında ve doğrudan sizin kaynak kodu dosyasında belge açıklamaları yerleştirme aksine, kaynak kodunuzdaki üyelerine başvurmak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="06f9b-198">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="06f9b-199">Tüm XML etiketlerini adlı ayrı bir XML dosyasına taşımak soracağız `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="06f9b-199">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="06f9b-200">İstediğiniz dosya adı çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="06f9b-200">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="06f9b-201">Yukarıdaki XML'de her üyenin belge açıklamaları doğrudan yapabileceklerini sonra adlı bir etiket içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="06f9b-201">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="06f9b-202">Kendi stratejisi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-202">You can choose your own strategy.</span></span>
<span data-ttu-id="06f9b-203">Ayrı bir dosyada XML yorumlarınızı sahip olduğunuza göre şimdi nasıl kodunuzu kullanarak daha okunabilir hale getirilebilir bakalım `<include>` etiketi:</span><span class="sxs-lookup"><span data-stu-id="06f9b-203">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="06f9b-204">Ve elinizde vardır: okunabilir olan geri kodumuz olduğundan ve hiçbir belge bilgi kaybı olmadı.</span><span class="sxs-lookup"><span data-stu-id="06f9b-204">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="06f9b-205">`filename` Öznitelik belgeleri içeren XML dosyasının adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06f9b-205">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="06f9b-206">`path` Özniteliğini temsil eder bir [XPath](https://msdn.microsoft.com/library/ms256115.aspx) için sorgu `tag name` belirtilen mevcut `filename`.</span><span class="sxs-lookup"><span data-stu-id="06f9b-206">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="06f9b-207">`name` Öznitelik ad tanımlayıcısı açıklamaları önündeki etiketinde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06f9b-207">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="06f9b-208">`id` Yerine kullanılan öznitelik `name` açıklamaları önünde etiket Kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06f9b-208">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="06f9b-209">Kullanıcı tanımlı etiketleri</span><span class="sxs-lookup"><span data-stu-id="06f9b-209">User Defined Tags</span></span>

<span data-ttu-id="06f9b-210">Yukarıda özetlenen tüm etiketleri, C# derleyicisi tarafından tanınmaktadır temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06f9b-210">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="06f9b-211">Ancak, bir kullanıcı kendi etiketleri tanımlamak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-211">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="06f9b-212">Sandcastle gibi araçları ister ek etiketleri için destek Getir [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) ve hatta Destek [ad alanları belgeleme](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="06f9b-212">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="06f9b-213">Özel veya şirket içi belge oluşturma araçları ile standart etiketleri de kullanılabilir ve HTML'den PDF birden çok çıkış biçimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-213">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="06f9b-214">Önerileri</span><span class="sxs-lookup"><span data-stu-id="06f9b-214">Recommendations</span></span>

<span data-ttu-id="06f9b-215">Kod belgeleme çeşitli nedenlerle önerilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-215">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="06f9b-216">Aşağıda bazı en iyi yöntemler, genel örneği senaryolarını ve ne zaman XML belgeleri kullanarak etiketleri, C# kodunuzda bilmeniz gerekenler şeyler kullanın.</span><span class="sxs-lookup"><span data-stu-id="06f9b-216">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="06f9b-217">Tutarlılık sağlamak, tüm genel olarak görülebilir tür ve üyelerin belgelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-217">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="06f9b-218">Bunu yapmanız gerekir, tüm yapın.</span><span class="sxs-lookup"><span data-stu-id="06f9b-218">If you must do it, do it all.</span></span>
* <span data-ttu-id="06f9b-219">Ayrıca özel üyeler XML açıklamaları kullanarak da belgelenecektir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-219">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="06f9b-220">Ancak, bunu kitaplığınızın (büyük olasılıkla gizli) çalışmalar kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="06f9b-220">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="06f9b-221">Çıplak en azından, türleri ve üyeleri olmalıdır bir `<summary>` içeriği için IntelliSense gerektiğinden etiketleyin.</span><span class="sxs-lookup"><span data-stu-id="06f9b-221">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="06f9b-222">Tam durakları ile biten bütün cümleleri kullanarak belge metnini yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-222">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="06f9b-223">Kısmi sınıflar tam olarak desteklenir ve belgelendirme bilgilerini tek bir giriş türü için içine birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="06f9b-223">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="06f9b-224">Derleyici sözdizimini doğrular `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` ve `<typeparam>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="06f9b-224">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="06f9b-225">Derleyici dosya yolları ve kodun diğer bölümleri için başvuruları içeren parametrelerini doğrular.</span><span class="sxs-lookup"><span data-stu-id="06f9b-225">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="06f9b-226">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06f9b-226">See also</span></span>

* [<span data-ttu-id="06f9b-227">XML belgeleri yorumları (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="06f9b-227">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)
* [<span data-ttu-id="06f9b-228">Belge açıklamaları (C# programlama Kılavuzu) için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="06f9b-228">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
