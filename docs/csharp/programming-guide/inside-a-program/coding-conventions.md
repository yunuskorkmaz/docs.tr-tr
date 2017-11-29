---
title: "C# Kodlama Kuralları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84ddc2b3cebb6bad95f5076889de11f12624b4de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="c-coding-conventions-c-programming-guide"></a>C# Kodlama Kuralları (C# Programlama Kılavuzu)
[C# dil belirtimi](http://go.microsoft.com/fwlink/?LinkId=199552) kodlama standart tanımlamıyor. Ancak, bu konudaki yönergeleri, örnekler ve belgeler geliştirmek için Microsoft tarafından kullanılır.  
  
 Kodlama kuralları aşağıdaki amaca hizmet eder:  
  
-   Okuyucular içeriğine değil düzeni odaklanabilmeniz bunlar kodu tutarlı bir görünüm oluşturur.  
  
-   Bunlar, önceki deneyimleri temel varsayımları yaparak kodu daha hızlı bir şekilde anlaşılması okuyucular etkinleştirin.  
  
-   Bunlar, kopyalama, değiştirme ve kod bakımı kolaylaştırır.  
  
-   Bunlar, C# en iyi uygulamaları gösterir.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları  
  
-   İçermeyen kısa örneklerde [yönergeleri kullanarak](../../../csharp/language-reference/keywords/using-directive.md), ad alanı nitelikleri kullanın. Bir ad alanı varsayılan projede alınır biliyorsanız, bu ad alanı adlarından tam olarak nitelemek gerekmez. Aşağıdaki örnekte gösterildiği gibi tek bir satır için çok uzun olmaları durumunda nitelenmiş adlar bir nokta (.) sonra bozuk olabilir.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   Bunları diğer yönergelerine uygun hale getirmek için Visual Studio Tasarımcı araçları kullanılarak oluşturulan nesnelerin adlarını değiştirmek zorunda değildir.  
  
## <a name="layout-conventions"></a>Düzeni Kuralları  
 Kodunuzu yapısını vurgulamak ve kod okunmasını kolaylaştırmak için iyi düzenini biçimlendirme kullanır. Microsoft örnekleri ve örnekler için aşağıdaki kurallara uygun:  
  
-   Varsayılan kod düzenleyicisinde ayarları (Akıllı Girintileme, dört karakter girintileri, alanları olarak kaydedilen sekmeleri) kullanın. Daha fazla bilgi için bkz: [seçenekler, metin düzenleyici, C++, biçimlendirme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Satır başına yalnızca bir deyim yazma.  
  
-   Satır başına yalnızca bir bildirimini yazma.  
  
-   Devamlılık satırlarının otomatik olarak girinti değil, bunları bir sekme durağı (dört alanları) girinti.  
  
-   Yöntem tanımlarını ve özellik tanımları arasında en az bir boş satır ekleyin.  
  
-   Yan tümceleri bir ifadede görünür, aşağıdaki kodda gösterildiği gibi yapma ayraç kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Yorum Oluşturma Kuralları  
  
-   Kod satırının sonunda değil ayrı bir satırda açıklama yerleştirin.  
  
-   Açıklama metni büyük harfe ile başlar.  
  
-   Açıklama metni noktayla bitmelidir.  
  
-   Açıklama sınırlayıcısı arasında bir boşluk (/ /) ve aşağıdaki örnekte gösterildiği gibi açıklama metni.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   Yorumlar geçici yıldızlar biçimlendirilmiş bloklarını oluşturmayın.  
  
## <a name="language-guidelines"></a>Dil Kuralları  
 Aşağıdaki bölümlerde C# takım kod örnekleri ve örnekleri hazırlamak için aşağıdaki yöntemleri açıklar.  
  
### <a name="string-data-type"></a>Dize Veri Türü  
  
-   Kullanım `+` aşağıdaki kodda gösterildiği gibi kısa dizeyi birleştirmek için işleci.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   Özellikle büyük miktarlarda metin ile çalışırken döngüler, dizelerde eklemek için kullanın bir <xref:System.Text.StringBuilder> nesnesi.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  
  
-   Kullanım [örtülü yazma](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) değişkeninin türü sağından atama veya kesin türü önemli olmadığında açık olduğunda, yerel değişkenleri.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   Kullanmayın [var](../../../csharp/language-reference/keywords/var.md) türü olmadığında atama sağ tarafında görünür.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   Değişken türünü belirtmek için değişken adını kullanmayın. Doğru olmayabilir.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   Kullanmaktan kaçının `var` yerine [dinamik](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   Örtük yazarak döngü değişken türünü belirlemek için kullanın [için](../../../csharp/language-reference/keywords/for.md) ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md) döngüler.  
  
     Aşağıdaki örnek, örtük yazarak kullanır bir `for` deyimi.  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     Aşağıdaki örnek, örtük yazarak kullanır bir `foreach` deyimi.  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>İmzasız Veri Türü  
  
-   Genel olarak, kullanın `int` imzasız türler yerine. Kullanımını `int` C# yaygın bir durumdur ve diğer kitaplıklarla birlikte kullandığınızda etkileşim daha kolaydır `int`.  
  
### <a name="arrays"></a>Diziler  
  
-   Diziler bildirimi satırındaki başlattığınızda kısa sözdizimini kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Temsilciler  
  
-   Bir temsilci türü örnekleri oluşturmak için kısa sözdizimini kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>try-catch ve Özel Durum İşleme bölümünde Deyimleri kullanma  
  
-   Kullanım bir [try-catch](../../../csharp/language-reference/keywords/try-catch.md) çoğu özel durum işleme için bildirimi.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   C# kullanarak kodunuzu basitleştiren [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md). Varsa bir [try-finally](../../../csharp/language-reference/keywords/try-finally.md) hangi deyiminde yalnızca kodda `finally` blok çağrıdır <xref:System.IDisposable.Dispose%2A> yöntemi, kullanım bir `using` deyimi yerine.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & ve &#124; &#124; İşleçler  
  
-   Özel durumlar önlemek ve gereksiz karşılaştırmaları atlayarak performansı artırmak için kullanmak [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) yerine [ & ](../../../csharp/language-reference/operators/and-operator.md) ve [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) yerine [&#124;](../../../csharp/language-reference/operators/or-operator.md) gerçekleştirdiğinizde karşılaştırmaları, aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Yeni İşleç  
  
-   Nesne oluşturmada kısa biçiminde örtülü yazma ile aşağıdaki bildiriminde gösterildiği gibi kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Önceki satıra aşağıdaki bildirimine eşdeğerdir.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   Nesne başlatıcıları nesne oluşturma işlemini basitleştirmek için kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Olay İşleme  
  
-   Daha sonra kaldırmanız gerekmez bir olay işleyicisi tanımlıyorsanız, lambda ifadesi kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statik Üyeler  
  
-   Çağrı [statik](../../../csharp/language-reference/keywords/static.md) sınıf adını kullanarak üyeleri: *ClassName.StaticMember*. Bu yöntem, temizleyin statik erişim sağlayarak kodunu daha okunabilir yapar.  Türetilmiş bir sınıf adı ile temel bir sınıf içinde tanımlanan statik bir üyenin uygun değil.  Bu kodu derlenir kodun okunabilirliğini yanıltıcı ve türetilmiş sınıf aynı ada sahip statik bir üyenin eklerseniz, kodu gelecekte kesilebilir.  
  
### <a name="linq-queries"></a>LINQ Sorguları  
  
-   Sorgu değişkenleri için anlamlı adlarını kullanın. Aşağıdaki örnek kullanır `seattleCustomers` Seattle'da bulunan müşteriler için.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Anonim türdeki özellik adları düzgün, Pascal kullanarak olduğundan emin emin olmak için diğer adlar kullanın büyük/küçük harf.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   Özellik adlarının sonuç belirsiz kullanırken özellikleri yeniden adlandırın. Sorgunuz bir müşteri adı ve bunları olarak bırakarak yerine bir dağıtıcı kimliği döndürürse, örneğin, `Name` ve `ID` sonucunda açıklamak için yeniden adlandırma `Name` bir müşteri adıdır ve `ID` dağıtıcı kimliğidir.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   Örtük sorgu değişkenleri ve aralık değişkeni bildiriminde yazarak kullanın.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Sorgu yan tümceleri altında Hizala [gelen](../../../csharp/language-reference/keywords/from-clause.md) önceki örneklerde gösterildiği gibi yan tümcesi.  
  
-   Kullanım [burada](../../../csharp/language-reference/keywords/where-clause.md) yan tümceleri sonraki sorgu yan tümceleri azaltılmış üzerinde çalışmasını sağlamak için diğer sorgu yan tümceleri önce filtrelenmiş veri kümesi.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   Birden çok kullanın `from` yan tümceleri yerine bir [birleştirme](../../../csharp/language-reference/keywords/join-clause.md) iç koleksiyonları erişmek için yan tümcesi. Örneğin, bir koleksiyonu `Student` nesneleri her içerebilir test puanları koleksiyonu. Aşağıdaki sorgu çalıştırıldığında, Soyadı puanı alınan Öğrenci birlikte üzerinde 90 her puan döndürür.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Güvenlik  
 Alan yönergeleri izleyin [güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic kodlama kuralları](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [Güvenli kodlama yönergeleri](../../../standard/security/secure-coding-guidelines.md)
