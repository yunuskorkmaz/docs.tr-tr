---
title: Kodunuzu XML açıklamalarıyla belgeleme
description: Kodunuzu XML belge açıklamalarıyla belgeleme ve derleme zamanında bir XML belge dosyası oluşturma hakkında bilgi edinin.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: b6744921f4703f53a16b6bdadcfbf375c2fb3332
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104781"
---
# <a name="documenting-your-code-with-xml-comments"></a>Kodunuzu XML açıklamalarıyla belgeleme

XML belge açıklamaları, Kullanıcı tanımlı herhangi bir tür veya üyenin tanımının üzerine eklenen özel bir açıklama türüdür.
Bunlar, derleme zamanında bir XML belge dosyası oluşturmak için derleyici tarafından işlenebilecekleri için özeldir.
Derleyici tarafından oluşturulan XML dosyası, .NET derlemenizin yanı sıra, Visual Studio ve diğer IDE 'Ler, türler veya üyeler hakkında hızlı bilgileri göstermek için IntelliSense kullanabilmesi için birlikte dağıtılabilir. Ayrıca, XML dosyasını gibi araçlarla çalıştırılabilir [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) API Başvurusu Web siteleri oluşturmak için.

Tüm diğer yorumlar gibi XML belgesi açıklamaları derleyici tarafından yok sayılır.

XML dosyasını, derleme zamanında aşağıdakilerden birini yaparak oluşturabilirsiniz:

- Komut satırından .NET Core ile bir uygulama geliştiriyorsanız,. csproj proje dosyanızın `<PropertyGroup>` bölümüne bir belgetadosya [öğesi](/visualstudio/msbuild/common-msbuild-project-properties) ekleyebilirsiniz. Aşağıdaki örnek, derleme ile aynı kök dosya adına sahip proje dizininde bir XML dosyası oluşturur:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   Ayrıca, XML dosyasının tam mutlak veya göreli yolunu ve adını belirtebilirsiniz. Aşağıdaki örnek, XML dosyasını bir uygulamanın hata ayıklama sürümüyle aynı dizinde oluşturur:

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- Visual Studio 'Yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayıp **Özellikler**' i seçin. Özellikler iletişim kutusunda **derleme** sekmesini seçin ve **XML belge dosyasını**denetleyin. Derleyicinin dosyayı yazdıkları konumu da değiştirebilirsiniz.

- Komut satırından bir .NET Framework uygulaması derlerken, derlerken [/doc derleyici seçeneğini](language-reference/compiler-options/doc-compiler-option.md) ekleyin.  

XML belge açıklamaları Üçlü eğik çizgi (`///`) ve XML biçimli bir açıklama gövdesi kullanır. Örneğin:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Gidiş

Yeni geliştiricilerin, üçüncü taraf geliştiricilerin kullanması için ve katkıda bulunmak amacıyla çok basit bir matematik kitaplığını belgeleme konusunda bilgi verlim.

Basit matematik kitaplığı için kod aşağıda verilmiştir:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Örnek kitaplık, dört önemli aritmetik işlemi `add` `multiply` , `subtract` `divide` ve açık `int` ve `double` veri türlerini destekler.

Şimdi, kitaplığınızı kullanan ancak kaynak koda erişiminiz olmayan üçüncü taraf geliştiriciler için kodınızdan bir API başvuru belgesi oluşturabiliyor olmanız istiyorsunuz.
Daha önce bahsedilen XML belge etiketleri bunu elde etmek için kullanılabilir. Artık C# derleyicinin DESTEKLEDIĞI standart XML etiketlerine tanıtılıcaksınız.

## <a name="summary"></a>\<summary>

Etiketi `<summary>` , bir tür veya üye hakkında kısa bilgiler ekler.
Kendi kullanımını `Math` sınıf tanımına ve ilk `Add` yönteme ekleyerek göstereceğim. Kodunuzu geri kalanına uygulamayı ücretsiz olarak hissetmekten çekinmeyin.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Etiketi çok önemlidir ve içeriği, IntelliSense 'de veya bir API başvuru belgesinde bulunan içerik veya üye bilgilerinin birincil kaynağı olduğundan, bunu dahil etmenizi öneririz.

## <a name="remarks"></a>\<açıklamalar >

Etiketi, `<summary>` etiketin sağladığı türler veya Üyeler hakkındaki bilgileri tamamlar. `<remarks>` Bu örnekte, bunu yalnızca sınıfına eklersiniz.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

`<returns>` Etiket, bir yöntem bildiriminin dönüş değerini açıklar.
Daha önce olduğu gibi, aşağıdaki örnek ilk `<returns>` `Add` yöntemde etiketini gösterir. Diğer yöntemlerle aynı şekilde yapabilirsiniz.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Etiketi, bu etiketle benzerdir `<returns>` , ancak bunları özellikler için kullanmanız gerekir. `<value>`
Kitaplığınızın bir statik `PI`özelliği olduğu varsayıldığında, bu etiketi şu şekilde kullanabilirsiniz: `Math`

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<örnek >

XML belgelerinize bir `<example>` örnek eklemek için etiketini kullanın.
Bunun için alt `<code>` etiketi kullanılması gerekir.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

Etiket `code` , daha uzun örnekler için satır sonlarını ve girintiyi korur.

## <a name="para"></a>\<Para >

İçeriğini üst etiketi `<para>` içinde biçimlendirmek için etiketini kullanın. `<para>`genellikle metin paragraflarına bölmek için `<remarks>` veya `<returns>`gibi bir etiket içinde kullanılır.
Sınıf tanımınız için `<remarks>` etiketin içeriğini biçimlendirebilirsiniz.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c >

Biçimlendirme konusunda hala, metnin bir kısmını kod olarak işaretlemek `<c>` için etiketini kullanırsınız.
Etiket, `<code>` ancak satır içi gibi. Bir etiketin içeriğinin bir parçası olarak hızlı bir kod örneği göstermek istediğinizde yararlı olur.
`Math` Sınıfın belgelerini güncelleştirelim.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<özel durum >

`<exception>` Etiketini kullanarak, geliştiricilerin bir yöntemin belirli özel durumlar oluşturduğunu bilmesini sağlar.
Kitaplığınıza bakarak, belirli bir koşul karşılanırsa her iki yöntemin `Add` de bir özel durum oluşturmasını sağlayabilirsiniz. `Math` Öyle değildir, ancak `Divide` `b` parametrenin sıfır olması durumunda tamsayı yöntemi de oluşturulur. Şimdi bu yönteme özel durum belgeleri ekleyin.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Öznitelik, geçerli derleme ortamında kullanılabilir olan bir özel duruma başvuruyu temsil eder.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir. Değeri çözülemezse, derleyici bir uyarı verebilir.

## <a name="see"></a>\<bkz. >

Etiketi `<see>` , başka bir kod öğesi için bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak sağlar. Sonraki örnekte, iki `Add` Yöntem arasında tıklatılabilir bir bağlantı oluşturacağız.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

, `cref` Geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eden **gerekli** bir özniteliktir.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.

## <a name="seealso"></a>\<SeeAlso >

`<seealso>` Etiketi, `<see>` etiketi yaptığınız şekilde kullanırsınız. Tek fark, içeriğinin genellikle bir "Ayrıca bkz." bölümüne yerleştirilme nedendir. Burada, tamsayı parametrelerini kabul `seealso` eden sınıftaki diğer yöntemlere `Add` başvurmak için tamsayı yöntemine bir etiket ekleyeceğiz:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Öznitelik, geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eder.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.

## <a name="param"></a>\<param>

Bir yöntemin parametrelerini `<param>` anlatmak için etiketini kullanırsınız. Double `Add` yöntemine bir örnek aşağıda verilmiştir: Etiketin açıkladığı parametre, **gerekli** `name` özniteliğinde belirtilir.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam >

Etiketi tıpkı `<typeparam>` etiketi gibi kullanırsınız, `<param>` ancak genel tür veya yöntem bildirimlerinin genel bir parametreyi tanımlamasını sağlar.
Bir miktarın diğerinden daha büyük olup olmadığını `Math` denetlemek için sınıfınıza hızlı genel bir yöntem ekleyin.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref >

Bazen bir yöntemin `<summary>` hangi bir etiketle ne olduğunu açıklayan ortasında olabilirsiniz ve bir parametreye başvuru yapmak isteyebilirsiniz. `<paramref>` Etiketi yalnızca bunun için harika. Double tabanlı `Add` yönteminizin özetini güncelleştirelim. Etiket gibi, **gerekli** `name` özniteliğinde parametre adı belirtilir. `<param>`

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref >

Etiketi tıpkı `<typeparamref>` etiketi gibi kullanırsınız, `<paramref>` ancak genel tür veya yöntem bildirimlerinin genel bir parametreyi tanımlamasını sağlar.
Daha önce oluşturduğunuz genel yöntemi kullanabilirsiniz.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<Liste >

Belge bilgilerini sıralı `<list>` liste, sırasız liste veya tablo olarak biçimlendirmek için etiketini kullanın.
`Math` Kitaplığınızın desteklediği her matematik işleminin sıralanmamış bir listesini oluşturun.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

`type` Özniteliği sırasıyla veya`table`olarakdeğiştirerek sıralı bir liste veya tablo yapabilirsiniz. `number`

### <a name="putting-it-all-together"></a>Tümünü bir araya getirme

Bu öğreticiyi takip ediyorsanız ve gereken yere etiketleri kodunuza uyguladıysanız, kodunuzun aşağıdakine benzer şekilde görünmesi gerekir:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Kodınızdan, tıklatılabilir çapraz başvurularla ayrıntılı bir belge Web sitesi oluşturabilirsiniz. Ancak başka bir sorunla karşılaşıyoruz: kodunuzun okunması zor oldu.
Bu koda katkıda bulunmak isteyen herhangi bir geliştirici için bu bir gece olacak şekilde, bu kadar çok bilgi vardır.
Bu konuda size yardımcı olabilecek bir XML etiketi vardı:

## <a name="include"></a>\<> dahil et

`<include>` Etiketi, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeyi aksine, kaynak kodunuzda türleri ve üyeleri tanımlayan ayrı bir XML dosyasındaki açıklamalara başvurmanıza olanak sağlar.

Artık tüm XML etiketlerinizi adlı `docs.xml`ayrı bir XML dosyasına taşıyacağız. Dosyayı istediğiniz şekilde adlandırabilirsiniz.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

Yukarıdaki XML 'de, her üyenin belge yorumu, ne yapacaklarıyla doğrudan adlı bir etiketin içinde görünür. Kendi stratejinizi seçebilirsiniz.
XML açıklamalarınız ayrı bir dosyada olduğuna göre, şu `<include>` etiketi kullanarak kodunuzun daha okunaklı hale getirilme biçimini görelim:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Bu durumda: kodunuz okunabilir hale getirilir ve belge bilgisi kaybedilmiyor.

`file` Öznitelik, belgeleri içeren XML dosyasının adını temsil eder.

Öznitelik, belirtilen `tag name` [](../standard/data/xml/xpath-queries-and-namespaces.md) öğesindevarolanbirXPathsorgusunutemsil`file`eder. `path`

`name` Öznitelik, yorumlarla önce gelen etiketteki ad belirticisini temsil eder.

Yerinde kullanılabilecek `id` öznitelik, yorumların önündeki etiketin kimliğini temsil eder. `name`

### <a name="user-defined-tags"></a>Kullanıcı tanımlı Etiketler

Yukarıda özetlenen tüm Etiketler, C# derleyici tarafından tanınan olanları temsil eder. Ancak, bir Kullanıcı kendi etiketlerini tanımlayaücretsizdir.
Sandrole gibi araçlar, [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) gibi ek Etiketler için destek getirme ve hatta [ad alanlarını belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)desteği.
Özel veya şirket içi belge oluşturma araçları ayrıca standart Etiketler ve HTML 'den PDF 'ye birden çok çıktı biçimi ile kullanılabilir.

## <a name="recommendations"></a>Öneriler

Kodu belgeleme pek çok nedenden dolayı önerilir. Aşağıda, bazı en iyi yöntemler, genel kullanım örneği senaryoları ve C# kodunuzda XML belge etiketlerini kullanırken bilmeniz gereken noktalar verilmiştir.

- Tutarlılık açısından, herkese açık olarak görünen tüm türler ve üyeleri açıklanmalıdır. Bunu yapmanız gerekiyorsa, bunu yapın.
- Özel Üyeler ayrıca XML açıklamaları kullanılarak Belgelenebilir. Ancak bu, kitaplığınızın iç (potansiyel olarak gizli) işleyişini kullanıma sunar.
- En azından, türler ve üyeleri, IntelliSense için içerik gerektiğinden bir `<summary>` etikete sahip olmalıdır.
- Belge metni tam uyarılarla biten tam tümceler kullanılarak yazılmalıdır.
- Kısmi sınıflar tam olarak desteklenir ve belge bilgileri bu tür için tek bir girişte birleştirilir.
- `<exception>`Derleyici ,`<see>`,, ve`<typeparam>`etiketlerinin sözdizimini doğrular. `<param>` `<include>` `<seealso>`
- Derleyici dosya yolları içeren parametreleri ve kodun diğer bölümlerine başvuruları doğrular.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belge açıklamaları (C# Programlama Kılavuzu)](programming-guide/xmldoc/index.md)
- [Belge açıklamaları için önerilen Etiketler (C# Programlama Kılavuzu)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
