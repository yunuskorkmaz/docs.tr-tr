---
title: C#Kodlama kuralları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 598f0e75a96a43162d0c626d00320effb418c7fd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241437"
---
# <a name="c-coding-conventions-c-programming-guide"></a>C# Kodlama Kuralları (C# Programlama Kılavuzu)
 Kodlama kuralları aşağıdaki amaçlara hizmet eder:  
  
-   Böylece okuyucular düzene değil içeriğe göre koda tutarlı bir görünüm oluştururlar.  
  
-   Bunlar, okuyucular kodunuzu daha hızlı bir şekilde önceki deneyime dayanan varsayımlar yaparak anlamanız etkinleştirin.  
  
-   Bunlar, kopyalama, değiştirme ve kodun bakımını kolaylaştırır.  
  
-   Bunlar, C# en iyi uygulamaları gösterir.  

 Bu konudaki yönergeleri, örnekler ve belgeler geliştirmek için Microsoft tarafından kullanılır.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları  
  
-   Dahil etmezseniz kısa örneklerde [yönergeleri kullanarak](../../../csharp/language-reference/keywords/using-directive.md), ad alanı nitelikleri kullanın. Bir ad alanı, bir projedeki varsayılan olarak içeri aktarılır biliyorsanız, bu ad alanı adlarından tam olarak nitelemek gerekmez. Aşağıdaki örnekte gösterildiği gibi tek bir satır için çok uzun olmaları durumunda tam adları nokta (.) sonra bozuk olabilir.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   Diğer yönergelerine uygun olacak şekilde Visual Studio Tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını değiştirmeniz gerekmez.  
  
## <a name="layout-conventions"></a>Düzeni Kuralları  
 İyi Düzen biçimlendirme, kod yapısını vurgulamak ve kodun okunmasını kolaylaştırmak için kullanır. Microsoft örnekleri ve örnek için aşağıdaki kurallara uygun:  
  
-   Varsayılan Kod Düzenleyicisi ayarları (Akıllı girintileme dört karakterlik girintileri, sekmeleri boşluk olarak kaydedilen) kullanın. Daha fazla bilgi için [seçenekler, metin düzenleyici, C++, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Her satırda yalnızca bir deyim yazın.  
  
-   Her satırda yalnızca bir bildirim yazın.  
  
-   Bir sekme durağı (dört alanları), devamlılık satırlarını otomatik olarak girinti değil, bunları girinti.  
  
-   Yöntem tanımlarını ve özellik tanımları arasına en az bir boş satır ekleyin.  
  
-   Yan tümceleri bir ifadede görünür, aşağıdaki kodda gösterildiği gibi hale getirmek için ayraç kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Yorum Oluşturma Kuralları  
  
-   Bir kod satırının sonunda değil ayrı bir satırda açıklama yerleştirin.  
  
-   Büyük harfle yorum metni başlatın.  
  
-   Yorum metnini noktayla sonlandırın.  
  
-   Açıklama sınırlayıcısı arasında bir boşluk (/ /) ve aşağıdaki örnekte gösterildiği gibi açıklama metni.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   Biçimlendirilmiş yıldız açıklamaları etrafında bloklarını oluşturmayın.  
  
## <a name="language-guidelines"></a>Dil Kuralları  
 Aşağıdaki bölümlerde, C# ekip kod örnekleri ve örnek hazırlamak için aşağıdaki yöntemleri açıklar.  
  
### <a name="string-data-type"></a>Dize Veri Türü  
  
-   Kullanım [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) kısa dizeler, aşağıdaki kodda gösterildiği gibi birleştirmek için.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   Döngülere diziler, özellikle büyük miktarlarda metini çalışırken eklemek için kullanmak bir <xref:System.Text.StringBuilder> nesne.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  
  
-   Kullanım [örtülü yazma](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) değişkeninin türünü atama veya kesin türü önemli olmadığı durumlarda sağından belirgin olduğunda yerel değişkenleri.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   Kullanmayın [var](../../../csharp/language-reference/keywords/var.md) türü olmadığında ataması sağ taraftan görünür.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   Değişken türünü belirtmek için değişken adını kullanmayın. Doğru olmayabilir.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   Kullanmaktan kaçının `var` yerine [dinamik](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   Örtülü yazma Döngü değişkeninin içinde türünü belirlemek için kullanın [için](../../../csharp/language-reference/keywords/for.md) ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md) döngüleri.  
  
     Aşağıdaki örnek örtük yazarak kullanan bir `for` deyimi.  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     Aşağıdaki örnek örtük yazarak kullanan bir `foreach` deyimi.  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>İmzasız Veri Türü  
  
-   Genel olarak, kullanın `int` imzasız türler yerine. Kullanımını `int` C# yaygın bir durumdur ve diğer kitaplıklarla birlikte kullandığınızda etkileşim kolaydır `int`.  
  
### <a name="arrays"></a>Diziler  
  
-   Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Temsilciler  
  
-   Bir temsilci türünün örneğini oluşturmak için kısa sözdizimi kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma  
  
-   Kullanım bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) çoğu özel durum işleme için bildirimi.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   C# kullanarak kodunuzu basitleştirerek [using deyimi](../../../csharp/language-reference/keywords/using-statement.md). Varsa bir [try-finally](../../../csharp/language-reference/keywords/try-finally.md) deyimi, yalnızca kod `finally` blok çağrısı ise <xref:System.IDisposable.Dispose%2A> yöntemini kullanmak bir `using` deyimi yerine.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & ve &#124; &#124; işleçleri  
  
-   Özel durumlar önlemek ve gereksiz karşılaştırmalar atlayarak performansı artırmak için kullandığınız [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) yerine [ & ](../../../csharp/language-reference/operators/and-operator.md) ve [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)yerine [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) gerçekleştirirken karşılaştırmalar, aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Yeni İşleç  
  
-   Nesne örneklemesini kısa biçiminde örtülü yazma için aşağıdaki bildirimde gösterildiği gibi kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Önceki satıra aşağıdaki bildirime eşdeğerdir.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   Nesne oluşturma işlemini basitleştirmek için nesne başlatıcıları kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Olay İşleme  
  
-   Daha sonra kaldırmanız gerekmez bir olay işleyicisi tanımlıyorsanız, bir lambda ifadesini kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statik Üyeler  
  
-   Çağrı [statik](../../../csharp/language-reference/keywords/static.md) üyeleri sınıf adını kullanarak: *ClassName.StaticMember*. Bu yöntem kod daha okunabilir Temizle statik erişim sağlayarak yapar.  Bir temel sınıfta türetilmiş bir sınıfın adıyla tanımlanan statik bir üye için uygun değildir.  Bu kod derlenir, kodun okunabilirliğini yanıltıcı ve türetilmiş sınıf için aynı ada sahip bir statik üye ekleme kodu gelecekte bozabilir.  
  
### <a name="linq-queries"></a>LINQ Sorguları  
  
-   Sorgu değişkenleri için anlamlı adlar kullanın. Aşağıdaki örnekte `seattleCustomers` müşteriler Seattle'dadır.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Anonim türlerinin özellik adlarının doğru Pascal kullanarak emin olmak için diğer adları kullanın. büyük/küçük harf.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   Sonuçtaki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın. Örneğin, sorgunuz bir müşteri adı ve olarak bırakmak yerine bir dağıtıcı kimliği döndürür `Name` ve `ID` sonucunda açıklamak için yeniden adlandırma `Name` bir müşteri adı ve `ID` bir dağıtıcıyı kimliğidir.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   Sorgu değişkenleri ve aralık değişkenleri bildiriminde örtülü yazma kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Altında sorgu yan tümcelerini hizalayın [gelen](../../../csharp/language-reference/keywords/from-clause.md) yan tümcesi, önceki örneklerde gösterildiği gibi.  
  
-   Kullanım [burada](../../../csharp/language-reference/keywords/where-clause.md) yan tümceleri önce sonraki sorgu yan tümcelerinin azaltılmış üzerinde çalışmasını sağlamak için diğer sorgu yan tümcelerinin filtrelenmiş veri kümesi.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   Birden çok kullanın `from` yan tümceleri yerine bir [birleştirme](../../../csharp/language-reference/keywords/join-clause.md) yan tümcesi iç koleksiyonlara erişmek için. Örneğin, bir koleksiyonunu `Student` nesneleri her içerebilir test puanlarını koleksiyonu. Aşağıdaki sorgu yürütüldüğünde, üzerinde birlikte puana Öğrenci Soyadı 90 her bir puan döndürür.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Güvenlik  
 Bölümündeki yönergeleri uygulayın [güvenli kodlama kılavuzları](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Basic kodlama kuralları](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
- [Güvenli Kodlama Yönergeleri](../../../standard/security/secure-coding-guidelines.md)
