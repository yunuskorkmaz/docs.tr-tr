---
title: Kodunuzu XML açıklamalarıyla belgeleme
description: Kodunuzu XML belge açıklamalarıyla belgeleme ve derleme zamanında bir XML belge dosyası oluşturma hakkında bilgi edinin.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: ef0d22e0ee7faa3ba51da6b44cf1827f19baf4f1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787830"
---
# <a name="document-your-code-with-xml-comments"></a>Kodunuzu XML açıklamalarıyla belgeleme

XML belge açıklamaları, Kullanıcı tanımlı herhangi bir tür veya üyenin tanımının üzerine eklenen özel bir açıklama türüdür.
Bunlar, derleme zamanında bir XML belge dosyası oluşturmak için derleyici tarafından işlenebilecekleri için özeldir.
Derleyici tarafından oluşturulan XML dosyası, .NET derlemenizin yanı sıra, Visual Studio ve diğer IDE 'Ler, türler veya üyeler hakkında hızlı bilgileri göstermek için IntelliSense kullanabilmesi için birlikte dağıtılabilir. Ayrıca, XML dosyasını gibi araçlarla çalıştırılabilir [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) API Başvurusu Web siteleri oluşturmak için.

Tüm diğer yorumlar gibi XML belgesi açıklamaları derleyici tarafından yok sayılır.

XML dosyasını, derleme zamanında aşağıdakilerden birini yaparak oluşturabilirsiniz:

- Komut satırından .NET Core ile bir uygulama geliştiriyorsanız,. csproj proje dosyanızın `<PropertyGroup>` bölümüne `GenerateDocumentationFile` öğesi ekleyebilirsiniz. Belge dosyasının yolunu doğrudan [`DocumentationFile` öğesi](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak da belirtebilirsiniz. Aşağıdaki örnek, derleme ile aynı kök dosya adına sahip proje dizininde bir XML dosyası oluşturur:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   Bu, aşağıdaki gibi eşdeğerdir:
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Visual Studio 'Yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayıp **Özellikler**' i seçin. Özellikler iletişim kutusunda **derleme** sekmesini seçin ve **XML belge dosyasını**denetleyin. Derleyicinin dosyayı yazdıkları konumu da değiştirebilirsiniz.

- Komut satırından bir .NET Framework uygulaması derlerken, derlerken [-doc derleyici seçeneğini](language-reference/compiler-options/doc-compiler-option.md) ekleyin.  

XML belge açıklamaları Üçlü eğik çizgi (`///`) ve XML biçimli bir açıklama gövdesi kullanır. Örneğin:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>İzlenecek yol

Yeni geliştiricilerin, üçüncü taraf geliştiricilerin kullanması için ve katkıda bulunmak üzere çok basit bir matematik kitaplığını belgeleme konusunda bilgi vereceğiz.

Basit matematik kitaplığı için kod aşağıda verilmiştir:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Örnek kitaplık, `int` ve `double` veri türlerinde `add`, `subtract`, `multiply` ve `divide` dört önemli aritmetik işlemi destekler.

Şimdi kitaplığınızı kullanan üçüncü taraf geliştiriciler için kodunuzda bir API başvuru belgesi oluşturabilmek, ancak kaynak koda erişiminiz yok.
Daha önce bahsedilen XML belge etiketleri bunu elde etmek için kullanılabilir. Artık C# derleyicinin DESTEKLEDIĞI standart XML etiketlerine tanıtılıcaksınız.

## <a name="summary"></a>\<summary>

`<summary>` etiketi, bir tür veya üye hakkında kısa bilgiler ekler.
`Math` sınıf tanımına ve ilk `Add` yöntemine ekleyerek kullanımını göstereceğim. Kodunuzu geri kalanına uygulamayı ücretsiz olarak hissetmekten çekinmeyin.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` etiketi çok önemlidir ve içeriği, IntelliSense 'de veya bir API başvuru belgesinde bulunan içerik veya üye bilgilerinin birincil kaynağı olduğundan, bunu dahil etmenizi öneririz.

## <a name="remarks"></a>\<açıklamalar >

`<remarks>` etiketi, `<summary>` etiketinin sağladığı türler veya Üyeler hakkındaki bilgileri tamamlar. Bu örnekte, bunu yalnızca sınıfına eklersiniz.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

`<returns>` etiketi bir yöntem bildiriminin dönüş değerini açıklar.
Daha önce olduğu gibi, aşağıdaki örnek ilk `Add` yönteminde `<returns>` etiketini gösterir. Diğer yöntemlerle aynı şekilde yapabilirsiniz.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

`<value>` etiketi, özellikler için kullanmanız dışında `<returns>` etiketine benzerdir.
`Math` kitaplığınızın `PI`adında bir statik özelliği olduğunu varsayarsak, bu etiketi nasıl kullanacağınızı aşağıda bulabilirsiniz:

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<örnek >

XML belgelerinize bir örnek eklemek için `<example>` etiketini kullanın.
Bu, alt `<code>` etiketinin kullanılmasını içerir.

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` etiketi, daha uzun örnekler için satır sonlarını ve girintiyi korur.

## <a name="para"></a>\<paragraf >

İçeriği üst etiketi içinde biçimlendirmek için `<para>` etiketini kullanın. `<para>`, genellikle metni paragraflarına bölmek için `<remarks>` veya `<returns>`gibi bir etiket içinde kullanılır.
Sınıf tanımınız için `<remarks>` etiketinin içeriğini biçimlendirebilirsiniz.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c >

Biçimlendirme konusunda hala, metnin bir kısmını kod olarak işaretlemek için `<c>` etiketini kullanırsınız.
`<code>` etiketi, ancak satır içi gibi. Bir etiketin içeriğinin bir parçası olarak hızlı bir kod örneği göstermek istediğinizde yararlı olur.
`Math` sınıfının belgelerini güncelleştirelim.

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<özel durum >

`<exception>` etiketini kullanarak, geliştiricilerinizin bir yöntemin belirli özel durumları oluşturduğunu bilmesini sağlayabilirsiniz.
`Math` kitaplığınıza baktığınızda, her iki `Add` yönteminin da belirli bir koşul karşılanırsa bir özel durum oluşturmasını sağlayabilirsiniz. Öyle değildir, ancak `b` parametresi sıfır ise tamsayı `Divide` yöntemi de oluşturulur. Şimdi bu yönteme özel durum belgeleri ekleyin.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` özniteliği geçerli derleme ortamında kullanılabilir bir özel duruma bir başvuruyu temsil eder.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir. Değeri çözülemezse, derleyici bir uyarı verebilir.

## <a name="see"></a>\<bkz. >

`<see>` etiketi, başka bir kod öğesi için bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak sağlar. Sonraki örnekte, iki `Add` yöntemi arasında tıklatılabilir bir bağlantı oluşturacağız.

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref`, geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eden **gerekli** bir özniteliktir.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.

## <a name="seealso"></a>\<seede >

`<seealso>` etiketini `<see>` etiketiyle aynı şekilde kullanırsınız. Tek fark, içeriğinin genellikle bir "Ayrıca bkz." bölümüne yerleştirilme nedendir. Burada, tamsayı parametrelerini kabul eden sınıftaki diğer yöntemlere başvurmak için tamsayı `Add` yöntemine bir `seealso` etiketi ekleyeceğiz:

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` özniteliği, geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eder.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.

## <a name="param"></a>\<param>

Metodun parametrelerini anlatmak için `<param>` etiketini kullanın. Double `Add` yöntemine bir örnek aşağıda verilmiştir: etiketin açıkladığı parametre, **gerekli** `name` özniteliğinde belirtilir.

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam >

`<typeparam>` etiketini `<param>` etiketi gibi kullanırsınız, ancak genel tür veya yöntem bildirimlerinde genel bir parametreyi betimleyelim.
Bir miktarın diğerinden daha büyük olup olmadığını denetlemek için `Math` sınıfınıza hızlı genel bir yöntem ekleyin.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref >

Bazen, bir yöntemin `<summary>` bir etiketle ne olduğunu açıklayan ortasında olabilirsiniz ve bir parametreye başvuru yapmak isteyebilirsiniz. `<paramref>` etiketi yalnızca bunun için harika. Double tabanlı `Add` yönteminizin özetini güncelleştirelim. `<param>` etiketi gibi, **gerekli** `name` özniteliğinde parametre adı belirtilir.

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref >

`<typeparamref>` etiketini `<paramref>` etiketi gibi kullanırsınız, ancak genel tür veya yöntem bildirimlerinde genel bir parametreyi betimleyelim.
Daha önce oluşturduğunuz genel yöntemi kullanabilirsiniz.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<listesi >

Belge bilgilerini sıralı liste, sırasız liste veya tablo olarak biçimlendirmek için `<list>` etiketini kullanırsınız.
`Math` kitaplığınızın desteklediği her matematik işleminin sıralanmamış bir listesini oluşturun.

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

`type` özniteliğini sırasıyla `number` veya `table`olarak değiştirerek sıralı bir liste veya tablo yapabilirsiniz.

## <a name="inheritdoc"></a>\<devralma belgesi >

Temel sınıflardan, arabirimlerde ve benzer yöntemlerle XML açıklamalarını devralacak `<inheritdoc>` etiketini kullanabilirsiniz. Bu, yinelenen XML açıklamalarını istenmeyen kopyalama ve yapıştırmayı ortadan kaldırır ve otomatik olarak XML açıklamalarını eşitlenmiş halde tutar.

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a>Hepsini bir araya getirin

Bu öğreticiyi takip ediyorsanız ve gereken yere etiketleri kodunuza uyguladıysanız, kodunuzun aşağıdakine benzer şekilde görünmesi gerekir:

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Kodınızdan, tıklatılabilir çapraz başvurularla ayrıntılı bir belge Web sitesi oluşturabilirsiniz. Ancak başka bir sorunla karşılaşıyoruz: kodunuzun okunması zor oldu.
Bu koda katkıda bulunmak isteyen herhangi bir geliştirici için bu bir gece olacak şekilde, bu kadar çok bilgi vardır.
Bu konuda size yardımcı olabilecek bir XML etiketi vardı:

## <a name="include"></a>\<içerme >

`<include>` etiketi, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeyi tersine, kaynak kodunuzda türleri ve üyeleri tanımlayan ayrı bir XML dosyasındaki açıklamalara başvurmanıza olanak sağlar.

Artık tüm XML etiketlerinizi `docs.xml`adlı ayrı bir XML dosyasına taşıyacağız. Dosyayı istediğiniz şekilde adlandırabilirsiniz.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

Yukarıdaki XML 'de, her üyenin belge yorumu, ne yapacaklarıyla doğrudan adlı bir etiketin içinde görünür. Kendi stratejinizi seçebilirsiniz.
XML yorumlarınıza artık ayrı bir dosyada sahip olduğunuza göre, kodunuzun `<include>` etiketi kullanılarak nasıl daha okunaklı hale getirildikimi görelim:

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Bu durumda: kodunuz okunabilir hale getirilir ve belge bilgisi kaybedilmiyor.

`file` öznitelik, belgeleri içeren XML dosyasının adını temsil eder.

`path` öznitelik, belirtilen `file`mevcut `tag name` bir [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) sorgusunu temsil eder.

`name` özniteliği, etiketteki açıklamaların önündeki ad belirticisini temsil eder.

`name` yerine kullanılabilecek `id` özniteliği, yorumların önündeki etiketin KIMLIĞINI temsil eder.

### <a name="user-defined-tags"></a>Kullanıcı tanımlı Etiketler

Yukarıda özetlenen tüm Etiketler, C# derleyici tarafından tanınan olanları temsil eder. Ancak, bir Kullanıcı kendi etiketlerini tanımlayaücretsizdir.
Sandrole gibi Araçlar [\<olay >](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) ve [\<Note >](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm)gibi ek Etiketler için destek getirme ve hatta [ad alanlarını belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)desteği.
Özel veya şirket içi belge oluşturma araçları ayrıca standart Etiketler ve HTML 'den PDF 'ye birden çok çıktı biçimi ile kullanılabilir.

## <a name="recommendations"></a>Öneriler

Kodu belgeleme pek çok nedenden dolayı önerilir. Aşağıda, bazı en iyi yöntemler, genel kullanım örneği senaryoları ve C# kodunuzda XML belge etiketlerini kullanırken bilmeniz gereken noktalar verilmiştir.

- Tutarlılık açısından, herkese açık olarak görünen tüm türler ve üyeleri açıklanmalıdır. Bunu yapmanız gerekiyorsa, bunu yapın.
- Özel Üyeler ayrıca XML açıklamaları kullanılarak Belgelenebilir. Ancak bu, kitaplığınızın iç (potansiyel olarak gizli) işleyişini kullanıma sunar.
- İçerik IntelliSense için gerekli olduğundan, en azından, türlerin ve üyelerinin `<summary>` bir etiketi olmalıdır.
- Belge metni tam uyarılarla biten tam tümceler kullanılarak yazılmalıdır.
- Kısmi sınıflar tam olarak desteklenir ve belge bilgileri bu tür için tek bir girişte birleştirilir.
- Derleyici `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`ve `<typeparam>` etiketlerinin sözdizimini doğrular.
- Derleyici dosya yolları içeren parametreleri ve kodun diğer bölümlerine başvuruları doğrular.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belge açıklamaları (C# Programlama Kılavuzu)](programming-guide/xmldoc/index.md)
- [Belge açıklamaları için önerilen Etiketler (C# Programlama Kılavuzu)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
