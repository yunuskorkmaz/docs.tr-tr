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
# <a name="document-your-code-with-xml-comments"></a>Kodunuzu XML açıklamalarıyla belgeleme

XML belge açıklamaları, Kullanıcı tanımlı herhangi bir tür veya üyenin tanımının üzerine eklenen özel bir açıklama türüdür.
Bunlar, derleme zamanında bir XML belge dosyası oluşturmak için derleyici tarafından işlenebilecekleri için özeldir.
Derleyici tarafından oluşturulan XML dosyası, Visual Studio ve diğer IDE 'Ler, türler veya üyeler hakkında hızlı bilgi göstermek için IntelliSense kullanabilmesi için .NET derlemenizin yanı sıra dağıtılabilir. Ayrıca, XML dosyası, API başvuru Web siteleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi araçlar aracılığıyla çalıştırılabilir.

Tüm diğer yorumlar gibi XML belgesi açıklamaları derleyici tarafından yok sayılır.

XML dosyasını, derleme zamanında aşağıdakilerden birini yaparak oluşturabilirsiniz:

- Komut satırından .NET Core ile bir uygulama geliştiriyorsanız, `GenerateDocumentationFile` `<PropertyGroup>` . csproj proje dosyanızın bölümüne bir öğesi ekleyebilirsiniz. Ayrıca, belge dosyasının yolunu doğrudan [ `DocumentationFile` öğesini](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak belirtebilirsiniz. Aşağıdaki örnek, derleme ile aynı kök dosya adına sahip proje dizininde bir XML dosyası oluşturur:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   Bu, aşağıdaki gibi eşdeğerdir:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Visual Studio 'Yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayıp **Özellikler**' i seçin. Özellikler iletişim kutusunda **derleme** sekmesini seçin ve **XML belge dosyasını**denetleyin. Derleyicinin dosyayı yazdıkları konumu da değiştirebilirsiniz.

- Komut satırından bir .NET uygulaması derlerken, derlerken [-doc derleyici seçeneğini](language-reference/compiler-options/doc-compiler-option.md) ekleyin.  

XML belge açıklamaları Üçlü eğik çizgi ( `///` ) ve XML biçimli bir açıklama gövdesi kullanır. Örneğin:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Kılavuz

Yeni geliştiricilerin, üçüncü taraf geliştiricilerin kullanması için ve katkıda bulunmak üzere çok basit bir matematik kitaplığını belgeleme konusunda bilgi vereceğiz.

Basit matematik kitaplığı için kod aşağıda verilmiştir:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Örnek kitaplık, ve veri türlerini dört ana aritmetik işlemi ( `add` , `subtract` , `multiply` , ve `divide` ) destekler `int` `double` .

Şimdi kitaplığınızı kullanan üçüncü taraf geliştiriciler için kodunuzda bir API başvuru belgesi oluşturabilmek, ancak kaynak koda erişiminiz yok.
Daha önce bahsedilen XML belge etiketleri bunu elde etmek için kullanılabilir. Artık C# derleyicisinin desteklediği standart XML etiketlerine tanıtılcaksınız.

## \<summary>

`<summary>`Etiketi, bir tür veya üye hakkında kısa bilgiler ekler.
Kendi kullanımını `Math` sınıf tanımına ve ilk yönteme ekleyerek göstereceğim `Add` . Kodunuzu geri kalanına uygulamayı ücretsiz olarak hissetmekten çekinmeyin.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>`Etiketi önemlidir ve içeriği, IntelliSense 'de veya BIR API başvuru belgesinde bulunan içerik veya üye bilgilerinin birincil kaynağı olduğundan, bunu dahil etmenizi öneririz.

## \<remarks>

`<remarks>`Etiketi, etiketin sağladığı türler veya Üyeler hakkındaki bilgileri tamamlar `<summary>` . Bu örnekte, bunu yalnızca sınıfına eklersiniz.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## \<returns>

`<returns>`Etiket, bir yöntem bildiriminin dönüş değerini açıklar.
Daha önce olduğu gibi, aşağıdaki örnek `<returns>` İlk yöntemde etiketini gösterir `Add` . Diğer yöntemlerle aynı şekilde yapabilirsiniz.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## \<value>

`<value>`Etiketi, bu etiketle benzerdir `<returns>` , ancak bunları özellikler için kullanmanız gerekir.
`Math`Kitaplığınızın bir statik özelliği olduğu varsayıldığında `PI` , bu etiketi şu şekilde kullanabilirsiniz:

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## \<example>

`<example>`XML belgelerinize bir örnek eklemek için etiketini kullanın.
Bunun için alt etiketi kullanılması gerekir `<code>` .

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code`Etiket, daha uzun örnekler için satır sonlarını ve girintiyi korur.

## \<para>

`<para>`İçeriğini üst etiketi içinde biçimlendirmek için etiketini kullanın. `<para>` genellikle `<remarks>` `<returns>` metin paragraflarına bölmek için veya gibi bir etiket içinde kullanılır.
`<remarks>`Sınıf tanımınız için etiketin içeriğini biçimlendirebilirsiniz.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## \<c>

Biçimlendirme konusunda hala, `<c>` metnin bir kısmını kod olarak işaretlemek için etiketini kullanırsınız.
`<code>`Etiket, ancak satır içi gibi. Bir etiketin içeriğinin bir parçası olarak hızlı bir kod örneği göstermek istediğinizde yararlı olur.
Sınıfın belgelerini güncelleştirelim `Math` .

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## \<exception>

`<exception>`Etiketini kullanarak, geliştiricilerin bir yöntemin belirli özel durumlar oluşturduğunu bilmesini sağlar.
`Math`Kitaplığınıza bakarak, `Add` belirli bir koşul karşılanırsa her iki yöntemin de bir özel durum oluşturmasını sağlayabilirsiniz. Öyle değildir, ancak `Divide` parametrenin sıfır olması durumunda tamsayı yöntemi de oluşturulur `b` . Şimdi bu yönteme özel durum belgeleri ekleyin.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref`Öznitelik, geçerli derleme ortamında kullanılabilir olan bir özel duruma başvuruyu temsil eder.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir. Değeri çözülemezse, derleyici bir uyarı verebilir.

## \<see>

`<see>`Etiketi, başka bir kod öğesi için bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak sağlar. Sonraki örnekte, iki yöntem arasında tıklatılabilir bir bağlantı oluşturacağız `Add` .

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

, `cref` Geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eden **gerekli** bir özniteliktir.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.

## \<seealso>

`<seealso>`Etiketi, etiketi yaptığınız şekilde kullanırsınız `<see>` . Tek fark, içeriğinin genellikle bir "Ayrıca bkz." bölümüne yerleştirilme nedendir. Burada, tamsayı `seealso` `Add` parametrelerini kabul eden sınıftaki diğer yöntemlere başvurmak için tamsayı yöntemine bir etiket ekleyeceğiz:

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref`Öznitelik, geçerli derleme ortamında kullanılabilir olan bir türe veya üyesine başvuruyu temsil eder.
Bu, projede veya başvurulan bir derlemede tanımlanmış herhangi bir tür olabilir.

## \<param>

`<param>`Bir yöntemin parametrelerini anlatmak için etiketini kullanırsınız. Double yöntemine bir örnek aşağıda verilmiştir `Add` : etiketin açıkladığı parametre, **gerekli** `name` özniteliğinde belirtilir.

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## \<typeparam>

Etiketi `<typeparam>` tıpkı etiketi gibi kullanırsınız, `<param>` ancak genel tür veya yöntem bildirimlerinin genel bir parametreyi tanımlamasını sağlar.
`Math`Bir miktarın diğerinden daha büyük olup olmadığını denetlemek için sınıfınıza hızlı genel bir yöntem ekleyin.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## \<paramref>

Bazen bir yöntemin hangi bir etiketle ne olduğunu açıklayan ortasında olabilirsiniz `<summary>` ve bir parametreye başvuru yapmak isteyebilirsiniz. `<paramref>`Etiketi yalnızca bunun için harika. Double tabanlı yönteminizin özetini güncelleştirelim `Add` . Etiketi gibi `<param>` , parametre adı **gerekli** `name` özniteliğinde belirtilir.

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## \<typeparamref>

Etiketi `<typeparamref>` tıpkı etiketi gibi kullanırsınız, `<paramref>` ancak genel tür veya yöntem bildirimlerinin genel bir parametreyi tanımlamasını sağlar.
Daha önce oluşturduğunuz genel yöntemi kullanabilirsiniz.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## \<list>

`<list>`Belge bilgilerini sıralı liste, sırasız liste veya tablo olarak biçimlendirmek için etiketini kullanın. Kitaplığınızın desteklediği her matematik işleminin sıralanmamış bir listesini oluşturun `Math` .

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

`type`Özniteliği sırasıyla veya olarak değiştirerek sıralı bir liste veya tablo yapabilirsiniz `number` `table` .

## \<inheritdoc>

`<inheritdoc>`Temel sınıflardan, arabirimlerden ve benzer metotlardan XML açıklamalarını devralacak şekilde etiketini kullanabilirsiniz. Bu, yinelenen XML açıklamalarını istenmeyen kopyalama ve yapıştırmayı ortadan kaldırır ve otomatik olarak XML açıklamalarını eşitlenmiş halde tutar.

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a>Hepsini bir araya getirin

Bu öğreticiyi takip ediyorsanız ve gereken yere etiketleri kodunuza uyguladıysanız, kodunuzun aşağıdakine benzer şekilde görünmesi gerekir:

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Kodınızdan, tıklatılabilir çapraz başvurularla ayrıntılı bir belge Web sitesi oluşturabilirsiniz. Ancak başka bir sorunla karşılaşıyoruz: kodunuzun okunması zor oldu.
Bu koda katkıda bulunmak isteyen herhangi bir geliştirici için bu bir gece olacak şekilde, bu kadar çok bilgi vardır.
Bu konuda size yardımcı olabilecek bir XML etiketi vardı:

## \<include>

`<include>`Etiketi, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeyi aksine, kaynak kodunuzda türleri ve üyeleri tanımlayan ayrı bır XML dosyasındaki açıklamalara başvurmanıza olanak sağlar.

Artık tüm XML etiketlerinizi adlı ayrı bir XML dosyasına taşıyacağız `docs.xml` . Dosyayı istediğiniz şekilde adlandırabilirsiniz.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

Yukarıdaki XML 'de, her üyenin belge yorumu, ne yapacaklarıyla doğrudan adlı bir etiketin içinde görünür. Kendi stratejinizi seçebilirsiniz.
XML açıklamalarınız ayrı bir dosyada olduğuna göre, şu etiketi kullanarak kodunuzun daha okunaklı hale getirilme biçimini görelim `<include>` :

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Bu durumda: kodunuz okunabilir hale getirilir ve belge bilgisi kaybedilmiyor.

`file`Öznitelik, belgeleri IÇEREN XML dosyasının adını temsil eder.

`path`Öznitelik, belirtilen öğesinde var olan bir [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) sorgusunu temsil eder `tag name` `file` .

`name`Öznitelik, yorumlarla önce gelen etiketteki ad belirticisini temsil eder.

Yerine `id` kullanılabilecek özniteliği, `name` yorumların ÖNÜNDEKI etiketin kimliğini temsil eder.

### <a name="user-defined-tags"></a>Kullanıcı tanımlı Etiketler

Yukarıda özetlenen tüm Etiketler, C# derleyicisi tarafından tanınan olanları temsil eder. Ancak, bir Kullanıcı kendi etiketlerini tanımlayaücretsizdir.
Sandrole gibi araçlar, ve gibi ekstra Etiketler için destek getirme [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) ve hatta [ad alanlarını belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)desteği.
Özel veya şirket içi belge oluşturma araçları ayrıca standart Etiketler ve HTML 'den PDF 'ye birden çok çıktı biçimi ile kullanılabilir.

## <a name="recommendations"></a>Öneriler

Kodu belgeleme pek çok nedenden dolayı önerilir. Aşağıda, bazı en iyi yöntemler, genel kullanım örneği senaryoları ve C# kodunuzda XML belge etiketlerini kullanırken bilmeniz gereken noktalar verilmiştir.

- Tutarlılık açısından, herkese açık olarak görünen tüm türler ve üyeleri açıklanmalıdır. Bunu yapmanız gerekiyorsa, bunu yapın.
- Özel Üyeler ayrıca XML açıklamaları kullanılarak Belgelenebilir. Ancak bu, kitaplığınızın iç (potansiyel olarak gizli) işleyişini kullanıma sunar.
- En azından, türler ve üyeleri, `<summary>` IntelliSense için içerik gerektiğinden bir etikete sahip olmalıdır.
- Belge metni tam uyarılarla biten tam tümceler kullanılarak yazılmalıdır.
- Kısmi sınıflar tam olarak desteklenir ve belge bilgileri bu tür için tek bir girişte birleştirilir.
- Derleyici,,,, `<exception>` `<include>` `<param>` `<see>` `<seealso>` ve `<typeparam>` etiketlerinin sözdizimini doğrular.
- Derleyici dosya yolları içeren parametreleri ve kodun diğer bölümlerine başvuruları doğrular.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belgeleri Yorumları (C# Programlama Kılavuzu)](programming-guide/xmldoc/index.md)
- [Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
