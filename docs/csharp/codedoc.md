---
title: XML açıklamalarıyla kodunuzu belgeleme
description: XML belgeleri yorumları ile kodunuzu belgeleme ve derleme zamanında XML belge dosyası oluşturma hakkında bilgi edinin.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 15bdd65b96159b4c9b6eb45016f8bdde58c1efe3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576206"
---
# <a name="documenting-your-code-with-xml-comments"></a>XML açıklamalarıyla kodunuzu belgeleme

XML belgeleri yorumları herhangi bir kullanıcı tanımlı tür veya üye tanımı eklenen açıklama, özel bir tür var.
Derleme zamanında XML belge dosyası oluşturmak için derleyici tarafından işlenebilir çünkü bunlar özeldir.
Böylece Visual Studio ve diğer Ide'leri IntelliSense türleri veya üyeleri hakkında hızlı bilgi göstermek için kullanabilirsiniz, derleyicinin ürettiği XML dosyasının yanı sıra .NET bütünleştirilmiş kodunuzda dağıtılabilir. Ayrıca, XML dosyasını gibi araçlarla çalıştırılabilir [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) API Başvurusu Web siteleri oluşturmak için.

XML belgeleri yorumları, diğer açıklamaları gibi derleyici tarafından göz ardı edilir.

XML dosyası, aşağıdakilerden birini yaparak, bir derleme zamanında oluşturabilirsiniz:

- Ekleyebileceğiniz komut satırından .NET Core ile bir uygulama varsa geliştiriyorsanız, bir [DocumentationFile öğesi](/visualstudio/msbuild/common-msbuild-project-properties) için `<PropertyGroup>` .csproj proje dosyanızın bölümü. Aşağıdaki örnek, proje dizinine derleme olarak aynı kök dosya adına sahip bir XML dosyası oluşturur:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   XML dosyasının adını ve tam mutlak veya göreli yolu belirtebilirsiniz. Aşağıdaki örnek, bir uygulamanın hata ayıklama sürümü ile aynı dizinde XML dosyası oluşturur:

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- Visual Studio kullanarak bir uygulama geliştiriyorsanız sağ tıklatın ve proje **özellikleri**. Özellikler iletişim kutusunda, seçmek **derleme** sekmesini tıklatıp denetleyin **XML belge dosyası**. Ayrıca, derleyici dosyayı yazacağı konum değiştirebilirsiniz.

- Bir .NET Framework uygulamasına komut satırından derleme yapıyorsanız ekleme [/doc derleyici seçeneği](language-reference/compiler-options/doc-compiler-option.md) derlenirken.  

XML belgeleri yorumları üç eğik çizgi kullanın (`///`) ve bir XML biçimli yorum gövdesi. Örneğin:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>İzlenecek yol

Anlama ve katkıda yeni geliştiricilerin ve üçüncü taraf geliştiriciler için kolaylaştıran bir çok temel matematik kitaplığı belgeleme aracılığıyla atalım.

Kodu basit matematik kitaplığı şu şekildedir:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Örnek kitaplığı dört temel aritmetik işlemleri destekler `add`, `subtract`, `multiply` ve `divide` üzerinde `int` ve `double` veri türleri.

Artık kitaplığınızı kullanan ancak kaynak koduna erişiminiz yoksa üçüncü taraf geliştiriciler için kodunuzdan bir API başvuru belgesi oluşturmak yönetebilmek istiyorsunuz.
Daha önce belirtildiği gibi XML belge etiketleri Bunu başarmak için kullanılabilir. Artık için standart XML etiketlerini görülecektir C# derleyici destekler.

### <a name="ltsummarygt"></a>&lt;Özeti&gt;

`<summary>` Etiketi bir tür veya üye hakkında kısa bilgiler ekler.
Ben ekleyerek kullanımını kazandırabileceğinizi göstereceğiz `Math` sınıf tanımı ve ilk `Add` yöntemi. Kodunuzun geri kalanı için geçerli çekinmeyin.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Etiketi çok önemlidir ve içeriği IntelliSense ya da bir API başvuru belgesini türe veya üyeye bilgilerinin birincil kaynağı olduğundan, dahil öneririz.

### <a name="ltremarksgt"></a>&lt;Açıklamalar&gt;

`<remarks>` Etiketi tamamlayan türleri veya üyeleri hakkında bilgi, `<summary>` etiketi sağlar. Bu örnekte, yalnızca bu sınıfa ekleyeceksiniz.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a>&lt;döndürür&gt;

`<returns>` Etiketi dönüş değeri bir yöntem bildiriminde açıklanmaktadır.
Önce aşağıdaki örnekte gösterildiği gibi `<returns>` ilk etiket `Add` yöntemi. Diğer yöntemler hakkında aynısını yapabilir.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a>&lt;value&gt;

`<value>` Etiketi benzer `<returns>` özelliklerini kullanmasını dışında etiketleyin.
Varsayarak, `Math` kitaplığı adlı statik bir özellik olan `PI`, İşte bu etiketi nasıl kullanırsınız:

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a>&lt;Örnek&gt;

Kullandığınız `<example>` örneği, XML belgelerinde dahil etmek için etiket.
Bu alt kullanılmasına `<code>` etiketi.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Etiketi satır sonu ve girinti uzun örnekleri için korur.

### <a name="ltparagt"></a>&lt;para&gt;

Kullandığınız `<para>` kendi üst etiketinin içinde içeriği biçimlendirmek için etiket. `<para>` genellikle gibi bir etiket içinde kullanılan `<remarks>` veya `<returns>`paragraflara metin ayırmak için.
İçeriğini biçimlendirebilirsiniz `<remarks>` sınıfı tanımınız için etiket.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a>&lt;c&gt;

Biçimlendirme hala konusu, kullandığınız `<c>` metin olarak kod parçası olarak işaretlemek için etiket.
Nasıl olduğunu `<code>` etiketi ancak satır içi. Hızlı kod örneği bir etiketin içeriği bir parçası olarak göstermek istediğinizde yararlıdır.
Belgelerine güncelleştirelim `Math` sınıfı.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a>&lt;özel durum&gt;

Kullanarak `<exception>` etiketi, bir yöntemi özel durum oluşturabilecek, geliştiricilere sağlar.
Bakarak, `Math` kitaplığı, gördüğünüz gibi her ikisi de `Add` yöntemleri, belirli bir koşul karşılandığında bir özel durum oluşturur. Değil yine de o kadar belirgin tamsayıdır `Divide` yöntemi oluşturursa yanı, `b` parametresi sıfırsa. Artık özel durum belgeleri bu yöntemine ekleyin.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Öznitelik geçerli derleme ortamdan kullanılabilir bir özel durum başvuru temsil eder.
Bu proje ya da başvurulan bir derlemede tanımlanan herhangi bir türü olabilir. Değerini çözümlenemezse, derleyici bir uyarı verir.

### <a name="ltseegt"></a>&lt;Bkz:&gt;

`<see>` Etiketi başka bir kod öğesi için bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak tanır. Sonraki Örneğimizde, ikisi arasındaki tıklatılabilir bir bağlantı oluşturacağız `Add` yöntemleri.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` Olduğu bir **gerekli** temsil eden bir tür veya geçerli derleme ortamdan kullanılabilir olan kendi üyesi başvuru özniteliği.
Bu proje ya da başvurulan bir derlemede tanımlanan herhangi bir türü olabilir.

### <a name="ltseealsogt"></a>&lt;SeeAlso&gt;

Kullandığınız `<seealso>` bunu aynı şekilde etiketi `<see>` etiketi. Tek fark, içeriği genellikle "bir Ayrıca bkz:" bölümünde yerleştirilir. Buraya ekleyeceğiz bir `seealso` üzerinde tamsayı etiketi `Add` tamsayı parametre kabul eden diğer sınıfı yöntemleri başvurmak için yöntemi:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Öznitelik, bir tür veya geçerli derleme ortamdan kullanılabilir olan kendi üyesi başvuru temsil eder.
Bu proje ya da başvurulan bir derlemede tanımlanan herhangi bir türü olabilir.

### <a name="ltparamgt"></a>&lt;param&gt;

Kullandığınız `<param>` bir yöntemin parametre açıklamak için etiket. İşte bir örnek üzerinde iki `Add` yöntemi: Etiket açıklar parametresi belirtildiğinden **gerekli** `name` özniteliği.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

Kullandığınız `<typeparam>` tıpkı etiketi `<param>` etiketi ancak genel parametre açıklamak genel tür veya yöntem bildirimleri.
Hızlı bir genel yöntem ekleme, `Math` bir miktar diğerinden daha büyük olup olmadığı denetlenecek sınıfı.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

Bazen ne olabilir bir yöntem ne yaptığını açıklayan ortasında olabilir bir `<summary>` etiketi ve parametre başvurusu yapmak isteyebilirsiniz. `<paramref>` Etikettir yalnızca bu harika. Şimdi güncelleştirme özeti sayfamızda çift tabanlı `Add` yöntemi. Gibi `<param>` parametre adı belirtilen etiketi **gerekli** `name` özniteliği.

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

Kullandığınız `<typeparamref>` tıpkı etiketi `<paramref>` etiketi ancak genel parametre açıklamak genel tür veya yöntem bildirimleri.
Daha önce oluşturduğunuz genel aynı yöntemi kullanabilirsiniz.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a>&lt;list&gt;

Kullandığınız `<list>` etiket biçimi belgeleri bilgilerine bir sıralı liste, sırasız liste veya tablo.
Sırasız bir listesini her matematik işleminin olun, `Math` kitaplığı destekler.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Bir sıralı listeyi veya tabloyu değiştirerek yapabilirsiniz `type` özniteliğini `number` veya `table`sırasıyla.

### <a name="putting-it-all-together"></a>Hepsini birleştirme

Bu öğreticiyi takip ve gerektiğinde etiketleri, koda uygulandı, kodunuzun aşağıdakine benzer görünmelidir:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Kodunuz aracılığıyla ayrıntılı belgeler Web sitesi ile tıklanabilir çapraz tam oluşturabilirsiniz. Ancak başka bir sorun yaşadığınız: kodunuzu okunması zor hale geldi.
Bu bir onarımı kabus bu koda katkıda bulunmak isteyen bir geliştirici olarak gittiği çalışılamayacak için çok fazla bilgi bulunmaktadır.
Ne yapmam yardımcı olabilecek bir XML etiket vardır:

### <a name="ltincludegt"></a>&lt;include&gt;

`<include>` Etiket türleri açıklayan yorumlar ayrı bir XML dosyasında ve doğrudan sizin kaynak kodu dosyasında belge açıklamaları yerleştirme aksine, kaynak kodunuzdaki üyelerine başvurmak olanak tanır.

Tüm XML etiketlerini adlı ayrı bir XML dosyasına taşımak soracağız `docs.xml`. İstediğiniz dosya adı çekinmeyin.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

Yukarıdaki XML'de her üyenin belge açıklamaları doğrudan yapabileceklerini sonra adlı bir etiket içinde görünür. Kendi stratejisi seçebilirsiniz.
Ayrı bir dosyada XML yorumlarınızı sahip olduğunuza göre şimdi nasıl kodunuzu kullanarak daha okunabilir hale getirilebilir bakalım `<include>` etiketi:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Ve elinizde vardır: okunabilir olan geri kodumuz olduğundan ve hiçbir belge bilgi kaybı olmadı.

`filename` Öznitelik belgeleri içeren XML dosyasının adını temsil eder.

`path` Özniteliğini temsil eder bir [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) için sorgu `tag name` belirtilen mevcut `filename`.

`name` Öznitelik ad tanımlayıcısı açıklamaları önündeki etiketinde temsil eder.

`id` Yerine kullanılan öznitelik `name` açıklamaları önünde etiket Kimliğini temsil eder.

### <a name="user-defined-tags"></a>Kullanıcı tanımlı etiketleri

Yukarıda özetlenen tüm etiketleri, C# derleyicisi tarafından tanınmaktadır temsil eder. Ancak, bir kullanıcı kendi etiketleri tanımlamak ücretsizdir.
Sandcastle gibi araçları ister ek etiketleri için destek Getir [ `<event>` ](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) ve hatta Destek [ad alanları belgeleme](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Özel veya şirket içi belge oluşturma araçları ile standart etiketleri de kullanılabilir ve HTML'den PDF birden çok çıkış biçimleri desteklenir.

## <a name="recommendations"></a>Öneriler

Kod belgeleme çeşitli nedenlerle önerilir. Aşağıda bazı en iyi yöntemler, genel örneği senaryolarını ve ne zaman XML belgeleri kullanarak etiketleri, C# kodunuzda bilmeniz gerekenler şeyler kullanın.

* Tutarlılık sağlamak, tüm genel olarak görülebilir tür ve üyelerin belgelenmelidir. Bunu yapmanız gerekir, tüm yapın.
* Ayrıca özel üyeler XML açıklamaları kullanarak da belgelenecektir. Ancak, bunu kitaplığınızın (büyük olasılıkla gizli) çalışmalar kullanıma sunar.
* Çıplak en azından, türleri ve üyeleri olmalıdır bir `<summary>` içeriği için IntelliSense gerektiğinden etiketleyin.
* Tam durakları ile biten bütün cümleleri kullanarak belge metnini yazılması gerekir.
* Kısmi sınıflar tam olarak desteklenir ve belgelendirme bilgilerini tek bir giriş türü için içine birleştirilir.
* Derleyici sözdizimini doğrular `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` ve `<typeparam>` etiketler.
- Derleyici dosya yolları ve kodun diğer bölümleri için başvuruları içeren parametrelerini doğrular.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belgeleri yorumları (C# programlama Kılavuzu)](programming-guide/xmldoc/xml-documentation-comments.md)
- [Belge açıklamaları (C# programlama Kılavuzu) için önerilen etiketler](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
