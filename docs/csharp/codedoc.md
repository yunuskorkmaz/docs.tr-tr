---
title: "XML açıklamaları ile kodunuzu belgeleme"
description: "XML belgeleri yorumları ile kodunuzu belgeleme ve derleme zamanında XML belge dosyası oluşturma hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 02/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 709ef2ba2202e69ba35834789ad6e743a0f6b719
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="documenting-your-code-with-xml-comments"></a>XML açıklamaları ile kodunuzu belgeleme

XML belgeleri yorumları açıklama, herhangi bir kullanıcı tanımlı tür veya üye tanımı eklendi özel bir tür var. Derleme zamanında XML belge dosyası oluşturmak için derleyici tarafından işlenebilir çünkü bunlar özel.
Visual Studio ve diğer IDE IntelliSense türler veya üyeler hakkında hızlı bilgi göstermek için kullanabilmesi için oluşturulan derleyici XML dosyası yanı sıra, .NET derleme dağıtılabilir. Ayrıca, XML dosyası gibi araçlar aracılığıyla çalıştırılabilir [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) API başvuru Web siteleri oluşturmak için.

XML belgeleri yorumları, diğer tüm yorumlar gibi derleyici tarafından göz ardı edilir.

Aşağıdakilerden birini yaparak derleme zamanında XML dosyası oluşturabilirsiniz:

- Ekleyebileceğiniz, .NET Core uygulamayla komut satırından geliştirmekte olduğunuz varsa, bir [DocumentationFile öğesi](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) için `<PropertyGroup>` .csproj proje dosyanızı bölümü. Aşağıdaki örnek, aynı kök filename derlemeyle ile proje dizininde bir XML dosyası oluşturur:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   XML dosyasının adı ve tam mutlak veya göreli yolunu da belirtebilirsiniz. Aşağıdaki örnek, bir uygulamanın hata ayıklama sürümü ile aynı dizinde XML dosyası oluşturur:

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- Visual Studio kullanarak bir uygulama geliştiriyorsanız, sağ tıklatın ve proje **özellikleri**. Özellikler iletişim kutusunda seçin **yapı** sekmesini tıklatın ve denetleme **XML belge dosyası**. Ayrıca, dosyanın derleyici yazacağı konumu değiştirebilirsiniz. 

- Bir .NET Framework uygulamasını komut satırından derleme varsa ekleyin [/doc derleyici seçeneği](language-reference/compiler-options/doc-compiler-option.md) derlerken.  

XML belgeleri yorumları Üçlü eğik kullanın (`///`) ve bir XML açıklama gövdesini biçimlendirilmiş. Örneğin:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>İzlenecek yol

Şimdi yeni geliştiricilerin anlamak ve katkıda ve kullanmak üçüncü taraf geliştiriciler için kolaylaştırmak için bir temel matematik kitaplığı belgeleme aracılığıyla yol.

Kod basit matematik kitaplığı aşağıdadır:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Dört ana aritmetik işlemler örnek kitaplığı destekleyen `add`, `subtract`, `multiply` ve `divide` üzerinde `int` ve `double` veri türleri.

Şimdi bir API başvuru belge kitaplığınızın kullanır ancak kaynak kodu erişiminiz yoksa üçüncü taraf geliştiriciler için kodunuzdan oluşturmak kullanabilmek ister.
Bunu başarmak için belirtilen önceki XML belge etiketleri kullanılabilir gibi standart XML etiketleri C# Derleyici destekler şimdi görülecektir.

### <a name="ltsummarygt"></a>&lt;Özet&gt;

`<summary>` Etiketi bir tür veya üye hakkında kısa bilgi ekler.
Ekleyerek ı kullanımını gösterir `Math` sınıf tanımı ve ilk `Add` yöntemi. Kodunuzun geri kalanı için uygulanacak çekinmeyin.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Etiketi çok önemlidir ve içeriğini birincil bilgi kaynağı olarak tür veya üye IntelliSense ya da bir API başvuru belgesini olduğundan bunu dahil öneririz.

### <a name="ltremarksgt"></a>&lt;Açıklamalar&gt;

`<remarks>` Etiketi tamamlayan türleri veya üyeleri hakkındaki bilgileri, `<summary>` etiketi sağlar. Bu örnekte, yalnızca onu sınıfa eklemeniz.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a>&lt;döndürür&gt;

`<returns>` Etiketi bir yöntem bildirimi dönüş değerini açıklar.
Önce aşağıdaki örnekte gösterildiği gibi `<returns>` ilk etiketinde `Add` yöntemi. Diğer yöntemler hakkında aynı yapabilirsiniz.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a>&lt;değer&gt;

`<value>` Etiketi benzer `<returns>` özelliklerini dışında kullanmasını etiketi.
Varsayarak, `Math` kitaplığı adlı bir statik özelliğe sahip `PI`, İşte bu etiketin nasıl kullanırsınız:

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a>&lt;Örnek&gt;

Kullandığınız `<example>` örnek XML belgelerinizde içerecek şekilde etiketi.
Bu alt kullanılmasına `<code>` etiketi.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Etiket, satır sonları ve girinti uzun örnekleri için korur.

### <a name="ltparagt"></a>&lt;para&gt;

Kullandığınız `<para>` kendi üst etiketinin içinde içeriği biçimlendirmek için etiketi. `<para>`genellikle bir etiketinin içine gibi kullanılan `<remarks>` veya `<returns>`, metin paragraflara bölmek için.
İçeriği biçimlendirmek `<remarks>` Sınıf tanımınız için etiket.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a>&lt;c&gt;

Biçimlendirme hala konuyla ilgili, kullandığınız `<c>` kod olarak metnin bir bölümünü işaretlemek etiketi.
Benzer; `<code>` etiketi ancak satır içi. Hızlı kod örneği bir etiketin içeriği bir parçası olarak göstermek istediğinizde kullanışlıdır.
Şimdi belgelerine güncelleştirme `Math` sınıfı.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a>&lt;özel durumu&gt;

Kullanarak `<exception>` etiketi, bir yöntem belirli istisnalar atabilirsiniz biliyorsanız, geliştiricilerin sağlar.
Bakarak, `Math` kitaplığı görebilirsiniz her ikisi de `Add` yöntemleri, belirli bir koşul karşılandığında bir özel durum atar. Değil yine de o kadar belirgin tamsayıdır `Divide` yöntemi atar de varsa `b` parametresi sıfırda. Şimdi bu yöntemi özel durum belgelerine ekleyin.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Öznitelik geçerli derleme ortamından kullanılabilir bir özel durum başvuru temsil eder.
Bu proje veya başvurulan bir derleme tanımlanan herhangi bir türü olabilir. Değerini çözümlenemiyorsa derleyici bir uyarı verecek.

### <a name="ltseegt"></a>&lt;bkz:&gt;

`<see>` Etiketi için başka bir kod öğesi bir belge sayfasına tıklatılabilir bir bağlantı oluşturmanıza olanak sağlar. Sonraki Örneğimizde, ikisi arasındaki tıklatılabilir bir bağlantı oluşturacağız `Add` yöntemleri.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` Olan bir **gerekli** temsil eden bir tür ya da geçerli derleme ortamından kullanılabilir kendi üyesi başvuru özniteliği. Bu proje veya başvurulan bir derleme tanımlanan herhangi bir türü olabilir.

### <a name="ltseealsogt"></a>&lt;SeeAlso&gt;

Kullandığınız `<seealso>` bunu aynı şekilde etiketinde `<see>` etiketi. Tek fark, içeriği genellikle "bir Ayrıca bkz:" bölümünde yerleştirilir ' dir. Burada ekleyeceğiz bir `seealso` üzerinde tamsayı etiketi `Add` tamsayı parametreleri kabul eden diğer sınıfı yöntemleri başvurmak için yöntemi:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Öznitelik bir tür ya da geçerli derleme ortamından kullanılabilir kendi üyesi başvuru temsil eder.
Bu proje veya başvurulan bir derleme tanımlanan herhangi bir türü olabilir.

### <a name="ltparamgt"></a>&lt;param&gt;

Kullandığınız `<param>` bir yöntemin parametre açıklamak için etiket. İşte bir örnek üzerinde çift `Add` yöntemi: Etiket açıklar parametresi belirtilen **gerekli** `name` özniteliği.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

Kullandığınız `<typeparam>` tıpkı etiketi `<param>` etiketi ancak genel bir parametreye açıklamak genel türü veya yöntemi bildirimleri.
Hızlı bir genel yöntem ekleme, `Math` sınıfı bir miktar diğerinden daha büyük olup olmadığını denetleyin.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

Bazen ne olabilir bir yöntem yaptığı açıklayan ortasında olabilir bir `<summary>` etiketi ve bir parametre için bir başvuru yapmak isteyebilirsiniz. `<paramref>` Etiketi yalnızca bu iş için mükemmeldir. Şimdi güncelleştirme bizim çift özetini dayalı `Add` yöntemi. Gibi `<param>` parametre adı belirtilen etiket **gerekli** `name` özniteliği.

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

Kullandığınız `<typeparamref>` tıpkı etiketi `<paramref>` etiketi ancak genel bir parametreye açıklamak genel türü veya yöntemi bildirimleri.
Daha önce oluşturduğunuz aynı genel yöntemini kullanabilirsiniz.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a>&lt;Liste&gt;

Kullandığınız `<list>` bir sıralı liste, sırasız liste veya tablo olarak biçimi belgelerine bilgilere etiketi.
Her matematik işlemi düzenlenmemiş bir listesini olun, `Math` kitaplığı destekler.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Sıralı liste veya tablo değiştirerek yapabilirsiniz `type` özniteliğini `number` veya `table`sırasıyla.

### <a name="putting-it-all-together"></a>Tüm bir araya getirme

Bu öğretici izleyen ve gerektiğinde etiketleri kodunuzu uygulanan, kodunuzu aşağıdakine benzer görünmelidir:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Kodunuz aracılığıyla, ayrıntılı belgelere Web sitesi ile tıklanabilir çapraz tam oluşturabilirsiniz. Ancak başka bir sorun karşılaştığı: kodunuzun okunması zor hale gelmiştir.
Bu onarımı kabus için bu kodu katkıda isteyen herhangi bir geliştirici olarak işaretleneceğini çalışılamayacak kadar çok bilgi bulunmaktadır. Thankfully yapmam yardımcı olabilecek bir XML etiketi vardır:

### <a name="ltincludegt"></a>&lt;içerir&gt;

`<include>` Etiketi türlerini açıklayan ayrı bir XML dosyası açıklamaları ve belge açıklamaları doğrudan, kaynak kodu dosyasına yerleştirerek aksine, kaynak kodunuzu üyelerinde bakın olanak sağlar.

Tüm XML etiketleri adlı ayrı bir XML dosyasına taşınır oluşturacağız artık `docs.xml`. İstediğiniz dosyanın adını çekinmeyin.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

Yukarıdaki XML'de her üyenin belge açıklamaları doğrudan ne yaptıklarını sonra adlı etiket içinde görüntülenir. Kendi stratejisi seçebilirsiniz. Ayrı bir dosyada XML yorumlarınızı sahip olduğunuza göre nasıl kodunuzu kullanarak daha okunabilir hale getirilebilir görelim `<include>` etiketi:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Ve elinizde vardır: okunabilir olması geri bizim koddur ve belgeleri bilgi kaybedildi. 

`filename` Öznitelik belgeleri içeren XML dosyasının adını temsil eder.

`path` Özniteliğini temsil bir [XPath](https://msdn.microsoft.com/library/ms256115.aspx) için sorgu `tag name` mevcut belirtilen `filename`.

`name` Öznitelik açıklamaları önündeki etiketinde ad belirticisi temsil eder.

`id` Yerine kullanılan öznitelik `name` açıklamaları önündeki etiket Kimliğini temsil eder.

### <a name="user-defined-tags"></a>Etiketler kullanıcı tanımlı

Yukarıda özetlenen tüm etiketleri, C# Derleyici tarafından tanınan temsil eder. Ancak, bir kullanıcı kendi etiketleri tanımlamak ücretsizdir.
Sandcastle gibi araçlar ek etiketleri ister için destek Getir [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) ve hatta Destek [ad alanları belgeleme](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Birden çok çıktı biçimlerinden HTML PDF için desteklenen ve özel veya şirket içi belgeleri oluşturma araçları ile standart etiketleri de kullanılabilir.

## <a name="recommendations"></a>Önerileri

Kod belgeleme nedenlerle önerilir. Hangi aşağıdaki gibi bazı en iyi uygulamalar, genel örneği senaryolarının ve ne zaman XML belgelerini kullanarak etiketleri, C# kodunda bilmeniz gereken şeyleri kullanın.

* Tutarlılık sağlamak, tüm herkese görünür türleri ve üyeleri belgelenen. Bunu yapmanız gerekir, bunu tüm.
* Özel üyelerin XML açıklamaları kullanarak da belgelenen. Ancak, bu kitaplığınızın (büyük olasılıkla gizli) çalışmalar kullanıma sunar.
* Tam en azından türleri ve üyeleri olmalıdır bir `<summary>` içeriği için IntelliSense gerektiğinden etiketi.
* Tam durakları ile biten bütün cümleleri kullanarak belge metin yazılması gerekir.
* Kısmi sınıflar tam olarak desteklenir ve belgeleri bilgi türü için tek bir giriş içine birleştirilmiş.
* Söz dizimi derleyici doğrular `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` ve `<typeparam>` etiketler.
- Derleyici dosya yolları ve diğer bölümleri kodunun başvuruları içeren parametreleri doğrular.

## <a name="see-also"></a>Ayrıca bkz.
[XML belgeleri yorumları (C# programlama Kılavuzu)](programming-guide/xmldoc/xml-documentation-comments.md)

[Belge açıklamaları (C# programlama Kılavuzu) için önerilen etiketler](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
