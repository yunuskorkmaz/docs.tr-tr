---
title: XML açıklamaları ile kodunuzu belgeleme
description: XML belgeleri yorumları ile kodunuzu belgeleme ve derleme zamanında XML belge dosyası oluşturma hakkında bilgi edinin.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1284f179c7debb323ea3bbd302df1f02bf8b31b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218511"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="089a1-103">XML açıklamaları ile kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="089a1-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="089a1-104">XML belgeleri yorumları açıklama, herhangi bir kullanıcı tanımlı tür veya üye tanımı eklendi özel bir tür var.</span><span class="sxs-lookup"><span data-stu-id="089a1-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span> <span data-ttu-id="089a1-105">Derleme zamanında XML belge dosyası oluşturmak için derleyici tarafından işlenebilir çünkü bunlar özel.</span><span class="sxs-lookup"><span data-stu-id="089a1-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="089a1-106">Visual Studio ve diğer IDE IntelliSense türler veya üyeler hakkında hızlı bilgi göstermek için kullanabilmesi için oluşturulan derleyici XML dosyası yanı sıra, .NET derleme dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="089a1-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="089a1-107">Ayrıca, XML dosyası gibi araçlar aracılığıyla çalıştırılabilir [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) API başvuru Web siteleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="089a1-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="089a1-108">XML belgeleri yorumları, diğer tüm yorumlar gibi derleyici tarafından göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="089a1-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="089a1-109">Aşağıdakilerden birini yaparak derleme zamanında XML dosyası oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="089a1-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="089a1-110">Ekleyebileceğiniz, .NET Core uygulamayla komut satırından geliştirmekte olduğunuz varsa, bir [DocumentationFile öğesi](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) için `<PropertyGroup>` .csproj proje dosyanızı bölümü.</span><span class="sxs-lookup"><span data-stu-id="089a1-110">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="089a1-111">Aşağıdaki örnek, aynı kök filename derlemeyle ile proje dizininde bir XML dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="089a1-111">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="089a1-112">XML dosyasının adı ve tam mutlak veya göreli yolunu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-112">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="089a1-113">Aşağıdaki örnek, bir uygulamanın hata ayıklama sürümü ile aynı dizinde XML dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="089a1-113">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="089a1-114">Visual Studio kullanarak bir uygulama geliştiriyorsanız, sağ tıklatın ve proje **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="089a1-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="089a1-115">Özellikler iletişim kutusunda seçin **yapı** sekmesini tıklatın ve denetleme **XML belge dosyası**.</span><span class="sxs-lookup"><span data-stu-id="089a1-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="089a1-116">Ayrıca, dosyanın derleyici yazacağı konumu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-116">You can also change the location to which the compiler writes the file.</span></span> 

- <span data-ttu-id="089a1-117">Bir .NET Framework uygulamasını komut satırından derleme varsa ekleyin [/doc derleyici seçeneği](language-reference/compiler-options/doc-compiler-option.md) derlerken.</span><span class="sxs-lookup"><span data-stu-id="089a1-117">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="089a1-118">XML belgeleri yorumları Üçlü eğik kullanın (`///`) ve bir XML açıklama gövdesini biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="089a1-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="089a1-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="089a1-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="089a1-120">İzlenecek yol</span><span class="sxs-lookup"><span data-stu-id="089a1-120">Walkthrough</span></span>

<span data-ttu-id="089a1-121">Şimdi yeni geliştiricilerin anlamak ve katkıda ve kullanmak üçüncü taraf geliştiriciler için kolaylaştırmak için bir temel matematik kitaplığı belgeleme aracılığıyla yol.</span><span class="sxs-lookup"><span data-stu-id="089a1-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="089a1-122">Kod basit matematik kitaplığı aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="089a1-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="089a1-123">Dört ana aritmetik işlemler örnek kitaplığı destekleyen `add`, `subtract`, `multiply` ve `divide` üzerinde `int` ve `double` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="089a1-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="089a1-124">Şimdi bir API başvuru belge kitaplığınızın kullanır ancak kaynak kodu erişiminiz yoksa üçüncü taraf geliştiriciler için kodunuzdan oluşturmak kullanabilmek ister.</span><span class="sxs-lookup"><span data-stu-id="089a1-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="089a1-125">Bunu başarmak için belirtilen önceki XML belge etiketleri kullanılabilir gibi standart XML etiketleri C# Derleyici destekler şimdi görülecektir.</span><span class="sxs-lookup"><span data-stu-id="089a1-125">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="089a1-126">&lt;Özet&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-126">&lt;summary&gt;</span></span>

<span data-ttu-id="089a1-127">`<summary>` Etiketi bir tür veya üye hakkında kısa bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="089a1-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="089a1-128">Ekleyerek ı kullanımını gösterir `Math` sınıf tanımı ve ilk `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="089a1-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="089a1-129">Kodunuzun geri kalanı için uygulanacak çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="089a1-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="089a1-130">`<summary>` Etiketi çok önemlidir ve içeriğini birincil bilgi kaynağı olarak tür veya üye IntelliSense ya da bir API başvuru belgesini olduğundan bunu dahil öneririz.</span><span class="sxs-lookup"><span data-stu-id="089a1-130">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="089a1-131">&lt;Açıklamalar&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-131">&lt;remarks&gt;</span></span>

<span data-ttu-id="089a1-132">`<remarks>` Etiketi tamamlayan türleri veya üyeleri hakkındaki bilgileri, `<summary>` etiketi sağlar.</span><span class="sxs-lookup"><span data-stu-id="089a1-132">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="089a1-133">Bu örnekte, yalnızca onu sınıfa eklemeniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-133">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a><span data-ttu-id="089a1-134">&lt;döndürür&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-134">&lt;returns&gt;</span></span>

<span data-ttu-id="089a1-135">`<returns>` Etiketi bir yöntem bildirimi dönüş değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="089a1-135">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="089a1-136">Önce aşağıdaki örnekte gösterildiği gibi `<returns>` ilk etiketinde `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="089a1-136">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="089a1-137">Diğer yöntemler hakkında aynı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-137">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a><span data-ttu-id="089a1-138">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-138">&lt;value&gt;</span></span>

<span data-ttu-id="089a1-139">`<value>` Etiketi benzer `<returns>` özelliklerini dışında kullanmasını etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-139">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="089a1-140">Varsayarak, `Math` kitaplığı adlı bir statik özelliğe sahip `PI`, İşte bu etiketin nasıl kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="089a1-140">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a><span data-ttu-id="089a1-141">&lt;Örnek&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-141">&lt;example&gt;</span></span>

<span data-ttu-id="089a1-142">Kullandığınız `<example>` örnek XML belgelerinizde içerecek şekilde etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-142">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="089a1-143">Bu alt kullanılmasına `<code>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-143">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="089a1-144">`code` Etiket, satır sonları ve girinti uzun örnekleri için korur.</span><span class="sxs-lookup"><span data-stu-id="089a1-144">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="089a1-145">&lt;Para&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-145">&lt;para&gt;</span></span>

<span data-ttu-id="089a1-146">Kullandığınız `<para>` kendi üst etiketinin içinde içeriği biçimlendirmek için etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-146">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="089a1-147">`<para>` genellikle bir etiketinin içine gibi kullanılan `<remarks>` veya `<returns>`, metin paragraflara bölmek için.</span><span class="sxs-lookup"><span data-stu-id="089a1-147">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="089a1-148">İçeriği biçimlendirmek `<remarks>` Sınıf tanımınız için etiket.</span><span class="sxs-lookup"><span data-stu-id="089a1-148">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a><span data-ttu-id="089a1-149">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-149">&lt;c&gt;</span></span>

<span data-ttu-id="089a1-150">Biçimlendirme hala konuyla ilgili, kullandığınız `<c>` kod olarak metnin bir bölümünü işaretlemek etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-150">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="089a1-151">Benzer; `<code>` etiketi ancak satır içi.</span><span class="sxs-lookup"><span data-stu-id="089a1-151">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="089a1-152">Hızlı kod örneği bir etiketin içeriği bir parçası olarak göstermek istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="089a1-152">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="089a1-153">Şimdi belgelerine güncelleştirme `Math` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="089a1-153">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a><span data-ttu-id="089a1-154">&lt;Özel durumu&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-154">&lt;exception&gt;</span></span>

<span data-ttu-id="089a1-155">Kullanarak `<exception>` etiketi, bir yöntem belirli istisnalar atabilirsiniz biliyorsanız, geliştiricilerin sağlar.</span><span class="sxs-lookup"><span data-stu-id="089a1-155">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="089a1-156">Bakarak, `Math` kitaplığı görebilirsiniz her ikisi de `Add` yöntemleri, belirli bir koşul karşılandığında bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="089a1-156">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="089a1-157">Değil yine de o kadar belirgin tamsayıdır `Divide` yöntemi atar de varsa `b` parametresi sıfırda.</span><span class="sxs-lookup"><span data-stu-id="089a1-157">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="089a1-158">Şimdi bu yöntemi özel durum belgelerine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="089a1-158">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="089a1-159">`cref` Öznitelik geçerli derleme ortamından kullanılabilir bir özel durum başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="089a1-159">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="089a1-160">Bu proje veya başvurulan bir derleme tanımlanan herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="089a1-160">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="089a1-161">Değerini çözümlenemiyorsa derleyici bir uyarı verecek.</span><span class="sxs-lookup"><span data-stu-id="089a1-161">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="089a1-162">&lt;Bkz:&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-162">&lt;see&gt;</span></span>

<span data-ttu-id="089a1-163">`<see>` Etiketi için başka bir kod öğesi bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="089a1-163">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="089a1-164">Sonraki Örneğimizde, ikisi arasındaki tıklatılabilir bir bağlantı oluşturacağız `Add` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="089a1-164">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="089a1-165">`cref` Olan bir **gerekli** temsil eden bir tür ya da geçerli derleme ortamından kullanılabilir kendi üyesi başvuru özniteliği.</span><span class="sxs-lookup"><span data-stu-id="089a1-165">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span> <span data-ttu-id="089a1-166">Bu proje veya başvurulan bir derleme tanımlanan herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="089a1-166">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="089a1-167">&lt;SeeAlso&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-167">&lt;seealso&gt;</span></span>

<span data-ttu-id="089a1-168">Kullandığınız `<seealso>` bunu aynı şekilde etiketinde `<see>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-168">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="089a1-169">Tek fark, içeriği genellikle "bir Ayrıca bkz:" bölümünde yerleştirilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="089a1-169">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="089a1-170">Burada ekleyeceğiz bir `seealso` üzerinde tamsayı etiketi `Add` tamsayı parametreleri kabul eden diğer sınıfı yöntemleri başvurmak için yöntemi:</span><span class="sxs-lookup"><span data-stu-id="089a1-170">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="089a1-171">`cref` Öznitelik bir tür ya da geçerli derleme ortamından kullanılabilir kendi üyesi başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="089a1-171">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="089a1-172">Bu proje veya başvurulan bir derleme tanımlanan herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="089a1-172">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="089a1-173">&lt;Param&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-173">&lt;param&gt;</span></span>

<span data-ttu-id="089a1-174">Kullandığınız `<param>` bir yöntemin parametre açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="089a1-174">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="089a1-175">İşte bir örnek üzerinde çift `Add` yöntemi: Etiket açıklar parametresi belirtilen **gerekli** `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="089a1-175">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a><span data-ttu-id="089a1-176">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-176">&lt;typeparam&gt;</span></span>

<span data-ttu-id="089a1-177">Kullandığınız `<typeparam>` tıpkı etiketi `<param>` etiketi ancak genel bir parametreye açıklamak genel türü veya yöntemi bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="089a1-177">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="089a1-178">Hızlı bir genel yöntem ekleme, `Math` sınıfı bir miktar diğerinden daha büyük olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="089a1-178">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a><span data-ttu-id="089a1-179">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-179">&lt;paramref&gt;</span></span>

<span data-ttu-id="089a1-180">Bazen ne olabilir bir yöntem yaptığı açıklayan ortasında olabilir bir `<summary>` etiketi ve bir parametre için bir başvuru yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-180">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="089a1-181">`<paramref>` Etiketi yalnızca bu iş için mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="089a1-181">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="089a1-182">Şimdi güncelleştirme bizim çift özetini dayalı `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="089a1-182">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="089a1-183">Gibi `<param>` parametre adı belirtilen etiket **gerekli** `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="089a1-183">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a><span data-ttu-id="089a1-184">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-184">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="089a1-185">Kullandığınız `<typeparamref>` tıpkı etiketi `<paramref>` etiketi ancak genel bir parametreye açıklamak genel türü veya yöntemi bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="089a1-185">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="089a1-186">Daha önce oluşturduğunuz aynı genel yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-186">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a><span data-ttu-id="089a1-187">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-187">&lt;list&gt;</span></span>

<span data-ttu-id="089a1-188">Kullandığınız `<list>` bir sıralı liste, sırasız liste veya tablo olarak biçimi belgelerine bilgilere etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-188">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="089a1-189">Her matematik işlemi düzenlenmemiş bir listesini olun, `Math` kitaplığı destekler.</span><span class="sxs-lookup"><span data-stu-id="089a1-189">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="089a1-190">Sıralı liste veya tablo değiştirerek yapabilirsiniz `type` özniteliğini `number` veya `table`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="089a1-190">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="089a1-191">Tüm bir araya getirme</span><span class="sxs-lookup"><span data-stu-id="089a1-191">Putting it all together</span></span>

<span data-ttu-id="089a1-192">Bu öğretici izleyen ve gerektiğinde etiketleri kodunuzu uygulanan, kodunuzu aşağıdakine benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="089a1-192">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="089a1-193">Kodunuz aracılığıyla, ayrıntılı belgelere Web sitesi ile tıklanabilir çapraz tam oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-193">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="089a1-194">Ancak başka bir sorun karşılaştığı: kodunuzun okunması zor hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="089a1-194">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="089a1-195">Bu onarımı kabus için bu kodu katkıda isteyen herhangi bir geliştirici olarak işaretleneceğini çalışılamayacak kadar çok bilgi bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="089a1-195">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span> <span data-ttu-id="089a1-196">Thankfully yapmam yardımcı olabilecek bir XML etiketi vardır:</span><span class="sxs-lookup"><span data-stu-id="089a1-196">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="089a1-197">&lt;İçerir&gt;</span><span class="sxs-lookup"><span data-stu-id="089a1-197">&lt;include&gt;</span></span>

<span data-ttu-id="089a1-198">`<include>` Etiketi türlerini açıklayan ayrı bir XML dosyası açıklamaları ve belge açıklamaları doğrudan, kaynak kodu dosyasına yerleştirerek aksine, kaynak kodunuzu üyelerinde bakın olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="089a1-198">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="089a1-199">Tüm XML etiketleri adlı ayrı bir XML dosyasına taşınır oluşturacağız artık `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="089a1-199">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="089a1-200">İstediğiniz dosyanın adını çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="089a1-200">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="089a1-201">Yukarıdaki XML'de her üyenin belge açıklamaları doğrudan ne yaptıklarını sonra adlı etiket içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="089a1-201">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="089a1-202">Kendi stratejisi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="089a1-202">You can choose your own strategy.</span></span> <span data-ttu-id="089a1-203">Ayrı bir dosyada XML yorumlarınızı sahip olduğunuza göre nasıl kodunuzu kullanarak daha okunabilir hale getirilebilir görelim `<include>` etiketi:</span><span class="sxs-lookup"><span data-stu-id="089a1-203">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="089a1-204">Ve elinizde vardır: okunabilir olması geri bizim koddur ve belgeleri bilgi kaybedildi.</span><span class="sxs-lookup"><span data-stu-id="089a1-204">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span> 

<span data-ttu-id="089a1-205">`filename` Öznitelik belgeleri içeren XML dosyasının adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="089a1-205">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="089a1-206">`path` Özniteliğini temsil bir [XPath](https://msdn.microsoft.com/library/ms256115.aspx) için sorgu `tag name` mevcut belirtilen `filename`.</span><span class="sxs-lookup"><span data-stu-id="089a1-206">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="089a1-207">`name` Öznitelik açıklamaları önündeki etiketinde ad belirticisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="089a1-207">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="089a1-208">`id` Yerine kullanılan öznitelik `name` açıklamaları önündeki etiket Kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="089a1-208">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="089a1-209">Etiketler kullanıcı tanımlı</span><span class="sxs-lookup"><span data-stu-id="089a1-209">User Defined Tags</span></span>

<span data-ttu-id="089a1-210">Yukarıda özetlenen tüm etiketleri, C# Derleyici tarafından tanınan temsil eder.</span><span class="sxs-lookup"><span data-stu-id="089a1-210">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="089a1-211">Ancak, bir kullanıcı kendi etiketleri tanımlamak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="089a1-211">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="089a1-212">Sandcastle gibi araçlar ek etiketleri ister için destek Getir [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) ve hatta Destek [ad alanları belgeleme](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="089a1-212">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="089a1-213">Birden çok çıktı biçimlerinden HTML PDF için desteklenen ve özel veya şirket içi belgeleri oluşturma araçları ile standart etiketleri de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="089a1-213">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="089a1-214">Önerileri</span><span class="sxs-lookup"><span data-stu-id="089a1-214">Recommendations</span></span>

<span data-ttu-id="089a1-215">Kod belgeleme nedenlerle önerilir.</span><span class="sxs-lookup"><span data-stu-id="089a1-215">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="089a1-216">Hangi aşağıdaki gibi bazı en iyi uygulamalar, genel örneği senaryolarının ve ne zaman XML belgelerini kullanarak etiketleri, C# kodunda bilmeniz gereken şeyleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="089a1-216">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="089a1-217">Tutarlılık sağlamak, tüm herkese görünür türleri ve üyeleri belgelenen.</span><span class="sxs-lookup"><span data-stu-id="089a1-217">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="089a1-218">Bunu yapmanız gerekir, bunu tüm.</span><span class="sxs-lookup"><span data-stu-id="089a1-218">If you must do it, do it all.</span></span>
* <span data-ttu-id="089a1-219">Özel üyelerin XML açıklamaları kullanarak da belgelenen.</span><span class="sxs-lookup"><span data-stu-id="089a1-219">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="089a1-220">Ancak, bu kitaplığınızın (büyük olasılıkla gizli) çalışmalar kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="089a1-220">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="089a1-221">Tam en azından türleri ve üyeleri olmalıdır bir `<summary>` içeriği için IntelliSense gerektiğinden etiketi.</span><span class="sxs-lookup"><span data-stu-id="089a1-221">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="089a1-222">Tam durakları ile biten bütün cümleleri kullanarak belge metin yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="089a1-222">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="089a1-223">Kısmi sınıflar tam olarak desteklenir ve belgeleri bilgi türü için tek bir giriş içine birleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="089a1-223">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="089a1-224">Söz dizimi derleyici doğrular `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` ve `<typeparam>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="089a1-224">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="089a1-225">Derleyici dosya yolları ve diğer bölümleri kodunun başvuruları içeren parametreleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="089a1-225">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="089a1-226">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="089a1-226">See also</span></span>
[<span data-ttu-id="089a1-227">XML belgeleri yorumları (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="089a1-227">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)

[<span data-ttu-id="089a1-228">Belge açıklamaları (C# programlama Kılavuzu) için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="089a1-228">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
