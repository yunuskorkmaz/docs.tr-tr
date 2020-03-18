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
# <a name="document-your-code-with-xml-comments"></a>Kodunuzu XML yorumlarıyla belgele

XML dokümantasyon yorumları, kullanıcı tarafından tanımlanan herhangi bir tür veya üyetanımının üzerine eklenen özel bir yorum türüdür.
Derleyici tarafından derleyici tarafından derleme zamanında bir XML dokümantasyon dosyası oluşturmak için işlenebileceğinden özeldirler.
Derleyici tarafından oluşturulan XML dosyası .NET derlemenizin yanında dağıtılabilir, böylece Visual Studio ve diğer IDA'lar türleri veya üyeleri hakkında hızlı bilgi göstermek için IntelliSense'i kullanabilir. Ayrıca, XML dosyası API başvuru web siteleri oluşturmak için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) gibi araçlar aracılığıyla çalıştırılabilir.

XML dokümantasyon yorumları, diğer tüm yorumlar gibi derleyici tarafından yoksayılır.

Aşağıdakilerden birini yaparak XML dosyasını derleme zamanında oluşturabilirsiniz:

- Komut satırından .NET Core içeren bir uygulama geliştiriyorsanız, `GenerateDocumentationFile` .csproj proje dosyanızın bölümüne `<PropertyGroup>` bir öğe ekleyebilirsiniz. Ayrıca, [ `DocumentationFile` öğeyi](/visualstudio/msbuild/common-msbuild-project-properties)kullanarak doğrudan dokümantasyon dosyasına giden yolu da belirtebilirsiniz. Aşağıdaki örnek, proje dizininde derlemeyle aynı kök dosya adına sahip bir XML dosyası oluşturur:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   Bu, aşağıdakilere eşdeğerdir:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Visual Studio'yu kullanarak bir uygulama geliştiriyorsanız, projeye sağ tıklayın ve **Özellikler'i**seçin. Özellikler iletişim kutusunda, **Yapı** sekmesini seçin ve **XML belge dosyasını**denetleyin. Derleyicinin dosyayı yazdığı konumu da değiştirebilirsiniz.

- Komut satırından bir .NET Framework uygulaması derliyorsanız, derleme yaparken [-doc derleyici seçeneğini](language-reference/compiler-options/doc-compiler-option.md) ekleyin.  

XML dokümantasyon yorumları üçlü`///`ileri eğik çizgiler ( ) ve XML biçimlendirilmiş yorum gövdesi kullanır. Örnek:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Kılavuz

Yeni geliştiricilerin anlamasını/katkıda bulunmasını ve üçüncü taraf geliştiricilerin kullanmasını kolaylaştırmak için çok temel bir matematik kitaplığını belgeleme konusunda yürüyelim.

Burada basit matematik kitaplığı için kod:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Örnek kitaplık dört ana aritmetik `subtract` `multiply`işlemleri `divide`destekler `int` ( `double` `add`, , , ve ) ve veri türleri.

Artık kitaplığınızı kullanan ancak kaynak koduna erişimi olmayan üçüncü taraf geliştiriciler için kodunuzdan bir API başvuru belgesi oluşturmak istiyorsunuz.
Daha önce belirtildiği gibi XML belge etiketleri bunu başarmak için kullanılabilir. Şimdi C# derleyicisinin desteklediği standart XML etiketleri ile tanışır.

## <a name="summary"></a>\<summary>

Etiket, `<summary>` bir tür veya üye hakkında kısa bilgiler ekler.
Ben `Math` sınıf tanımı ve ilk `Add` yöntem ekleyerek kullanımını göstereceğim. Kodunuzun geri kalanına uygulamadan çekinmeyin.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

Etiket `<summary>` önemlidir ve içeriği IntelliSense'deki tür veya üye bilgilerinin birincil kaynağı veya API başvuru belgesi olduğundan etiketlemeyi eklemenizi öneririz.

## <a name="remarks"></a>\<açıklamalar>

Etiket, `<remarks>` `<summary>` etiketin sağladığı türveya üyeler hakkındaki bilgileri tamamlar. Bu örnekte, sınıfa eklemeniz gereken bir örnek.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

Etiket, `<returns>` yöntem bildiriminin dönüş değerini açıklar.
Daha önce olduğu gibi, `<returns>` aşağıdaki örnekte `Add` ilk yöntemdeki etiket gösterin. Aynı şeyi diğer yöntemlerde de yapabilirsiniz.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Etiket, `<value>` özellikleri için `<returns>` kullanmanız dışında etikete benzer.
Kitaplığınızın `Math` statik `PI`bir özelliği olduğunu varsayarsak, bu etiketi şu şekilde kullanırdınız:

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<örnek>

`<example>` Etiketi XML belgelerinize bir örnek eklemek için kullanırsınız.
Bu, alt `<code>` etiketini kullanmayı içerir.

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

Etiket, `code` satır sonları ve girintiyi daha uzun örnekler için korur.

## <a name="para"></a>\<para>

`<para>` Etiketi, ana etiketindeki içeriği biçimlendirmek için kullanırsınız. `<para>`genellikle bir etiket içinde kullanılır, gibi `<remarks>` veya `<returns>`, paragraflara metin bölmek için.
Sınıf tanımınız için `<remarks>` etiketin içeriğini biçimlendirebilirsiniz.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c>

Biçimlendirme konusunda hala, metnin `<c>` bir bölümünü kod olarak işaretlemek için etiketi kullanırsınız.
Bu `<code>` etiket gibi ama satır içinde. Bir etiketin içeriğinin bir parçası olarak hızlı bir kod örneği göstermek istediğinizde kullanışlıdır.
Sınıfın belgelerini `Math` güncelleyelim.

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<özel durum>

`<exception>` Etiketi kullanarak, geliştiricilerinize bir yöntemin belirli özel durumlar atabileceğini bildirin.
Kitaplığınıza `Math` baktığınızda, belirli bir `Add` koşul yerine getirildiğinde her iki yöntemin de özel bir durum ortaya çıkardığını görebilirsiniz. O kadar açık değil, ancak, `Divide` `b` parametre sıfır ise tamsayı yöntemi de atar. Şimdi bu yönteme özel durum belgeleri ekleyin.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

Öznitelik, `cref` geçerli derleme ortamından kullanılabilen bir özel durum için bir başvuruyu temsil eder.
Bu, projede tanımlanan herhangi bir tür veya başvurulan bir derleme olabilir. Derleyici, değeri çözülemiyorsa bir uyarı yayımlar.

## <a name="see"></a>\<bkz.>

Etiket, `<see>` başka bir kod öğesi için bir belgesayfasına tıklanabilir bir bağlantı oluşturmanıza olanak tanır. Bir sonraki örneğimizde, iki `Add` yöntem arasında tıklanabilir bir bağlantı oluştururuz.

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

Bu, `cref` geçerli derleme ortamından kullanılabilen bir türe veya üyesine yapılan başvuruyu temsil eden **gerekli** bir özniteliktir.
Bu, projede tanımlanan herhangi bir tür veya başvurulan bir derleme olabilir.

## <a name="seealso"></a>\<seealso>

`<seealso>` Etiketi, `<see>` etiketi yaptığınız gibi kullanırsınız. Tek fark, içeriğinin genellikle bir "Ayrıca Bak" bölümüne yerleştirilmiş olmasıdır. Burada tamsayı parametrelerini kabul eden `Add` sınıftaki diğer yöntemlere başvurmak için tamsayı yöntemine bir `seealso` etiket ekleyeceğiz:

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

Öznitelik, `cref` geçerli derleme ortamından kullanılabilen bir türe veya üyesine yapılan başvuruyu temsil eder.
Bu, projede tanımlanan herhangi bir tür veya başvurulan bir derleme olabilir.

## <a name="param"></a>\<param>

Bir yöntemin parametrelerini `<param>` açıklamak için etiketi kullanırsınız. Çift `Add` yöntemle ilgili bir örnek aşağıda verilmiştir: Etiketin açıkladığı parametre **gerekli** `name` öznitelikte belirtilir.

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam>

Etiketi etiket gibi, ancak genel bir parametreyi açıklamak için genel tür veya yöntem bildirimleri için kullanırsınız. `<typeparam>` `<param>`
Bir miktarın diğerinden `Math` büyük olup olmadığını denetlemek için sınıfınıza hızlı bir genel yöntem ekleyin.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref>

Bazen bir yöntemin `<summary>` etiket olabilecek bir şeyde ne yaptığını açıklamanın ortasında olabilirsiniz ve bir parametreye başvuruda bulunmak isteyebilirsiniz. Etiket `<paramref>` sadece bu için harika. Çift tabanlı `Add` yöntemimizin özetini güncelleyelim. `<param>` Etiket gibi, parametre adı da **gerekli** `name` öznitelikte belirtilir.

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref>

Etiketi etiket gibi, ancak genel bir parametreyi açıklamak için genel tür veya yöntem bildirimleri için kullanırsınız. `<typeparamref>` `<paramref>`
Daha önce oluşturduğunuz genel yöntemi kullanabilirsiniz.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<liste>

Etiketi, `<list>` belge bilgilerini sıralı bir liste, sıralanmamış liste veya tablo olarak biçimlendirmek için kullanırsınız. Kitaplığınızın `Math` desteklediği her matematik işleminin sıralanmamış bir listesini yapın.

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Sırasıyla özniteliği değiştirerek `type` sıralı bir liste `number` `table`veya tablo yapabilirsiniz.

## <a name="inheritdoc"></a>\<kalıtsal doc>

`<inheritdoc>` Etiketi, temel sınıflardan, arabirimlerden ve benzer yöntemlerden XML yorumlarını devralmak için kullanabilirsiniz. Bu, yinelenen XML yorumlarının istenmeyen kopyalanması ve yapıştırMasını ortadan kaldırır ve XML yorumlarını otomatik olarak senkronize eder.

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a>Hepsini bir araya getirin

Bu öğreticiyi takip ettiyseniz ve etiketleri gerektiğinde kodunuza uyguladıysanız, kodunuz artık aşağıdakilere benzer olmalıdır:

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Kodunuzdan, tıklanabilir çapraz referanslarla birlikte ayrıntılı bir dokümantasyon web sitesi oluşturabilirsiniz. Ama başka bir sorunla karşı karşıyasınız: kodunuzu okumak zor laştı.
Bu koda katkıda bulunmak isteyen herhangi bir geliştirici için bir kabus olacak bu elemek için çok fazla bilgi var.
Neyse ki bu başa yardımcı olabilecek bir XML etiketi var:

## <a name="include"></a>\<> dahil

Etiket, `<include>` belge yorumlarını doğrudan kaynak kod dosyanıza yerleştirmek yerine kaynak kodunuzdaki türleri ve üyeleri açıklayan ayrı bir XML dosyasındaki yorumlara başvurmanızı sağlar.

Şimdi tüm XML etiketlerinizi ayrı bir XML dosyasına `docs.xml`taşıyacaksın. Dosyaya istediğiniz ismi vermekte çekinmeyin.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

Yukarıdaki XML'de, her üyenin dokümantasyon yorumları doğrudan yaptıklarından sonra bir etiketin içinde görünür. Kendi stratejini seçebilirsin.
Artık XML yorumlarınızı ayrı bir dosyada gördüğünüze göre, `<include>` etiketi kullanarak kodunuzun nasıl daha okunabilir hale getirebileceğini görelim:

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Ve işte burada: kodumuz tekrar okunabilir hale döndü ve hiçbir belge bilgisi kaybedilmedi.

Öznitelik belgeleri `file` içeren XML dosyasının adını temsil eder.

Öznitelik `path` belirtilen `tag name` bugünü bir [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) sorgusu `file`temsil eder.

Öznitelik, `name` yorumlardan önce etiketteki adı belirtici temsil eder.

`id` Yerine `name`kullanılabilen öznitelik, yorumlardan önce gelen etiketin kimliğini temsil eder.

### <a name="user-defined-tags"></a>Kullanıcı tanımlı etiketler

Yukarıda özetlenen tüm etiketler, C# derleyicisi tarafından tanınan etiketleri temsil elerdir. Ancak, bir kullanıcı kendi etiketlerini tanımlamakta özgürdür.
Sandcastle gibi araçlar [ \<olay>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) ve [ \<not>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm)gibi ekstra etiketler için destek getirmek ve hatta ad alanlarını [belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)desteği.
Özel veya şirket içi dokümantasyon oluşturma araçları da standart etiketlerle kullanılabilir ve HTML'den PDF'ye birden fazla çıkış biçimi desteklenebilir.

## <a name="recommendations"></a>Öneriler

Kodu belgeleme birçok nedenden dolayı önerilir. C# kodunuzda XML belge etiketleri kullanırken bilmeniz gereken bazı en iyi uygulamalar, genel kullanım durumu senaryoları ve bilmeniz gereken şeyler aşağıda verilmiştir.

- Tutarlılık adına, herkesin önünde görülebilen tüm türler ve üyeleri belgelenmelidir. Eğer yapmak zorundaysan, hepsini yap.
- Özel üyeler xml yorumları kullanılarak da belgelenebilir. Ancak bu, kitaplığınızın iç (potansiyel olarak gizli) çalışmasını ortaya çıkarır.
- En azından, intelliSense için `<summary>` içeriği gerektiğinden, türleri ve üyeleri bir etikete sahip olmalıdır.
- Dokümantasyon metni tam duraklarla biten tam cümleler kullanılarak yazılmalıdır.
- Kısmi sınıflar tam olarak desteklenir ve belge bilgileri bu tür için tek bir girişe dönüştürülecektir.
- `<exception>`Derleyici, `<include>`, , `<param>` `<see>`, `<seealso>`, , ve `<typeparam>` etiketlerin sözdizimini doğrular.
- Derleyici, dosya yolları ve kodun diğer bölümlerine başvurular içeren parametreleri doğrular.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belgeleri Yorumları (C# Programlama Kılavuzu)](programming-guide/xmldoc/index.md)
- [Belge Açıklamaları için Önerilen Etiketler (C# Programlama Kılavuzu)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
