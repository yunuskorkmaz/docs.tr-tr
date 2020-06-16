---
title: .NET Framework'te Tür Dönüştürme
description: .NET ' te tür dönüştürmesi hakkında bilgi edinmek için, eski türün değerine denk gelen yeni bir tür değeri oluşturur, ancak özgün kimliğini saklayamayabilir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- widening conversions
- explicit conversions
- narrowing conversions
- type conversion, about type conversion
- type conversion
- converting types
- narrowing coercion
- Explicit operator
- IConvertible interface
- base types, converting
- op_Implicit method
- widening coercion
- op_Explicit method
- Convert class
- implicit conversions
- Implicit operator
- data types [.NET Framework], converting
ms.assetid: ba36154f-064c-47d3-9f05-72f93a7ca96d
ms.openlocfilehash: 11345081610459dbf053d846aa04369301010732
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769229"
---
# <a name="type-conversion-in-the-net-framework"></a>.NET Framework'te Tür Dönüştürme
Her değerin, değere ayrılan alan miktarı, sahip olduğu olası değer aralığı ve kullanılabilir olduğu Üyeler gibi öznitelikleri tanımlayan ilişkili bir türü vardır. Birçok değer, tek bir türden fazlası olarak ifade edilebilir. Örneğin, 4 değeri bir tamsayı olarak veya bir kayan nokta değeri olarak ifade edilebilir. Tür dönüştürme, eski bir türün değerine eşit olan, yeni türde bir değer oluşturur, fakat özgün nesnenin kimliğini (veya tam değerini) koruması gerekmez.  
  
 .NET Framework, aşağıdaki dönüştürmeleri otomatik olarak destekler:  
  
- Türetilmiş bir sınıftan temel sınıfa dönüştürme. Bu, örneğin, herhangi bir sınıf veya yapının bir örneğinin örneğe dönüştürülebileceği anlamına gelir <xref:System.Object> .  Bu dönüştürme bir atama veya dönüştürme işleci gerektirmez.  
  
- Temel sınıftan özgün türetilmiş sınıfa geri dönüştürme. C# dilinde, bu dönüştürme bir atama işleci gerektirir. Visual Basic, açık ise işleci gerektirir `CType` `Option Strict` .  
  
- Arabirimi uygulayan bir türden, bu arabirimi temsil eden bir arabirim nesnesine dönüştürme. Bu dönüştürme bir atama veya dönüştürme işleci gerektirmez.  
  
- Arabirim nesnesinden bu arabirimi uygulayan özgün türe dönüştürme.  C# dilinde, bu dönüştürme bir atama işleci gerektirir. Visual Basic, açık ise işleci gerektirir `CType` `Option Strict` .  
  
 Bu otomatik Dönüştürmelere ek olarak .NET Framework, özel tür dönüştürmeyi destekleyen çeşitli özellikler sağlar. Bunlar aşağıdakileri içerir:  
  
- `Implicit`Türler arasında kullanılabilir genişletme dönüştürmelerini tanımlayan işleç. Daha fazla bilgi için [örtük operatör ile örtük dönüştürme](#implicit-conversion-with-the-implicit-operator) bölümüne bakın.  
  
- `Explicit`Türler arasında kullanılabilir daraltma dönüştürmelerini tanımlayan işleç. Daha fazla bilgi için [Açık operatör Ile açık dönüştürme](#explicit-conversion-with-the-explicit-operator) bölümüne bakın.  
  
- <xref:System.IConvertible>Temel .NET Framework veri türlerinin her birine dönüşümler tanımlayan arabirim. Daha fazla bilgi için, bkz. [ıverli arabirim](#the-iconvertible-interface) bölümü.  
  
- <xref:System.Convert>Arabirimindeki yöntemleri uygulayan bir yöntemler kümesi sağlayan sınıfı <xref:System.IConvertible> . Daha fazla bilgi için [Convert Class](#the-convert-class) bölümüne bakın.  
  
- <xref:System.ComponentModel.TypeConverter>Belirtilen bir türün başka bir türe dönüştürülmesini desteklemek için genişletilebilen bir temel sınıf olan sınıf. Daha fazla bilgi için [TypeConverter sınıfı](#the-typeconverter-class) bölümüne bakın.  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Örtülü İşleçle Örtülü Dönüştürme  
 Genişletme dönüştürmeleri, varolan bir türün değerinden, hedef türe göre daha kısıtlayıcı bir aralığı veya daha kısıtlayıcı bir üye listesi olan yeni bir değer oluşturmayı gerektirir. Genişletme dönüştürmeleri, (kesinlik kaybıyla sonuçlanabilir olsalar da) veri kaybıyla sonuçlanmaz. Veriler kaybedilemeyeceğinden, derleyiciler, açık bir dönüştürme yöntemi veya bir yayın işleci kullanılmadan, dönüştürmeyi örtülü olarak veya saydam olarak işleyebilir.  
  
> [!NOTE]
> Örtülü bir dönüştürme uygulayan kod bir dönüştürme yöntemi çağırabilir veya bir yayımlama işleci kullanabilir olsa da, örtülü dönüştürmeleri destekleyen derleyiciler tarafından kullanılmaları gerekmez.  
  
 Örneğin, türü örtük dönüştürmeleri,,,,,,, <xref:System.Decimal> <xref:System.Byte> <xref:System.Char> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.UInt16> <xref:System.UInt32> ve <xref:System.UInt64> değerlerinden destekler. Aşağıdaki örnek, bir değişkene değer atarken bu örtük dönüştürmelerin bazılarını göstermektedir <xref:System.Decimal> .  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Belirli bir dil derleyicisi özel işleçleri desteklerse, kendi özel türlerinizde de örtülü dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, `ByteWithSign` oturum açma ve büyüklük gösterimini kullanan adlı imzalı bir bayt veri türünün kısmi bir uygulamasını sağlar. Örtülü dönüştürme <xref:System.Byte> ve değerlere değerler destekler <xref:System.SByte> `ByteWithSign` .  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Daha sonra istemci kodu `ByteWithSign` <xref:System.Byte> <xref:System.SByte> , aşağıdaki örnekte gösterildiği gibi herhangi bir açık dönüştürme gerçekleştirmeden veya herhangi bir atama işlecini kullanmadan bir değişken bildirebilir ve bu değeri atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Açık İşleçli Açık Dönüştürme  
 Dönüştürmeleri daraltma, hedef türden daha geniş bir aralığa veya daha büyük bir üye listesine sahip olan varolan bir türün değerinden yeni bir değer oluşturulmasını gerektirir. Bir daraltma dönüşümü veri kaybıyla sonuçlanabildiğinden, derleyiciler genellikle dönüştürmenin bir dönüştürme yöntemine veya bir yayımlama işlecine yapılan bir çağrı yoluyla açık hale getirilmesini gerektirir. Yani, dönüştürmenin, geliştirici kodunda açıkça işlenmesi gerekir.  
  
> [!NOTE]
> Daraltma dönüştürmeleri için bir dönüştürme yöntemi veya atama işleci gerektirmesinin ana amacı, geliştiricinin veri kaybı olasılığını veya bir <xref:System.OverflowException> şekilde kod içinde işlenebilmesini sağlayacak şekilde haberdar hale getirme yöntemidir. Ancak, bazı derleyiciler bu gereksinimi ılımlı hale getirebilir. Örneğin, Visual Basic, `Option Strict` kapalıysa (varsayılan ayarı), Visual Basic derleyici, daraltma dönüşümlerini örtülü olarak gerçekleştirmeye çalışır.  
  
 Örneğin,, <xref:System.UInt32> <xref:System.Int64> ve <xref:System.UInt64> veri türleri, <xref:System.Int32> Aşağıdaki tabloda gösterildiği gibi, veri türünü aşan aralıklar vardır.  
  
|Tür|Int32 aralığıyla karşılaştırma|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>büyüktür ve küçüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType> (değerinden daha <xref:System.Int64.MinValue?displayProperty=nameWithType> büyük bir negatif aralığa sahiptir) <xref:System.Int32.MinValue?displayProperty=nameWithType> .|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>Şundan büyüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType> .|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>Şundan büyüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType> .|  
  
 Bu tür daraltma dönüşümlerini işlemek için .NET Framework, türlerin bir işleç tanımlamasına olanak tanır `Explicit` . Tek tek dil derleyicileri, bu işleci kendi söz dizimini kullanarak uygulayabilir ya da <xref:System.Convert> Dönüştürmeyi gerçekleştirmek için sınıfının bir üyesi çağrılabilir. (Sınıf hakkında daha fazla bilgi için <xref:System.Convert> Bu konunun ilerleyen kısımlarında bulunan [Convert sınıfı](#the-convert-class) bölümüne bakın.) Aşağıdaki örnek, bu potansiyel olarak Aralık dışı tamsayı değerlerinin değerlere açıkça dönüştürülmesini işlemek için dil özelliklerinin kullanımını gösterir <xref:System.Int32> .  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Açık dönüştürmeler farklı dillerde farklı sonuçlar üretebilir ve bu sonuçlar karşılık gelen yöntemin döndürdüğü değerden farklı olabilir <xref:System.Convert> . Örneğin, <xref:System.Double> 12,63251 değeri bir öğesine dönüştürülürse <xref:System.Int32> , hem Visual Basic yöntemi hem de `CInt` .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> yöntemi <xref:System.Double> 13 değerini döndürmek için ' i yuvarlar, ancak C# `(int)` işleci, <xref:System.Double> 12 değerini döndürmek için öğesini keser. Benzer şekilde, C# `(int)` Işleci Boolean-tamsayı dönüştürmeyi desteklemez, ancak Visual Basic `CInt` yöntemi değerini `true` -1 ' e dönüştürür. Diğer taraftan, <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> yöntemi değerini `true` 1 olarak dönüştürür.  
  
 Derleyicilerin çoğu, açık dönüştürmelerin denetlenen veya denetlenmeyen bir şekilde yapılmasına olanak tanır. Denetlenen bir dönüştürme gerçekleştirildiğinde, <xref:System.OverflowException> dönüştürülecek türün değeri hedef türü aralığının dışında olduğunda bir atılır. Aynı koşullarda denetlenmeyen bir dönüştürme yapıldığında, dönüştürme bir özel durum oluşturmayabilir, fakat davranış tam olarak tanımsız hale gelir ve sonuç olarak hatalı bir değer oluşabilir.  
  
> [!NOTE]
> C# ' de, denetlenen dönüşümler, `checked` anahtar sözcüğü bir atama işleciyle birlikte kullanılarak veya `/checked+` derleyici seçeneği belirtilerek gerçekleştirilebilir. Buna karşılık, denetlenmeyen dönüştürmeler, `unchecked` atama işleciyle birlikte anahtar sözcüğü kullanılarak veya `/checked-` derleyici seçeneği belirtilerek gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenmez. Visual Basic ' de, projenin **Gelişmiş derleyici ayarları** iletişim kutusundaki **tamsayı taşma denetimlerini kaldır** onay kutusu temizlenerek veya derleyici seçeneği belirtilerek, denetlenen dönüştürmeler gerçekleştirilebilir `/removeintchecks-` . Buna karşılık, denetlenmeyen dönüştürmeler, projenin **Gelişmiş derleyici ayarları** iletişim kutusunda **tamsayı taşma denetimlerini kaldır** onay kutusu seçilerek veya `/removeintchecks+` derleyici seçeneği belirtilerek gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenir.  
  
 Aşağıdaki C# örneği, `checked` `unchecked` bir öğesinin aralığının dışında bir değer değerine dönüştürüldüğünde davranıştaki farkı göstermek için ve anahtar sözcüklerini kullanır <xref:System.Byte> <xref:System.Byte> . İşaretlenen dönüştürme bir özel durum oluşturur, ancak Denetlenmemiş dönüştürme değişkenine atar <xref:System.Byte.MaxValue?displayProperty=nameWithType> <xref:System.Byte> .  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Belirli bir dil derleyicisi özel aşırı yüklü işleçleri desteklerse, kendi özel türlerinizde de açık dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, `ByteWithSign` oturum açma ve büyüklük gösterimini kullanan adlı imzalı bir bayt veri türünün kısmi bir uygulamasını sağlar. Açık dönüştürme <xref:System.Int32> ve <xref:System.UInt32> değerlere değerler destekler `ByteWithSign` .  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Daha sonra `ByteWithSign` <xref:System.Int32> <xref:System.UInt32> , aşağıdaki örnekte gösterildiği gibi, istemci kodu bir değişken bildirebilir ve atamalar bir atama işleci veya dönüştürme yöntemi içeriyorsa bu değeri atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>IConvertible Arabirimi  
 Herhangi bir türün ortak dil çalışma zamanı temel türüne dönüştürülmesini desteklemek için .NET Framework <xref:System.IConvertible> arabirimi sağlar. Uygulama türünün aşağıdakileri sağlaması gerekir:  
  
- Uygulama türünün değerini döndüren bir yöntem <xref:System.TypeCode> .  
  
- Uygulama türünü her ortak dil çalışma zamanı temel türüne (,,,, <xref:System.Boolean> vb <xref:System.Byte> <xref:System.DateTime> <xref:System.Decimal> <xref:System.Double> .) dönüştürme yöntemleri.  
  
- Uygulama türünün bir örneğini başka bir belirtilen türe dönüştürmek için genelleştirilmiş bir dönüştürme yöntemi. Desteklenmeyen dönüştürmeler bir oluşturması gerekir <xref:System.InvalidCastException> .  
  
 Her ortak dil çalışma zamanı temel türü (yani,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, <xref:System.Boolean> <xref:System.Byte> <xref:System.Char> <xref:System.DateTime> <xref:System.Decimal> <xref:System.Double> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.Single> <xref:System.String> <xref:System.UInt16> <xref:System.UInt32> ve <xref:System.UInt64> ), <xref:System.DBNull> ve <xref:System.Enum> türleri <xref:System.IConvertible> Ancak bunlar açık arabirim uygulamalarıdır; <xref:System.IConvertible>Aşağıdaki örnekte gösterildiği gibi, dönüştürme yöntemi yalnızca bir arabirim değişkeni üzerinden çağrılabilir. Bu örnek, bir <xref:System.Int32> değeri eşdeğer değerine dönüştürür <xref:System.Char> .  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Dönüştürme yöntemini, uygulama türünde değil, kendi arabiriminde çağırma gereksinimi, açık arabirim uygulamalarını görece pahalılaştırır. Bunun yerine, <xref:System.Convert> ortak dil çalışma zamanı temel türleri arasında dönüştürme yapmak için sınıfının uygun üyesini çağırmanız önerilir. Daha fazla bilgi için [Convert sınıfının](#the-convert-class)sonraki bölümüne bakın.  
  
> [!NOTE]
> <xref:System.IConvertible>Arabirime ve <xref:System.Convert> .NET Framework tarafından sunulan sınıfa ek olarak, tek tek diller dönüştürmeleri gerçekleştirmek için de yollar verebilir. Örneğin, C# atama işleçlerini kullanır; Visual Basic, ve gibi derleyici tarafından uygulanan dönüştürme işlevlerini `CType` kullanır `CInt` `DirectCast` .  
  
 Çoğu bölüm için <xref:System.IConvertible> arabirim, .NET Framework temel türler arasında dönüştürmeyi destekleyecek şekilde tasarlanmıştır. Ancak, arabirim, o türün diğer özel türlere dönüştürülmesini desteklemek için özel bir tür tarafından da uygulanabilir. Daha fazla bilgi için, bu konunun ilerleyen bölümlerindeki [ChangeType yöntemiyle özel dönüştürmeler](#custom-conversions-with-the-changetype-method) bölümüne bakın.

## <a name="the-convert-class"></a>Dönüştürme Sınıfı
 Her temel türün <xref:System.IConvertible> arabirim uygulamasının tür dönüştürmesi gerçekleştirmek için çağrılabilir olmasına karşın, sınıfının yöntemlerini çağırmak, <xref:System.Convert?displayProperty=nameWithType> bir temel türden diğerine dönüştürmek için önerilen dilden bağımsız bir yoldur. Ayrıca, <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi belirtilen özel bir türden başka bir türe dönüştürmek için de kullanılabilir.  
  
### <a name="conversions-between-base-types"></a>Temel Türler Arasında Dönüştürme  
 <xref:System.Convert>Sınıfı, temel türler arasında dönüştürmeler gerçekleştirmek için dilden bağımsız bir yol sağlar ve ortak dil çalışma zamanını hedefleyen tüm dillerde kullanılabilir. Her iki genişletme ve daraltma dönüştürmesi için bir yöntem kümesi sağlar ve <xref:System.InvalidCastException> Desteklenmeyen dönüşümler (örneğin bir <xref:System.DateTime> değeri bir tamsayı değerine dönüştürme) oluşturur. Daraltma dönüştürmeleri işaretlenmiş bir bağlamda gerçekleştirilir ve <xref:System.OverflowException> dönüştürme başarısız olursa bir oluşturulur.  
  
> [!IMPORTANT]
> <xref:System.Convert>Sınıfı her temel türe ve bu türden dönüştürülecek Yöntemler içerdiğinden, her temel türün açık arabirim uygulamasını çağırma gereksinimini ortadan kaldırır <xref:System.IConvertible> .  
  
 Aşağıdaki örnek, <xref:System.Convert?displayProperty=nameWithType> .NET Framework temel türleri arasında birkaç genişletme ve daraltma dönüştürmesi gerçekleştirmek için sınıfının kullanımını gösterir.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 Bazı durumlarda, kayan nokta değerlerine dönüştürme yaparken, bir dönüştürme, bir oluşturmasa bile bir duyarlık kaybı içerebilir <xref:System.OverflowException> . Aşağıdaki örnekte bu kesinlik kaybı gösterilmektedir. İlk durumda, <xref:System.Decimal> bir değer bir değerine dönüştürüldüğünde daha az duyarlığa sahiptir (daha az önemli basamak) <xref:System.Double> . İkinci durumda, <xref:System.Double> dönüştürme işleminin tamamlanabilmesi için bir değer 42,72 ' den 43 ' e yuvarlanır.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Sınıfı tarafından desteklenen genişleyen ve daraltma dönüştürmelerini listeleyen bir tablo için <xref:System.Convert> bkz. [tür dönüştürme tabloları](conversion-tables.md).  

### <a name="custom-conversions-with-the-changetype-method"></a>ChangeType Yöntemiyle Özel Dönüştürmeler  
 Temel türlerin her birine Dönüştürmelere ek olarak, <xref:System.Convert> sınıfı özel bir türü bir veya daha fazla önceden tanımlanmış türe dönüştürmek için kullanılabilir. Bu dönüştürme yöntemi tarafından gerçekleştirilir ve bu, sırayla <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> parametresinin yöntemine bir çağrı sarar <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> `value` . Bu, parametresi tarafından temsil edilen nesnenin `value` arabirimin bir uygulamasını sağlaması gerektiği anlamına gelir <xref:System.IConvertible> .  
  
> [!NOTE]
> <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType>Ve <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri <xref:System.Type> dönüştürülecek hedef türü belirtmek için bir nesnesi kullandığından `value` , türü derleme zamanında bilinmeyen bir nesneye dinamik dönüştürme gerçekleştirmek için kullanılabilirler. Ancak uygulamasının <xref:System.IConvertible> uygulamanın `value` bu dönüştürmeyi hala desteklemesi gerektiğini unutmayın.  
  
 Aşağıdaki örnek, <xref:System.IConvertible> bir `TemperatureCelsius` nesnenin bir nesneye dönüştürülmesine izin veren ve tam tersi olan arabirimin olası bir uygulamasını gösterir `TemperatureFahrenheit` . Örnek, `Temperature` <xref:System.IConvertible> arabirimini uygulayan ve yöntemi geçersiz kılan bir temel sınıfı tanımlar <xref:System.Object.ToString%2A?displayProperty=nameWithType> . Türetilmiş `TemperatureCelsius` ve `TemperatureFahrenheit` sınıflarının her biri, `ToType` `ToString` temel sınıfın yöntemlerini ve yöntemlerini geçersiz kılar.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Aşağıdaki örnek, nesneleri nesnelere dönüştürmek için bu uygulamalara yapılan birkaç çağrı gösterir <xref:System.IConvertible> `TemperatureCelsius` `TemperatureFahrenheit` ve tam tersi de geçerlidir.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>TypeConverter Sınıfı  
 .NET Framework Ayrıca, <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> sınıfı genişleterek ve tür dönüştürücüsünü bir öznitelik aracılığıyla türle ilişkilendirerek özel bir tür için tür dönüştürücüsü tanımlamanızı da sağlar <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> . Aşağıdaki tabloda, bu yaklaşım arasındaki farklar vurgulanmıştır ve <xref:System.IConvertible> özel bir tür için arabirim uygulama.  
  
> [!NOTE]
> Tasarım zamanı desteği, yalnızca kendisi için tanımlanmış bir tür dönüştürücüsü varsa, özel bir tür için sağlanabilir.  
  
|TypeConverter kullanılarak dönüştürme|IConvertible kullanılarak dönüştürme|  
|------------------------------------|-----------------------------------|  
|, Öğesinden ayrı bir sınıf türeterek özel bir tür için uygulanır <xref:System.ComponentModel.TypeConverter> . Bu türetilmiş sınıf, bir öznitelik uygulanarak özel türle ilişkilendirilir <xref:System.ComponentModel.TypeConverterAttribute> .|Dönüştürme yapmak için özel bir tür tarafından uygulanır. Türün bir kullanıcısı <xref:System.IConvertible> tür üzerinde bir dönüştürme yöntemi çağırır.|  
|Hem tasarım zamanında hem de çalışma zamanında kullanılabilir.|Yalnızca çalışma zamanında kullanılabilir.|  
|Yansıma kullanır; Bu nedenle, tarafından etkinleştirilen dönüşümden daha yavaştır <xref:System.IConvertible> .|Yansıma kullanmaz.|  
|özel türden diğer veri türlerine ve diğer veri türlerinden özel türe olmak üzere, iki yönlü tür dönüştürmelerine olanak tanır. Örneğin, <xref:System.ComponentModel.TypeConverter> için tanımlanan, `MyType` Dönüştürmelere ve arasında dönüştürme yapılmasına izin verir `MyType` <xref:System.String> <xref:System.String> `MyType` .|Özel bir türden diğer veri türlerine dönüştürmeye olanak tanır, fakat diğer veri türlerinden özel türe dönüştürmeye olanak tanımaz.|  
  
 Dönüştürmeleri gerçekleştirmek üzere tür dönüştürücülerinin kullanımı hakkında daha fazla bilgi için bkz <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tür dönüştürme tabloları](conversion-tables.md)
