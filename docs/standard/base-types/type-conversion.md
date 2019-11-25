---
title: .NET Framework'te Tür Dönüştürme
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
ms.openlocfilehash: 0e88303f2bac2dae90a97f9d2de92af1d2a0f80d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976486"
---
# <a name="type-conversion-in-the-net-framework"></a>.NET Framework'te Tür Dönüştürme
Her değerin, değere ayrılan yer miktarı, sahip olabileceği olası değerler aralığı ve kullanılabilir yaptığı üyeler gibi öznitelikleri tanımlayan ilişkili bir türü vardır. Birçok değer, tek bir türden fazlası olarak ifade edilebilir. Örneğin, 4 değeri bir tamsayı olarak veya bir kayan nokta değeri olarak ifade edilebilir. Tür dönüştürme, eski bir türün değerine eşit olan, yeni türde bir değer oluşturur, fakat özgün nesnenin kimliğini (veya tam değerini) koruması gerekmez.  
  
 .NET Framework, aşağıdaki dönüştürmeleri otomatik olarak destekler:  
  
- Türetilmiş bir sınıftan temel sınıfa dönüştürme. Bu, örneğin, herhangi bir sınıf veya yapının örneğinin bir <xref:System.Object> örneğine dönüştürülebileceği anlamına gelir.  Bu dönüştürme bir atama veya dönüştürme işleci gerektirmez.  
  
- Temel sınıftan özgün türetilmiş sınıfa geri dönüştürme. ' C#De, bu dönüştürme bir atama işleci gerektirir. Visual Basic, `Option Strict` açık ise `CType` işlecini gerektirir.  
  
- Arabirimi uygulayan bir türden, bu arabirimi temsil eden bir arabirim nesnesine dönüştürme. Bu dönüştürme bir atama veya dönüştürme işleci gerektirmez.  
  
- Arabirim nesnesinden bu arabirimi uygulayan özgün türe dönüştürme.  ' C#De, bu dönüştürme bir atama işleci gerektirir. Visual Basic, `Option Strict` açık ise `CType` işlecini gerektirir.  
  
 Bu otomatik Dönüştürmelere ek olarak .NET Framework, özel tür dönüştürmeyi destekleyen çeşitli özellikler sağlar. Bunlar aşağıdakileri içerir:  
  
- Türler arasında kullanılabilir genişletme dönüştürmelerini tanımlayan `Implicit` işleci. Daha fazla bilgi için [örtük operatör ile örtük dönüştürme](#implicit-conversion-with-the-implicit-operator) bölümüne bakın.  
  
- Türler arasında kullanılabilir daraltma dönüştürmelerini tanımlayan `Explicit` işleci. Daha fazla bilgi için [Açık operatör Ile açık dönüştürme](#explicit-conversion-with-the-explicit-operator) bölümüne bakın.  
  
- Temel .NET Framework veri türlerinin her birine dönüştürmeleri tanımlayan <xref:System.IConvertible> arabirimi. Daha fazla bilgi için, bkz. [ıverli arabirim](#the-iconvertible-interface) bölümü.  
  
- <xref:System.IConvertible> arabirimindeki yöntemleri uygulayan bir yöntemler kümesi sağlayan <xref:System.Convert> sınıfı. Daha fazla bilgi için [Convert Class](#the-convert-class) bölümüne bakın.  
  
- Belirtilen bir türün başka bir türe dönüştürülmesini desteklemek için genişletilebilen temel bir sınıf olan <xref:System.ComponentModel.TypeConverter> sınıfı. Daha fazla bilgi için [TypeConverter sınıfı](#the-typeconverter-class) bölümüne bakın.  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Örtülü İşleçle Örtülü Dönüştürme  
 Genişletme dönüştürmeleri, varolan bir türün değerinden, hedef türe göre daha kısıtlayıcı bir aralığı veya daha kısıtlayıcı bir üye listesi olan yeni bir değer oluşturmayı gerektirir. Genişletme dönüştürmeleri, (kesinlik kaybıyla sonuçlanabilir olsalar da) veri kaybıyla sonuçlanmaz. Veriler kaybedilemeyeceğinden, derleyiciler, açık bir dönüştürme yöntemi veya bir yayın işleci kullanılmadan, dönüştürmeyi örtülü olarak veya saydam olarak işleyebilir.  
  
> [!NOTE]
> Örtülü bir dönüştürme uygulayan kod bir dönüştürme yöntemi çağırabilir veya bir yayımlama işleci kullanabilir olsa da, örtülü dönüştürmeleri destekleyen derleyiciler tarafından kullanılmaları gerekmez.  
  
 Örneğin <xref:System.Decimal> türü <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>ve <xref:System.UInt64> değerlerinden örtük dönüştürmeleri destekler. Aşağıdaki örnek, <xref:System.Decimal> değişkenine değer atarken bu örtük dönüştürmelerin bazılarını göstermektedir.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Belirli bir dil derleyicisi özel işleçleri desteklerse, kendi özel türlerinizde de örtülü dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, oturum açma ve büyüklük gösterimini kullanan `ByteWithSign` adlı imzalı bir bayt veri türünün kısmi bir uygulamasını sağlar. <xref:System.Byte> ve <xref:System.SByte> değerlerinin `ByteWithSign` değerlere örtük olarak dönüştürülmesini destekler.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 İstemci kodu daha sonra, aşağıdaki örnekte gösterildiği gibi, bir `ByteWithSign` değişken bildirebilir ve bu <xref:System.Byte> ve <xref:System.SByte> değerlerini hiçbir açık dönüştürme gerçekleştirmeden veya herhangi bir atama işlecini kullanarak atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Açık İşleçli Açık Dönüştürme  
 Dönüştürmeleri daraltma, hedef türden daha geniş bir aralığa veya daha büyük bir üye listesine sahip olan varolan bir türün değerinden yeni bir değer oluşturulmasını gerektirir. Bir daraltma dönüşümü veri kaybıyla sonuçlanabildiğinden, derleyiciler genellikle dönüştürmenin bir dönüştürme yöntemine veya bir yayımlama işlecine yapılan bir çağrı yoluyla açık hale getirilmesini gerektirir. Yani, dönüştürmenin, geliştirici kodunda açıkça işlenmesi gerekir.  
  
> [!NOTE]
> Daraltma dönüştürmeleri için bir dönüştürme yöntemi veya atama işleci gerektirmesinin ana amacı, geliştiricinin veri kaybı olasılığa veya bir <xref:System.OverflowException> kodda işlenebilmesi için bir olasılığını bilmesini sağlamaktır. Ancak, bazı derleyiciler bu gereksinimi ılımlı hale getirebilir. Örneğin, Visual Basic `Option Strict` kapalıysa (varsayılan ayarı), Visual Basic derleyici daraltma dönüştürmelerini örtük olarak gerçekleştirmeye çalışır.  
  
 Örneğin, <xref:System.UInt32>, <xref:System.Int64>ve <xref:System.UInt64> veri türleri, aşağıdaki tabloda gösterildiği gibi <xref:System.Int32> veri türünü aşan aralıklar vardır.  
  
|Tür|Int32 aralığıyla karşılaştırma|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyüktür ve <xref:System.Int64.MinValue?displayProperty=nameWithType> küçüktür (daha büyük bir negatif aralığa sahiptir) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>, <xref:System.Int32.MaxValue?displayProperty=nameWithType>daha büyük.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>, <xref:System.Int32.MaxValue?displayProperty=nameWithType>daha büyük.|  
  
 Bu tür daraltma dönüşümlerini işlemek için .NET Framework, türlerin bir `Explicit` işleci tanımlamasına olanak tanır. Tek tek dil derleyicileri, bu işleci kendi söz dizimini kullanarak uygulayabilir veya <xref:System.Convert> sınıfının bir üyesi dönüştürmeyi gerçekleştirmek için çağrılabilir. (<xref:System.Convert> sınıfı hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [Convert sınıfı](#the-convert-class) bölümüne bakın.) Aşağıdaki örnek, bu potansiyel olarak Aralık dışı tamsayı değerlerinin <xref:System.Int32> değerlerine açık dönüştürülmesini işlemek için dil özelliklerinin kullanımını gösterir.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Açık dönüştürmeler farklı dillerde farklı sonuçlar üretebilir ve bu sonuçlar karşılık gelen <xref:System.Convert> yöntemi tarafından döndürülen değerden farklı olabilir. Örneğin, 12,63251 <xref:System.Double> değeri bir <xref:System.Int32>dönüştürülürse, hem Visual Basic `CInt` yöntemi hem de .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> yöntemi 13 değerini döndürmek için <xref:System.Double> ' i yuvarlar, ancak C# `(int)` işleci 12 değerini döndürmek için <xref:System.Double> keser. Benzer şekilde, C# `(int)` işleci Boolean-tamsayı dönüştürmeyi desteklemez, ancak Visual Basic `CInt` yöntemi `true` değerini-1 ' e dönüştürür. Diğer taraftan <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> yöntemi bir `true` değerini 1 ' e dönüştürür.  
  
 Derleyicilerin çoğu, açık dönüştürmelerin denetlenen veya denetlenmeyen bir şekilde yapılmasına olanak tanır. Denetlenen bir dönüştürme gerçekleştirildiğinde, dönüştürülecek türün değeri hedef türü aralığının dışında olduğunda bir <xref:System.OverflowException> oluşur. Aynı koşullarda denetlenmeyen bir dönüştürme yapıldığında, dönüştürme bir özel durum oluşturmayabilir, fakat davranış tam olarak tanımsız hale gelir ve sonuç olarak hatalı bir değer oluşabilir.  
  
> [!NOTE]
> ' C#De, denetlenen dönüşümler `checked` anahtar sözcüğü bir atama işleciyle birlikte kullanılarak veya `/checked+` derleyici seçeneği belirtilerek gerçekleştirilebilir. Buna karşılık, denetlenmeyen dönüştürmeler, atama işleciyle birlikte `unchecked` anahtar sözcüğü kullanılarak veya `/checked-` derleyici seçeneği belirtilerek gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenmez. Visual Basic ' de, projenin **Gelişmiş derleyici ayarları** iletişim kutusundaki **tamsayı taşma denetimlerini kaldır** onay kutusu temizlenerek veya `/removeintchecks-` derleyici seçeneği belirtilerek, denetlenen dönüştürmeler gerçekleştirilebilir. Buna karşılık, denetlenmeyen dönüştürmeler, projenin **Gelişmiş derleyici ayarları** iletişim kutusunda **tamsayı taşma denetimlerini kaldır** onay kutusu seçilerek veya `/removeintchecks+` derleyici seçeneği belirtilerek gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenir.  
  
 Aşağıdaki C# örnek, bir <xref:System.Byte> aralığı dışında bir değer <xref:System.Byte>olarak dönüştürüldüğünde davranış farkını göstermek için `checked` ve `unchecked` anahtar sözcüklerini kullanır. İşaretlenen dönüştürme bir özel durum oluşturur, ancak Denetlenmemiş dönüştürme <xref:System.Byte> değişkenine <xref:System.Byte.MaxValue?displayProperty=nameWithType> atar.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Belirli bir dil derleyicisi özel aşırı yüklü işleçleri desteklerse, kendi özel türlerinizde de açık dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, oturum açma ve büyüklük gösterimini kullanan `ByteWithSign` adlı imzalı bir bayt veri türünün kısmi bir uygulamasını sağlar. <xref:System.Int32> ve <xref:System.UInt32> değerlerinin `ByteWithSign` değerlerine açık dönüştürülmesini destekler.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Daha sonra, aşağıdaki örnekte gösterildiği gibi, istemci kodu bir `ByteWithSign` değişkeni bildirebilir ve atamalar bir atama işleci veya dönüştürme yöntemi içeriyorsa, <xref:System.Int32> ve <xref:System.UInt32> değerleri atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>IConvertible Arabirimi  
 Herhangi bir türün ortak dil çalışma zamanı temel türüne dönüştürülmesini desteklemek için, .NET Framework <xref:System.IConvertible> arabirimini sağlar. Uygulama türünün aşağıdakileri sağlaması gerekir:  
  
- Uygulama türünün <xref:System.TypeCode> döndüren bir yöntem.  
  
- Uygulama türünü her ortak dil çalışma zamanı temel türüne dönüştürme yöntemleri (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, vb.).  
  
- Uygulama türünün bir örneğini başka bir belirtilen türe dönüştürmek için genelleştirilmiş bir dönüştürme yöntemi. Desteklenmeyen dönüştürmeler bir <xref:System.InvalidCastException>oluşturması gerekir.  
  
 Her ortak dil çalışma zamanı temel türü (yani, <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>ve <xref:System.UInt64>) ve <xref:System.DBNull> ve <xref:System.Enum> türleri <xref:System.IConvertible> arabirimini uygular. Ancak bunlar açık arabirim uygulamalarıdır; Aşağıdaki örnekte gösterildiği gibi, dönüştürme yöntemi yalnızca bir <xref:System.IConvertible> arabirimi değişkeniyle çağrılabilir. Bu örnek, bir <xref:System.Int32> değerini eşdeğer <xref:System.Char> değerine dönüştürür.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Dönüştürme yöntemini, uygulama türünde değil, kendi arabiriminde çağırma gereksinimi, açık arabirim uygulamalarını görece pahalılaştırır. Bunun yerine, ortak dil çalışma zamanı temel türleri arasında dönüştürmek için <xref:System.Convert> sınıfının uygun üyesini çağırmanız önerilir. Daha fazla bilgi için [Convert sınıfının](#the-convert-class)sonraki bölümüne bakın.  
  
> [!NOTE]
> <xref:System.IConvertible> arabirimine ve .NET Framework tarafından sunulan <xref:System.Convert> sınıfına ek olarak, tek tek diller dönüştürmeleri gerçekleştirmeye yönelik yollar da verebilir. Örneğin, C# atama işleçlerini kullanır; Visual Basic, `CType`, `CInt`ve `DirectCast`gibi derleyici tarafından uygulanan dönüştürme işlevlerini kullanır.  
  
 Çoğu bölüm için, <xref:System.IConvertible> arabirimi .NET Framework temel türler arasında dönüştürmeyi destekleyecek şekilde tasarlanmıştır. Ancak, arabirim, o türün diğer özel türlere dönüştürülmesini desteklemek için özel bir tür tarafından da uygulanabilir. Daha fazla bilgi için, bu konunun ilerleyen bölümlerindeki [ChangeType yöntemiyle özel dönüştürmeler](#custom-conversions-with-the-changetype-method) bölümüne bakın.

## <a name="the-convert-class"></a>Dönüştürme Sınıfı
 Her temel türün <xref:System.IConvertible> arabirimi uygulamasının bir tür dönüştürmesi gerçekleştirecek şekilde çağrılabilmesine rağmen, <xref:System.Convert?displayProperty=nameWithType> sınıfının yöntemlerini çağırmak, bir temel türden diğerine dönüştürmek için önerilen dilden bağımsız yoldur. Ayrıca, <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi belirtilen özel bir türden başka bir türe dönüştürmek için de kullanılabilir.  
  
### <a name="conversions-between-base-types"></a>Temel Türler Arasında Dönüştürme  
 <xref:System.Convert> sınıfı, temel türler arasında dönüştürmeler gerçekleştirmek için dilden bağımsız bir yol sağlar ve ortak dil çalışma zamanını hedefleyen tüm dillerde kullanılabilir. Her iki genişletme ve daraltma dönüştürmesi için bir yöntem kümesi sağlar ve desteklenmeyen dönüştürmeler için bir <xref:System.InvalidCastException> (bir <xref:System.DateTime> değerinin bir tamsayı değerine dönüştürülmesi gibi) oluşturur. Daraltma dönüştürmeleri, denetlenen bir bağlamda gerçekleştirilir ve dönüştürme başarısız olursa bir <xref:System.OverflowException> oluşturulur.  
  
> [!IMPORTANT]
> <xref:System.Convert> sınıfı her temel türe dönüştürmek için yöntemler içerdiğinden, her temel türün <xref:System.IConvertible> açık arabirim uygulamasını çağırma gereksinimini ortadan kaldırır.  
  
 Aşağıdaki örnek, .NET Framework temel türler arasında birkaç genişletme ve daraltma dönüştürmesi gerçekleştirmek için <xref:System.Convert?displayProperty=nameWithType> sınıfının kullanımını gösterir.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 Bazı durumlarda, kayan nokta değerlerine dönüştürme yaparken, özellikle de bir <xref:System.OverflowException>oluşturmasa bile bir dönüştürme bir duyarlık kaybı içerebilir. Aşağıdaki örnekte bu kesinlik kaybı gösterilmektedir. İlk durumda, bir <xref:System.Decimal> değeri bir <xref:System.Double>dönüştürüldüğünde daha az duyarlığa sahiptir (daha az önemli basamak). İkinci durumda, dönüştürme işleminin tamamlanabilmesi için <xref:System.Double> bir değer 42,72 ' den 43 ' e yuvarlanır.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 <xref:System.Convert> sınıfı tarafından desteklenen genişletme ve daraltma dönüştürmelerini listeleyen bir tablo için bkz. [tür dönüştürme tabloları](../../../docs/standard/base-types/conversion-tables.md).  

### <a name="custom-conversions-with-the-changetype-method"></a>ChangeType Yöntemiyle Özel Dönüştürmeler  
 Temel türlerin her birine Dönüştürmelere ek olarak, <xref:System.Convert> sınıfı özel bir türü bir veya daha fazla önceden tanımlanmış türe dönüştürmek için kullanılabilir. Bu dönüştürme <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi tarafından gerçekleştirilir ve bu, sırasıyla `value` parametresinin <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> yöntemine bir çağrı sarmalar. Bu, `value` parametresi tarafından temsil edilen nesnenin <xref:System.IConvertible> arabiriminin bir uygulamasını sağlaması gerektiği anlamına gelir.  
  
> [!NOTE]
> <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> ve <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri, `value` dönüştürüldüğü hedef türü belirtmek için bir <xref:System.Type> nesnesi kullandığından, türü derleme zamanında bilinmeyen bir nesneye dinamik dönüştürme gerçekleştirmek için kullanılabilirler. Ancak, `value` <xref:System.IConvertible> uygulamasının bu dönüştürmeyi desteklemeye devam ettiğinden emin olmanız gerektiğini unutmayın.  
  
 Aşağıdaki örnek, bir `TemperatureCelsius` nesnesinin bir `TemperatureFahrenheit` nesnesine dönüştürülmesine izin veren <xref:System.IConvertible> arabiriminin olası bir uygulamasını gösterir ve tam tersi de geçerlidir. Örnek, <xref:System.IConvertible> arabirimini uygulayan ve <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemini geçersiz kılan `Temperature`bir temel sınıf tanımlar. Türetilmiş `TemperatureCelsius` ve `TemperatureFahrenheit` sınıflarının her biri, temel sınıfın `ToType` ve `ToString` yöntemlerini geçersiz kılar.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Aşağıdaki örnek, `TemperatureCelsius` nesnelerini `TemperatureFahrenheit` nesnelerine dönüştürmek için bu <xref:System.IConvertible> uygulamalarına yapılan bazı çağrıları gösterir ve tam tersi de geçerlidir.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>TypeConverter Sınıfı  
 .NET Framework Ayrıca, <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> sınıfını genişleterek ve tür dönüştürücüsünü bir <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> özniteliği aracılığıyla türle ilişkilendirerek özel bir tür için tür dönüştürücüsü tanımlamanızı da sağlar. Aşağıdaki tabloda, bu yaklaşım arasındaki farklar vurgulanmıştır ve özel bir tür için <xref:System.IConvertible> arabirimini uygulama.  
  
> [!NOTE]
> Tasarım zamanı desteği, yalnızca kendisi için tanımlanmış bir tür dönüştürücüsü varsa, özel bir tür için sağlanabilir.  
  
|TypeConverter kullanılarak dönüştürme|IConvertible kullanılarak dönüştürme|  
|------------------------------------|-----------------------------------|  
|, <xref:System.ComponentModel.TypeConverter>'den ayrı bir sınıf türeterek özel bir tür için uygulanır. Bu türetilmiş sınıf, bir <xref:System.ComponentModel.TypeConverterAttribute> özniteliği uygulanarak özel türle ilişkilendirilir.|Dönüştürme yapmak için özel bir tür tarafından uygulanır. Türün bir kullanıcısı tür üzerinde <xref:System.IConvertible> bir dönüştürme yöntemi çağırır.|  
|Hem tasarım zamanında hem de çalışma zamanında kullanılabilir.|Yalnızca çalışma zamanında kullanılabilir.|  
|Yansıma kullanır; Bu nedenle, <xref:System.IConvertible>tarafından etkinleştirilen dönüştürmeye göre daha yavaştır.|Yansıma kullanmaz.|  
|özel türden diğer veri türlerine ve diğer veri türlerinden özel türe olmak üzere, iki yönlü tür dönüştürmelerine olanak tanır. Örneğin, `MyType` için tanımlanan <xref:System.ComponentModel.TypeConverter>, `MyType` Dönüştürmelere <xref:System.String>ve <xref:System.String> 'den `MyType`'ye dönüştürmeye olanak tanır.|Özel bir türden diğer veri türlerine dönüştürmeye olanak tanır, fakat diğer veri türlerinden özel türe dönüştürmeye olanak tanımaz.|  
  
 Dönüştürmeleri gerçekleştirmek üzere tür dönüştürücülerinin kullanımı hakkında daha fazla bilgi için bkz. <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tür Dönüştürme Tabloları](../../../docs/standard/base-types/conversion-tables.md)
