---
title: C# Kodlama Kuralları - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399737"
---
# <a name="c-coding-conventions-c-programming-guide"></a>C# Kodlama Kuralları (C# Programlama Kılavuzu)

Kodlama kuralları aşağıdaki amaçlara hizmet eder:  
  
- Okuyucuların düzene değil içeriğe odaklanabilmesi için koda tutarlı bir görünüm oluştururlar.  
  
- Okuyucuların önceki deneyimlere dayalı varsayımlar yaparak kodu daha hızlı anlamalarını sağlarlar.  
  
- Kodun kopyalanması, değiştirilmesi ve korunmasını kolaylaştırır.  
  
- C# en iyi uygulamaları gösteriyorlar.  

Bu makaledeki yönergeler Microsoft tarafından örnekler ve belgeler geliştirmek için kullanılır.  
  
## <a name="naming-conventions"></a>Adlandırma Kuralları  
  
- [Yönergeleri kullanmayı](../../language-reference/keywords/using-directive.md)içermeyen kısa örneklerde, ad alanı niteliklerini kullanın. Bir projede varsayılan olarak bir ad alanının alındığını biliyorsanız, bu ad alanından adları tam olarak nitelemeniz gerekmez. Aşağıdaki örnekte gösterildiği gibi, tek bir satır için çok uzunsa, nitelikli adlar bir nokta (.) sonra kırılabilir.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- Visual Studio tasarımcı araçlarını kullanarak oluşturulan nesnelerin adlarını diğer yönergelere uygun hale getirmek için değiştirmeniz gerekmez.  
  
## <a name="layout-conventions"></a>Düzeni Kuralları  

İyi düzen, kodunuzu vurgulamak ve kodun okunmasını kolaylaştırmak için biçimlendirmeyi kullanır. Microsoft örnekleri ve örnekleri aşağıdaki kurallara uygundur:  
  
- Varsayılan Kod Düzenleyicisi ayarlarını (akıllı girinti, dört karakterli girintiler, boşluk olarak kaydedilen sekmeler) kullanın. Daha fazla bilgi için [seçenekler, Metin Düzenleyicisi, C#, Biçimlendirme'ye](/visualstudio/ide/reference/options-text-editor-csharp-formatting)bakın.  
  
- Satır başına yalnızca bir deyim yazın.  
  
- Satır başına yalnızca bir bildirim yazın.  
  
- Devam satırları otomatik olarak girintisi değilse, bir sekme durağı (dört boşluk) girintisi girintisi.  
  
- Yöntem tanımları ve özellik tanımları arasında en az bir boş satır ekleyin.  
  
- Aşağıdaki kodda gösterildiği gibi, bir ifadedeki yan tümceleri görünür hale getirmek için parantezleri kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Yorum Oluşturma Kuralları  
  
- Yorumu kod satırının sonuna değil, ayrı bir satıra yerleştirin.  
  
- Açıklama metnini büyük harfle başlayın.  
  
- Açıklama metnini bir dönemle sonla.  
  
- Aşağıdaki örnekte gösterildiği gibi, açıklama delimiter (//) ile açıklama metni arasına bir boşluk ekleyin.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- Yorumların etrafında biçimlendirilmiş yıldız taşları oluşturmayın.  
  
## <a name="language-guidelines"></a>Dil Kuralları  

Aşağıdaki bölümlerde C# ekibinin kod örnekleri ve örnekleri hazırlamak için izlediği uygulamalar açıklanmaktadır.  
  
### <a name="string-data-type"></a>Dize Veri Türü  
  
- Aşağıdaki kodda gösterildiği gibi kısa dizeleri birleştirmek için [dize enterpolasyonunu](../../language-reference/tokens/interpolated.md) kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- Özellikle büyük miktarda metinle çalışıyorsanız, döngüler halinde dizeleri eklemek için bir <xref:System.Text.StringBuilder> nesne kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  
  
- Değişkenin türü atamanın sağ tarafından belirgin olduğunda veya kesin tür önemli olmadığında yerel değişkenler için [örtük yazma](../classes-and-structs/implicitly-typed-local-variables.md) kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- Tür atamanın sağ tarafından belirgin olmadığında [var](../../language-reference/keywords/var.md) kullanmayın.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- Değişkenin türünü belirtmek için değişken adına güvenmeyin. Doğru olmayabilir.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- [Dinamik](../../language-reference/builtin-types/reference-types.md)yerine `var` kullanmaktan kaçının.  
  
- Döngüler için döngü değişkeninin türünü belirlemek [için](../../language-reference/keywords/for.md) örtük yazıyı kullanın.  
  
     Aşağıdaki örnekte bir `for` deyimde örtük yazma kullanılır.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- [Foreach](../../language-reference/keywords/foreach-in.md) döngülerde döngü değişkeninin türünü belirlemek için örtük yazma kullanmayın.

     Aşağıdaki örnekte bir `foreach` deyimde açık yazım kullanılır.

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > Yinelenebilir koleksiyonun bir öğesini yanlışlıkla değiştirmemeye dikkat edin. Örneğin, sorgunun yürütülmesini <xref:System.Linq.IQueryable?displayProperty=nameWithType> değiştiren <xref:System.Collections.IEnumerable?displayProperty=nameWithType> bir `foreach` deyimde geçiş yapmak kolaydır.

### <a name="unsigned-data-type"></a>İmzasız Veri Türü  
  
Genel olarak, `int` imzasız türler yerine kullanın. Kullanımı `int` C# boyunca yaygındır ve kullandığınızda `int`diğer kitaplıklarla etkileşim kurmak daha kolaydır.  
  
### <a name="arrays"></a>Diziler  
  
Bildirim satırındaki dizileri baş harfe aldığınızda kısa sözdizimini kullanın.  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Temsilciler  
  
Temsilci türü örnekleri oluşturmak için kısa sözdizimini kullanın.  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma  
  
- Çoğu özel durum işleme için [try-catch](../../language-reference/keywords/try-catch.md) deyimi kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- [C# deyimini kullanarak](../../language-reference/keywords/using-statement.md)kodunuzu basitleştirin. Bloktaki tek kodun <xref:System.IDisposable.Dispose%2A> yönteme çağrı olduğu bir `using` [try-finally](../../language-reference/keywords/try-finally.md) deyiminiz varsa, bunun yerine bir deyim kullanın. `finally`  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>&& ve &#124;&#124; Operatörleri  
  
İstisnaları önlemek ve gereksiz karşılaştırmaları atlayarak [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) performansı [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) artırmak için, aşağıdaki örnekte gösterildiği gibi karşılaştırmalar yaparken [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) yerine yerine kullanın ve [&#124;&#124;.](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Yeni İşleç  
  
- Aşağıdaki bildirimde gösterildiği gibi, örtük yazım la nesne anlık kısa formu kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Önceki satır aşağıdaki bildirime eşdeğerdir.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- Nesne oluşturmayı kolaylaştırmak için nesne baş harflerini kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Olay İşleme  
  
Daha sonra kaldırmanız gerekmeyen bir olay işleyicisi tanımlıyorsanız, lambda ifadesi kullanın.  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statik Üyeler  
  
Sınıf adını kullanarak [statik](../../language-reference/keywords/static.md) üyeleri arayın: *ClassName.StaticMember*. Bu uygulama, statik erişimi net hale getirerek kodu daha okunabilir hale getirir.  Taban sınıfta tanımlanan statik bir üyeyi türetilmiş sınıf adıyla nitelemayın.  Bu kod derlenirken, kod okunabilirliği yanıltıcıdır ve türemiş sınıfa aynı ada sahip statik bir üye eklerseniz kod gelecekte kırılabilir.  
  
### <a name="linq-queries"></a>LINQ Sorguları  
  
- Sorgu değişkenleri için anlamlı adlar kullanın. Aşağıdaki örnek, `seattleCustomers` Seattle'da bulunan müşteriler için kullanır.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Pascal kasasını kullanarak anonim türdeki özellik adlarının doğru şekilde büyük harfle yazdığından emin olmak için takma adlar kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- Sonuç taki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın. Örneğin, sorgunuz bir müşteri adı ve bir distribütör kimliği `Name` döndürürse, sonuç olarak ve `ID` sonuç olarak bırakmak `ID` yerine, müşterinin adı olduğunu ve bir distribütörün kimliği olduğunu `Name` açıklığa kavuşturmak için bunları yeniden adlandırın.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- Sorgu değişkenleri ve aralık değişkenleri bildiriminde örtük yazıyı kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Önceki örneklerde gösterildiği [gibi, sorgu](../../language-reference/keywords/from-clause.md) yan tümcelerini from yan tümcesinin altında hizala.  
  
- Daha sonraki sorgu yan tümcelerinin azaltılmış, filtre uygulanmış veri kümesinde çalışmasını sağlamak için diğer sorgu yan tümcelerinden önce [nerede](../../language-reference/keywords/where-clause.md) yan tümcelerini kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- İç `from` koleksiyonlara erişmek için [birleştirme](../../language-reference/keywords/join-clause.md) yan tümcesi yerine birden çok yan tümce kullanın. Örneğin, nesnelerin bir `Student` koleksiyonu her test puanları bir koleksiyon içerebilir. Aşağıdaki sorgu yürütüldüğünde, 90'ın üzerindeki her puanı, puanı alan öğrencinin soyadıyla birlikte döndürür.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Güvenlik  

Güvenli Kodlama [Yönergeleri'ndeki](../../../standard/security/secure-coding-guidelines.md)yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Kodlama Kuralları](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Güvenli Kodlama Yönergeleri](../../../standard/security/secure-coding-guidelines.md)
