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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8fc6f59b7a295cb73489a644da80976345cb172
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922684"
---
# <a name="type-conversion-in-the-net-framework"></a>.NET Framework'te Tür Dönüştürme
<a name="top"></a>Her değerin, değere ayrılan alan miktarı, sahip olduğu olası değer aralığı ve kullanılabilir olduğu Üyeler gibi öznitelikleri tanımlayan ilişkili bir türü vardır. Birçok değer, tek bir türden fazlası olarak ifade edilebilir. Örneğin, 4 değeri bir tamsayı olarak veya bir kayan nokta değeri olarak ifade edilebilir. Tür dönüştürme, eski bir türün değerine eşit olan, yeni türde bir değer oluşturur, fakat özgün nesnenin kimliğini (veya tam değerini) koruması gerekmez.  
  
 .NET Framework, aşağıdaki dönüştürmeleri otomatik olarak destekler:  
  
- Türetilmiş bir sınıftan temel sınıfa dönüştürme. Bu, örneğin, herhangi bir sınıf veya yapının bir örneğinin <xref:System.Object> örneğe dönüştürülebileceği anlamına gelir.  Bu dönüştürme bir atama veya dönüştürme işleci gerektirmez.  
  
- Temel sınıftan özgün türetilmiş sınıfa geri dönüştürme. ' C#De, bu dönüştürme bir atama işleci gerektirir. Visual Basic, açık ise `CType` `Option Strict` işleci gerektirir.  
  
- Arabirimi uygulayan bir türden, bu arabirimi temsil eden bir arabirim nesnesine dönüştürme. Bu dönüştürme bir atama veya dönüştürme işleci gerektirmez.  
  
- Arabirim nesnesinden bu arabirimi uygulayan özgün türe dönüştürme.  ' C#De, bu dönüştürme bir atama işleci gerektirir. Visual Basic, açık ise `CType` `Option Strict` işleci gerektirir.  
  
 Bu otomatik Dönüştürmelere ek olarak .NET Framework, özel tür dönüştürmeyi destekleyen çeşitli özellikler sağlar. Bunlar aşağıdakileri içerir:  
  
- Türler arasında kullanılabilir genişletme dönüştürmelerini tanımlayan işleç.`Implicit` Daha fazla bilgi için [örtük operatör ile örtük dönüştürme](#implicit_conversion_with_the_implicit_operator) bölümüne bakın.  
  
- Türler arasında kullanılabilir daraltma dönüştürmelerini tanımlayan işleç.`Explicit` Daha fazla bilgi için [Açık operatör Ile açık dönüştürme](#explicit_conversion_with_the_explicit_operator) bölümüne bakın.  
  
- Temel .NET Framework veri türlerinin her birine dönüşümler tanımlayan arabirim.<xref:System.IConvertible> Daha fazla bilgi için, bkz. [ıverli arabirim](#the_iconvertible_interface) bölümü.  
  
- Arabirimindeki yöntemleri uygulayan bir yöntemler kümesi sağlayan sınıfı.<xref:System.Convert> <xref:System.IConvertible> Daha fazla bilgi için [Convert Class](#Convert) bölümüne bakın.  
  
- Belirtilen bir türün başka bir türe dönüştürülmesini desteklemek için genişletilebilen bir temel sınıf olan sınıf.<xref:System.ComponentModel.TypeConverter> Daha fazla bilgi için [TypeConverter sınıfı](#the_typeconverter_class) bölümüne bakın.  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Örtülü İşleçle Örtülü Dönüştürme  
 Genişletme dönüştürmeleri, varolan bir türün değerinden, hedef türe göre daha kısıtlayıcı bir aralığı veya daha kısıtlayıcı bir üye listesi olan yeni bir değer oluşturmayı gerektirir. Genişletme dönüştürmeleri, (kesinlik kaybıyla sonuçlanabilir olsalar da) veri kaybıyla sonuçlanmaz. Veriler kaybedilemeyeceğinden, derleyiciler, açık bir dönüştürme yöntemi veya bir yayın işleci kullanılmadan, dönüştürmeyi örtülü olarak veya saydam olarak işleyebilir.  
  
> [!NOTE]
> Örtülü bir dönüştürme uygulayan kod bir dönüştürme yöntemi çağırabilir veya bir yayımlama işleci kullanabilir olsa da, örtülü dönüştürmeleri destekleyen derleyiciler tarafından kullanılmaları gerekmez.  
  
 <xref:System.Decimal> Örneğin, türü örtük dönüştürmeleri<xref:System.SByte>, <xref:System.Char> <xref:System.Byte> ,,,,<xref:System.Int16>,, ve<xref:System.UInt64> değerlerinden destekler. <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> <xref:System.UInt32> Aşağıdaki örnek, bir <xref:System.Decimal> değişkene değer atarken bu örtük dönüştürmelerin bazılarını göstermektedir.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Belirli bir dil derleyicisi özel işleçleri desteklerse, kendi özel türlerinizde de örtülü dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, oturum açma ve büyüklük gösterimini kullanan adlı `ByteWithSign` imzalı bir bayt veri türünün kısmi bir uygulamasını sağlar. Örtülü dönüştürme <xref:System.Byte> ve <xref:System.SByte> değerlere değerler `ByteWithSign` destekler.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Daha sonra istemci kodu, aşağıdaki `ByteWithSign` örnekte gösterildiği gibi herhangi bir <xref:System.SByte> açık dönüştürme gerçekleştirmeden veya herhangi bir atama işlecini kullanmadan bir değişken bildirebilir ve bu <xref:System.Byte> değeri atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Başa dön](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Açık İşleçli Açık Dönüştürme  
 Dönüştürmeleri daraltma, hedef türden daha geniş bir aralığa veya daha büyük bir üye listesine sahip olan varolan bir türün değerinden yeni bir değer oluşturulmasını gerektirir. Bir daraltma dönüşümü veri kaybıyla sonuçlanabildiğinden, derleyiciler genellikle dönüştürmenin bir dönüştürme yöntemine veya bir yayımlama işlecine yapılan bir çağrı yoluyla açık hale getirilmesini gerektirir. Yani, dönüştürmenin, geliştirici kodunda açıkça işlenmesi gerekir.  
  
> [!NOTE]
> Daraltma dönüştürmeleri için bir dönüştürme yöntemi veya atama işleci gerektirmesinin ana amacı, geliştiricinin veri kaybı olasılığını veya bir <xref:System.OverflowException> şekilde kod içinde işlenebilmesini sağlayacak şekilde haberdar hale getirme yöntemidir. Ancak, bazı derleyiciler bu gereksinimi ılımlı hale getirebilir. Örneğin, Visual Basic, `Option Strict` kapalıysa (varsayılan ayarı), Visual Basic derleyici, daraltma dönüşümlerini örtülü olarak gerçekleştirmeye çalışır.  
  
 Örneğin <xref:System.UInt32> <xref:System.UInt64> ,, ve<xref:System.Int32> veri türleri, aşağıdaki tabloda gösterildiği gibi, veri türünü aşan aralıklar vardır. <xref:System.Int64>  
  
|Tür|Int32 aralığıyla karşılaştırma|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>büyüktür ve <xref:System.Int64.MinValue?displayProperty=nameWithType> küçüktür (değerinden daha büyük bir negatif aralığa sahiptir) <xref:System.Int32.MinValue?displayProperty=nameWithType>. <xref:System.Int32.MaxValue?displayProperty=nameWithType>|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>Şundan <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyüktür.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>Şundan <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyüktür.|  
  
 Bu tür daraltma dönüşümlerini işlemek için .NET Framework, türlerin bir `Explicit` işleç tanımlamasına olanak tanır. Tek tek dil derleyicileri, bu işleci kendi söz dizimini kullanarak uygulayabilir ya da dönüştürmeyi gerçekleştirmek için <xref:System.Convert> sınıfının bir üyesi çağrılabilir. ( <xref:System.Convert> Sınıf hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [Convert sınıfı](#Convert) bölümüne bakın.) Aşağıdaki örnek, bu potansiyel olarak Aralık dışı tamsayı değerlerinin <xref:System.Int32> değerlere açıkça dönüştürülmesini işlemek için dil özelliklerinin kullanımını gösterir.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Açık dönüştürmeler farklı dillerde farklı sonuçlar üretebilir ve bu sonuçlar karşılık gelen <xref:System.Convert> yöntemin döndürdüğü değerden farklı olabilir. <xref:System.Double> Örneğin C# `(int)` , 12,63251 değeri <xref:System.Int32>bir öğesine dönüştürülürse, hem Visual Basic `CInt` yöntemi hem de .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> yöntemi 13 değerini döndürmek <xref:System.Double> için öğesini yuvarlar, ancak işleci, <xref:System.Double> 12 değerini döndürecek şekilde atar. Benzer şekilde, C# `(int)` işleci Boolean-tamsayı dönüştürmeyi desteklemez, ancak Visual Basic `CInt` yöntemi değerini `true` -1 ' e dönüştürür. Diğer taraftan, <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> yöntemi `true` değerini 1 olarak dönüştürür.  
  
 Derleyicilerin çoğu, açık dönüştürmelerin denetlenen veya denetlenmeyen bir şekilde yapılmasına olanak tanır. Denetlenen bir dönüştürme gerçekleştirildiğinde, dönüştürülecek türün değeri <xref:System.OverflowException> hedef türü aralığının dışında olduğunda bir atılır. Aynı koşullarda denetlenmeyen bir dönüştürme yapıldığında, dönüştürme bir özel durum oluşturmayabilir, fakat davranış tam olarak tanımsız hale gelir ve sonuç olarak hatalı bir değer oluşabilir.  
  
> [!NOTE]
> ' C#De, denetlenen dönüşümler, `checked` anahtar sözcüğü bir atama işleciyle birlikte kullanılarak `/checked+` veya derleyici seçeneği belirtilerek gerçekleştirilebilir. Buna karşılık, denetlenmeyen dönüştürmeler, atama işleciyle birlikte `unchecked` anahtar sözcüğü kullanılarak veya `/checked-` derleyici seçeneği belirtilerek gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenmez. Visual Basic ' de, projenin **Gelişmiş derleyici ayarları** iletişim kutusundaki `/removeintchecks-` **tamsayı taşma denetimlerini kaldır** onay kutusu temizlenerek veya derleyici seçeneği belirtilerek, denetlenen dönüştürmeler gerçekleştirilebilir. Buna karşılık, denetlenmeyen dönüştürmeler, projenin **Gelişmiş derleyici ayarları** iletişim kutusunda `/removeintchecks+` **tamsayı taşma denetimlerini kaldır** onay kutusu seçilerek veya derleyici seçeneği belirtilerek gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenir.  
  
 Aşağıdaki C# örnek `checked` , <xref:System.Byte>bir `unchecked` öğesininaralığının<xref:System.Byte> dışında bir değer bir değerine dönüştürüldüğünde davranıştaki farkı göstermek için ve anahtar sözcüklerini kullanır. İşaretlenen dönüştürme bir özel durum oluşturur, ancak Denetlenmemiş dönüştürme <xref:System.Byte.MaxValue?displayProperty=nameWithType> <xref:System.Byte> değişkenine atar.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Belirli bir dil derleyicisi özel aşırı yüklü işleçleri desteklerse, kendi özel türlerinizde de açık dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, oturum açma ve büyüklük gösterimini kullanan adlı `ByteWithSign` imzalı bir bayt veri türünün kısmi bir uygulamasını sağlar. Açık dönüştürme <xref:System.Int32> ve <xref:System.UInt32> `ByteWithSign` değerlere değerler destekler.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Daha sonra, aşağıdaki örnekte gösterildiği `ByteWithSign` gibi, istemci kodu <xref:System.Int32> bir <xref:System.UInt32> değişken bildirebilir ve atamalar bir atama işleci veya dönüştürme yöntemi içeriyorsa bu değeri atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Başa dön](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>IConvertible Arabirimi  
 Herhangi bir türün ortak dil çalışma zamanı temel türüne dönüştürülmesini desteklemek için .NET Framework <xref:System.IConvertible> arabirimi sağlar. Uygulama türünün aşağıdakileri sağlaması gerekir:  
  
- Uygulama türünün değerini döndüren <xref:System.TypeCode> bir yöntem.  
  
- Uygulama türünü her ortak dil çalışma zamanı temel türüne (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime> <xref:System.Decimal> <xref:System.Double>,, vb.) dönüştürme yöntemleri.  
  
- Uygulama türünün bir örneğini başka bir belirtilen türe dönüştürmek için genelleştirilmiş bir dönüştürme yöntemi. Desteklenmeyen dönüştürmeler bir <xref:System.InvalidCastException>oluşturması gerekir.  
  
 Her ortak dil <xref:System.Boolean>çalışma zamanı temel türü ( <xref:System.Decimal> <xref:System.DateTime> <xref:System.Double> <xref:System.Byte> <xref:System.Char>,,, ,,,,,,,,,,,,,,,<xref:System.Int32> <xref:System.Int16> <xref:System.Int64> <xref:System.SByte> <xref:System.Single> <xref:System.String> ,,<xref:System.Enum> , ,ve<xref:System.UInt64>) ,<xref:System.DBNull> ve türleri, arabirimini<xref:System.IConvertible> uygular. <xref:System.UInt32> <xref:System.UInt16> Ancak bunlar açık arabirim uygulamalarıdır; Aşağıdaki örnekte gösterildiği gibi, dönüştürme yöntemi yalnızca bir <xref:System.IConvertible> arabirim değişkeni üzerinden çağrılabilir. Bu örnek, bir <xref:System.Int32> değeri eşdeğer <xref:System.Char> değerine dönüştürür.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Dönüştürme yöntemini, uygulama türünde değil, kendi arabiriminde çağırma gereksinimi, açık arabirim uygulamalarını görece pahalılaştırır. Bunun yerine, ortak dil çalışma zamanı temel türleri arasında dönüştürme yapmak <xref:System.Convert> için sınıfının uygun üyesini çağırmanız önerilir. Daha fazla bilgi için [Convert sınıfının](#Convert)sonraki bölümüne bakın.  
  
> [!NOTE]
> <xref:System.IConvertible> Arabirime<xref:System.Convert> ve .NET Framework tarafından sunulan sınıfa ek olarak, tek tek diller dönüştürmeleri gerçekleştirmek için de yollar verebilir. Örneğin, C# atama işleçlerini kullanır; Visual Basic, ve `CType` `CInt` gibiderleyici`DirectCast`tarafından uygulanan dönüştürme işlevlerini kullanır.  
  
 Çoğu bölüm <xref:System.IConvertible> için arabirim, .NET Framework temel türler arasında dönüştürmeyi destekleyecek şekilde tasarlanmıştır. Ancak, arabirim, o türün diğer özel türlere dönüştürülmesini desteklemek için özel bir tür tarafından da uygulanabilir. Daha fazla bilgi için, bu konunun ilerleyen bölümlerindeki [ChangeType yöntemiyle özel dönüştürmeler](#ChangeType) bölümüne bakın.  
  
 [Başa dön](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Dönüştürme Sınıfı  
 Her temel türün <xref:System.IConvertible> arabirim uygulamasının tür dönüştürmesi gerçekleştirmek için çağrılabilir olmasına karşın, <xref:System.Convert?displayProperty=nameWithType> sınıfının yöntemlerini çağırmak, bir temel türden diğerine dönüştürmek için önerilen dilden bağımsız bir yoldur. Ayrıca, <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi belirtilen özel bir türden başka bir türe dönüştürmek için de kullanılabilir.  
  
### <a name="conversions-between-base-types"></a>Temel Türler Arasında Dönüştürme  
 Sınıfı <xref:System.Convert> , temel türler arasında dönüştürmeler gerçekleştirmek için dilden bağımsız bir yol sağlar ve ortak dil çalışma zamanını hedefleyen tüm dillerde kullanılabilir. Her iki genişletme ve daraltma dönüştürmesi için bir yöntem kümesi sağlar ve desteklenmeyen dönüşümler (örneğin bir <xref:System.InvalidCastException> <xref:System.DateTime> değeri bir tamsayı değerine dönüştürme) oluşturur. Daraltma dönüştürmeleri işaretlenmiş bir bağlamda gerçekleştirilir ve dönüştürme başarısız olursa bir <xref:System.OverflowException> oluşturulur.  
  
> [!IMPORTANT]
> Sınıfı her temel türe ve bu türden dönüştürülecek Yöntemler içerdiğinden, her temel <xref:System.IConvertible> türün açık arabirim uygulamasını çağırma gereksinimini ortadan kaldırır. <xref:System.Convert>  
  
 Aşağıdaki örnek, .NET Framework temel türleri arasında birkaç <xref:System.Convert?displayProperty=nameWithType> genişletme ve daraltma dönüştürmesi gerçekleştirmek için sınıfının kullanımını gösterir.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 Bazı durumlarda, kayan nokta değerlerine dönüştürme yaparken, bir dönüştürme, bir <xref:System.OverflowException>oluşturmasa bile bir duyarlık kaybı içerebilir. Aşağıdaki örnekte bu kesinlik kaybı gösterilmektedir. İlk durumda, <xref:System.Decimal> bir değer bir <xref:System.Double>değerine dönüştürüldüğünde daha az duyarlığa sahiptir (daha az önemli basamak). İkinci durumda, dönüştürme işleminin tamamlanabilmesi <xref:System.Double> için bir değer 42,72 ' den 43 ' e yuvarlanır.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 <xref:System.Convert> Sınıfı tarafından desteklenen genişleyen ve daraltma dönüştürmelerini listeleyen bir tablo için bkz. [tür dönüştürme tabloları](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>ChangeType Yöntemiyle Özel Dönüştürmeler  
 Temel türlerin her birine Dönüştürmelere ek olarak, <xref:System.Convert> sınıfı özel bir türü bir veya daha fazla önceden tanımlanmış türe dönüştürmek için kullanılabilir. Bu dönüştürme <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi tarafından gerçekleştirilir ve bu, sırayla `value` parametresinin <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> yöntemine bir çağrı sarar. Bu, `value` parametresi tarafından temsil edilen nesnenin <xref:System.IConvertible> arabirimin bir uygulamasını sağlaması gerektiği anlamına gelir.  
  
> [!NOTE]
> Ve yöntemleri dönüştürülecek `value` hedef türü belirtmek <xref:System.Type> için bir nesnesi kullandığından, türü derleme zamanında bilinmeyen bir nesneye dinamik dönüştürme gerçekleştirmek için kullanılabilirler. <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> Ancak uygulamasının <xref:System.IConvertible> `value` uygulamanın bu dönüştürmeyi hala desteklemesi gerektiğini unutmayın.  
  
 Aşağıdaki örnek, bir <xref:System.IConvertible> `TemperatureCelsius` nesnenin bir `TemperatureFahrenheit` nesneye dönüştürülmesine izin veren ve tam tersi olan arabirimin olası bir uygulamasını gösterir. Örnek, `Temperature` <xref:System.IConvertible> arabirimini uygulayan ve <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi geçersiz kılan bir temel sınıfı tanımlar. Türetilmiş `TemperatureCelsius` ve `TemperatureFahrenheit` sınıflarının herbiri`ToType` , temel sınıfın yöntemleriniveyöntemlerinigeçersizkılar.`ToString`  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Aşağıdaki örnek, nesneleri <xref:System.IConvertible> `TemperatureFahrenheit` nesnelere dönüştürmek `TemperatureCelsius` için bu uygulamalara yapılan birkaç çağrı gösterir ve tam tersi de geçerlidir.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Başa dön](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>TypeConverter Sınıfı  
 .NET Framework Ayrıca, <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> sınıfı genişleterek ve tür dönüştürücüsünü bir <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> öznitelik aracılığıyla türle ilişkilendirerek özel bir tür için tür dönüştürücüsü tanımlamanızı da sağlar. Aşağıdaki tabloda, bu yaklaşım arasındaki farklar vurgulanmıştır ve özel bir <xref:System.IConvertible> tür için arabirim uygulama.  
  
> [!NOTE]
> Tasarım zamanı desteği, yalnızca kendisi için tanımlanmış bir tür dönüştürücüsü varsa, özel bir tür için sağlanabilir.  
  
|TypeConverter kullanılarak dönüştürme|IConvertible kullanılarak dönüştürme|  
|------------------------------------|-----------------------------------|  
|, Öğesinden <xref:System.ComponentModel.TypeConverter>ayrı bir sınıf türeterek özel bir tür için uygulanır. Bu türetilmiş sınıf, bir <xref:System.ComponentModel.TypeConverterAttribute> öznitelik uygulanarak özel türle ilişkilendirilir.|Dönüştürme yapmak için özel bir tür tarafından uygulanır. Türün bir kullanıcısı tür üzerinde bir <xref:System.IConvertible> dönüştürme yöntemi çağırır.|  
|Hem tasarım zamanında hem de çalışma zamanında kullanılabilir.|Yalnızca çalışma zamanında kullanılabilir.|  
|Yansıma kullanır; Bu nedenle, tarafından <xref:System.IConvertible>etkinleştirilen dönüşümden daha yavaştır.|Yansıma kullanmaz.|  
|özel türden diğer veri türlerine ve diğer veri türlerinden özel türe olmak üzere, iki yönlü tür dönüştürmelerine olanak tanır. Örneğin, <xref:System.ComponentModel.TypeConverter> için <xref:System.String> `MyType` <xref:System.String> tanımlanan, Dönüştürmelere ve arasında`MyType`dönüştürme yapılmasına izin verir. `MyType`|Özel bir türden diğer veri türlerine dönüştürmeye olanak tanır, fakat diğer veri türlerinden özel türe dönüştürmeye olanak tanımaz.|  
  
 Dönüştürmeleri gerçekleştirmek üzere tür dönüştürücülerinin kullanımı hakkında daha fazla bilgi için <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tür Dönüştürme Tabloları](../../../docs/standard/base-types/conversion-tables.md)
