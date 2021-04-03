---
title: C# kodlama kuralları-C# Programlama Kılavuzu
description: C# ' de kodlama kuralları hakkında bilgi edinin. Kodlama kuralları koda tutarlı bir görünüm oluşturur ve kodun kopyalanmasını, değiştirilmesini ve bakımının yapılmasını kolaylaştırır.
ms.date: 03/31/2021
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.openlocfilehash: 019bf02ea3cdfec2c4ae0d73b5b375781c5fcd9a
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231329"
---
# <a name="c-coding-conventions-c-programming-guide"></a>C# Kodlama Kuralları (C# Programlama Kılavuzu)

Kodlama kuralları aşağıdaki amaçlara hizmet eder:  
  
- Bunlar, koda tutarlı bir görünüm oluşturur, böylece okuyucular düzene göre değil, içeriğe odaklanabilir.  
  
- Bu kullanıcılar, önceki deneyimle dayalı varsayımlar yaparak okuyucuların kodu daha hızlı anlamasına imkan sağlar.  
  
- Kodu kopyalama, değiştirme ve sürdürme işlemlerini kolaylaştırır.  
  
- C# En Iyi yöntemlerini gösterir.  

Bu makaledeki yönergeler, Microsoft tarafından örnek ve belge geliştirmek için kullanılır.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları  
  
- [Yönergeleri kullanarak](../../language-reference/keywords/using-directive.md)dahil olmayan kısa örneklerde ad alanı nitelikleri kullanın. Bir ad alanının bir projede varsayılan olarak içeri aktarıldığını biliyorsanız, adları bu ad alanından tam olarak nitelemeniz gerekmez. Nitelenmiş adlar, aşağıdaki örnekte gösterildiği gibi, tek bir satırda çok uzunsa bir nokta (.) sonrasında bozulabilir.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet1":::

- Visual Studio tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını, diğer yönergelere uyum sağlamak için değiştirmeniz gerekmez.  
  
## <a name="layout-conventions"></a>Düzen kuralları  

İyi düzen, kodunuzun yapısını vurgulamak ve kodun daha kolay okunmasını sağlamak için biçimlendirme kullanır. Microsoft örnekleri ve örnekleri aşağıdaki kurallara uygun şekilde yapılır:  
  
- Varsayılan kod Düzenleyicisi ayarlarını (akıllı girintileme, dört karakterlik girintiler, sekmeler boşluk olarak kaydedilir) kullanın. Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici, C#, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
- Her satırda yalnızca bir ifade yazın.  
  
- Her satırda yalnızca bir bildirim yazın.  
  
- Devamlılık satırları otomatik olarak girintili değilse, bir sekme durağı (dört boşluk) için girinti yapın.  
  
- Yöntem tanımları ve özellik tanımları arasına en az bir boş satır ekleyin.  
  
- Aşağıdaki kodda gösterildiği gibi, bir ifadedeki tümceleri görünür hale getirmek için parantezleri kullanın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet2":::

## <a name="commenting-conventions"></a>Yorum oluşturma kuralları  
  
- Yorumu bir kod satırının sonuna değil, ayrı bir satıra yerleştirin.  
  
- Açıklama metnini büyük harfle Başlat.  
  
- Açıklama metnini noktayla bitirin.  
  
- Aşağıdaki örnekte gösterildiği gibi açıklama sınırlayıcısı (//) ve açıklama metni arasına bir boşluk ekleyin.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet3":::

- Yorumlar etrafında yıldız işareti blokları oluşturmayın.  
  
## <a name="language-guidelines"></a>Dil yönergeleri  

Aşağıdaki bölümlerde, C# ekibinin kod örneklerini ve örnekleri hazırlamak için izlediği uygulamalar açıklanır.  
  
### <a name="string-data-type"></a>Dize veri türü  
  
- Aşağıdaki kodda gösterildiği gibi, kısa dizeleri birleştirmek için [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) kullanın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet6":::

- Döngülerde dizeleri eklemek için, özellikle büyük miktarlarda metinle çalışırken bir <xref:System.Text.StringBuilder> nesnesi kullanın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

### <a name="implicitly-typed-local-variables"></a>Örtülü olarak belirtilmiş yerel değişkenler  
  
- Değişkenin türü atamanın sağ tarafından açık olduğunda veya kesin tür önemli olmadığında yerel değişkenler için [örtülü yazma](../classes-and-structs/implicitly-typed-local-variables.md) kullanın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet8":::
  
- Tür atamanın sağ tarafından görünmüyorsa, [yok kullanmayın.](../../language-reference/keywords/var.md) Türün bir yöntem adından temiz olduğunu varsaymayın. Bir değişken türü, bir `new` işleç veya açık bir tür ise Clear olarak değerlendirilir.
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet9":::

- Değişkenin türünü belirtmek için değişken adına güvenmeyin. Doğru olmayabilir. Aşağıdaki örnekte, değişken adı `inputInt` yanıltıcıdır. Bu bir dizedir.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet10":::

- Dinamik yerine kullanılmasını önleyin `var` . [](../../language-reference/builtin-types/reference-types.md) `dynamic`Çalışma zamanı tür çıkarımı istediğinizde kullanın. Daha fazla bilgi için bkz. [dinamik tür kullanımı (C# Programlama Kılavuzu)](../types/using-type-dynamic.md).
  
- Döngülerde içindeki döngü değişkeninin türünü [öğrenmek için örtük](../../language-reference/keywords/for.md) yazma kullanın.  
  
  Aşağıdaki örnek, bir bildiriminde örtük yazma kullanır `for` .  

    :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

- [Foreach](../../language-reference/keywords/foreach-in.md) Döngülerde döngü değişkeninin türünü anlamak için örtük yazma kullanmayın.

  Aşağıdaki örnek, bir bildiriminde açık bir yazma kullanır `foreach` .

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet12":::

  > [!NOTE]
  > Yinelenebilir bir koleksiyonun öğe türünü yanlışlıkla değiştirmemeye dikkat edin. Örneğin, bir <xref:System.Linq.IQueryable?displayProperty=nameWithType> <xref:System.Collections.IEnumerable?displayProperty=nameWithType> sorgunun yürütülmesini değiştiren bir ifadede öğesine geçiş yapmak kolaydır `foreach` .

### <a name="unsigned-data-types"></a>İmzasız veri türleri  
  
Genel olarak, `int` imzasız türler yerine kullanın. Kullanımı `int` C# ' nin tamamında ortaktır ve kullandığınızda diğer kitaplıklarla etkileşim kurmak daha kolaydır `int` .  
  
### <a name="arrays"></a>Diziler  
  
Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın. Aşağıdaki örnekte yerine kullanmayacağınızı unutmayın `var` `string[]` .  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13a":::

Açık örnek oluşturma kullanıyorsanız, kullanabilirsiniz `var` .

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13b":::

Bir dizi boyutu belirtirseniz, öğeleri birer birer başlatmalısınız.
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13c":::
  
### <a name="delegates"></a>Temsilciler  
  
Temsilci türlerini tanımlamak yerine [ `Func<>` ve `Action<>` ](../../../standard/delegates-lambdas.md) kullanın. Bir sınıfında, temsilci yöntemini tanımlayın.  

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14a":::

Veya temsilcisi tarafından tanımlanan imzayı kullanarak yöntemi çağırın `Func<>` `Action<>` .

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15a":::

Bir temsilci türünün örneklerini oluşturursanız, kısa sözdizimini kullanın. Bir sınıfında, temsilci türünü ve eşleşen imzaya sahip bir yöntemi tanımlayın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14b":::

Temsilci türünün bir örneğini oluşturun ve çağırın. Aşağıdaki bildirimde, sıkıştırılmış sözdizimi gösterilmektedir.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15b":::

Aşağıdaki bildirim tam sözdizimini kullanır.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15c":::

### <a name="try-catch-and-using-statements-in-exception-handling"></a>`try`-`catch` ve `using` özel durum işlemede deyimleri  
  
- Çoğu özel durum işleme için [try-catch](../../language-reference/keywords/try-catch.md) ifadesini kullanın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet16":::

- C# [using ifadesini](../../language-reference/keywords/using-statement.md)kullanarak kodunuzu kolaylaştırın. Yalnızca bloktaki kodun yöntemine yönelik bir çağrı olduğu bir [try-finally](../../language-reference/keywords/try-finally.md) deyiminiz varsa `finally` <xref:System.IDisposable.Dispose%2A> , `using` bunun yerine bir ifade kullanın.

  Aşağıdaki örnekte, `try` - `finally` ifade yalnızca `Dispose` `finally` bloğunda çağırır.
  
   :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17a":::

  Deyimle aynı şeyi yapabilirsiniz `using` .

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17b":::

  C# 8 ve sonraki sürümlerinde, küme ayraçları gerektirmeyen yeni [ `using` sözdizimini](../../language-reference/keywords/using-statement.md) kullanın:

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17c":::

### <a name="-and--operators"></a>`&&` ve `||` işleçleri  
  
Özel durumların önüne geçmek ve gereksiz karşılaştırmaları atlayarak performansı artırmak için, [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) [`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) Aşağıdaki örnekte gösterildiği gibi karşılaştırmaları gerçekleştirirken yerine kullanın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet18":::

Bölen 0 ise, deyimdeki ikinci yan tümce `if` bir çalışma zamanı hatasına neden olur. Ancak ilk ifade false olduğunda && işleci kısa devredir. Yani, ikinci ifadeyi değerlendirmez. & işleci her ikisini de değerlendirir ve 0 olduğunda bir çalışma zamanı hatasına neden olur `divisor` .
  
### <a name="new-operator"></a>`new` işlecinde  
  
- Aşağıdaki bildirimlerde gösterildiği gibi, nesne örneklemesinin kısa biçimlerinden birini kullanın. İkinci örnekte, C# 9 ' dan başlayarak kullanılabilir olan sözdizimi gösterilmektedir.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet19":::
  
  ```csharp
  ExampleClass instance2 = new();
  ```
  
  Önceki bildirimler aşağıdaki bildirime eşdeğerdir.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet20":::

- Aşağıdaki örnekte gösterildiği gibi, nesne oluşturma işlemini basitleştirmek için nesne başlatıcıları kullanın.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21a":::

  Aşağıdaki örnek, önceki örnekle aynı özellikleri ayarlar, ancak başlatıcıları kullanmaz.
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21b":::

### <a name="event-handling"></a>Olay işleme  
  
Daha sonra kaldırmanız gerekmeyen bir olay işleyicisi tanımlıyorsanız bir lambda ifadesi kullanın.  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet22":::

Lambda ifadesi aşağıdaki geleneksel tanımı kısaltır.

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet23":::

### <a name="static-members"></a>Statik üyeler  
  
[Statik](../../language-reference/keywords/static.md) üyeleri, sınıf adı: *ClassName. staticmember*' i kullanarak çağırın. Bu uygulama, statik erişim Temizleme yaparak kodu daha okunabilir hale getirir.  Türetilmiş bir sınıf adına sahip bir temel sınıfta tanımlanan statik bir üyeyi niteleme.  Kod derlense de, kod okunurluğu yanıltıcı olur ve türetilmiş sınıfa aynı ada sahip bir statik üye eklerseniz kod daha sonra bozulabilir.  
  
### <a name="linq-queries"></a>LINQ sorguları  
  
- Sorgu değişkenleri için anlamlı adlar kullanın. Aşağıdaki örnek `seattleCustomers` Seattle 'da bulunan müşteriler için kullanır.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- Anonim türlerin özellik adlarının, Pascal büyük küçük harf kullanarak doğru şekilde büyük harfli olduğundan emin olmak için diğer adları kullanın.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet26":::

- Sonuç içindeki Özellik adları belirsiz olduğunda özellikleri yeniden adlandırın. Örneğin, sorgunuz bir müşteri adı ve bir dağıtıcı KIMLIĞI döndürürse, ve sonuç olarak bırakmak yerine, `Name` `ID` `Name` bir müşterinin adı olduğunu ve bır dağıtıcının kimliğini açıklığa kavuşturacak şekilde yeniden adlandırın `ID` .  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet27":::

- Sorgu değişkenleri ve Aralık değişkenleri bildiriminde örtük yazma kullanın.  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- Önceki örneklerde gösterildiği gibi, [from](../../language-reference/keywords/from-clause.md) yan tümcesinin altındaki sorgu yan tümcelerini hizalayın.  

- Daha sonra sorgu yan tümcelerinin azaltılmış ve filtrelenmiş veri kümesi üzerinde çalışmasını sağlamak için diğer sorgu yan tümcelerinden önce [WHERE](../../language-reference/keywords/where-clause.md) yan tümceleri kullanın.  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet29":::

- `from`İç koleksiyonlara erişmek için [JOIN](../../language-reference/keywords/join-clause.md) yan tümcesi yerine birden çok yan tümce kullanın. Örneğin, bir `Student` nesne koleksiyonu her biri bir test puanları koleksiyonu içerebilir. Aşağıdaki sorgu yürütüldüğünde, puanı alan öğrencinin son adıyla birlikte 90 ' ten fazla olan her puanı döndürür.  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet30":::

## <a name="security"></a>Güvenlik  

[Güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md)bölümündeki yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET çalışma zamanı kodlama yönergeleri](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
- [Visual Basic Kodlama Kuralları](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Güvenli Kodlama Yönergeleri](../../../standard/security/secure-coding-guidelines.md)
