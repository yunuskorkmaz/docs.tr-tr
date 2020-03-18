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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976486"
---
# <a name="type-conversion-in-the-net-framework"></a>.NET Framework'te Tür Dönüştürme
Her değer, değere ayrılan alan miktarı, sahip olabileceği olası değerlerin aralığı ve kullanılabilir hale getiren üyeler gibi öznitelikleri tanımlayan ilişkili bir türü vardır. Birçok değer, tek bir türden fazlası olarak ifade edilebilir. Örneğin, 4 değeri bir tamsayı olarak veya bir kayan nokta değeri olarak ifade edilebilir. Tür dönüştürme, eski bir türün değerine eşit olan, yeni türde bir değer oluşturur, fakat özgün nesnenin kimliğini (veya tam değerini) koruması gerekmez.  
  
 .NET Framework otomatik olarak aşağıdaki dönüşümleri destekler:  
  
- Türetilmiş bir sınıftan taban sınıfa dönüştürme. Bu, örneğin, herhangi bir sınıf veya yapının bir örneğinin bir <xref:System.Object> örneğe dönüştürülebileceği anlamına gelir.  Bu dönüştürme bir döküm veya dönüştürme işleci gerektirmez.  
  
- Taban sınıftan özgün türemiş sınıfa dönüştürme. C#'da bu dönüştürme bir döküm işleci gerektirir. Visual Basic'te, `CType` üzerindeyse `Option Strict` işleci gerektirir.  
  
- Arabirim uygulayan bir türden, bu arabirimi temsil eden bir arabirim nesnesine dönüştürme. Bu dönüştürme bir döküm veya dönüştürme işleci gerektirmez.  
  
- Arabirim nesnesinden bu arabirimi uygulayan özgün türe dönüştürme.  C#'da bu dönüştürme bir döküm işleci gerektirir. Visual Basic'te, `CType` üzerindeyse `Option Strict` işleci gerektirir.  
  
 Bu otomatik dönüşümlere ek olarak,.NET Framework özel tür dönüştürmedestekleyen çeşitli özellikler sağlar. Bunlar aşağıdakileri içerir:  
  
- Türler `Implicit` arasında kullanılabilir genişletme dönüşümlerini tanımlayan işleç. Daha fazla bilgi için [Örtük Operatör bölümüyle Örtük Dönüşüm bölümüne](#implicit-conversion-with-the-implicit-operator) bakın.  
  
- Türler `Explicit` arasındaki kullanılabilir daralma dönüşümlerini tanımlayan işleç. Daha fazla bilgi için Açık [Operatör bölümüyle Açık Dönüşüm bölümüne](#explicit-conversion-with-the-explicit-operator) bakın.  
  
- Temel <xref:System.IConvertible> .NET Framework veri türlerinin her birine dönüşümleri tanımlayan arabirim. Daha fazla bilgi [için, IConvertible Interface bölümüne](#the-iconvertible-interface) bakın.  
  
- <xref:System.IConvertible> Arabirimdeki <xref:System.Convert> yöntemleri uygulayan bir yöntem kümesi sağlayan sınıf. Daha fazla bilgi için [Sınıfı Dönüştür bölümüne](#the-convert-class) bakın.  
  
- Belirli <xref:System.ComponentModel.TypeConverter> bir türün başka bir türe dönüştürülmesini desteklemek için genişletilebilen bir taban sınıf olan sınıf. Daha fazla bilgi için [TypeConverter Sınıfı bölümüne](#the-typeconverter-class) bakın.  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Örtülü İşleçle Örtülü Dönüştürme  
 Genişletme dönüştürmeleri, varolan bir türün değerinden, hedef türe göre daha kısıtlayıcı bir aralığı veya daha kısıtlayıcı bir üye listesi olan yeni bir değer oluşturmayı gerektirir. Genişletme dönüştürmeleri, (kesinlik kaybıyla sonuçlanabilir olsalar da) veri kaybıyla sonuçlanmaz. Veriler kaybedilemeyeceğinden, derleyiciler, açık bir dönüştürme yöntemi veya bir yayın işleci kullanılmadan, dönüştürmeyi örtülü olarak veya saydam olarak işleyebilir.  
  
> [!NOTE]
> Örtülü bir dönüştürme uygulayan kod bir dönüştürme yöntemi çağırabilir veya bir yayımlama işleci kullanabilir olsa da, örtülü dönüştürmeleri destekleyen derleyiciler tarafından kullanılmaları gerekmez.  
  
 Örneğin, <xref:System.Decimal> tür , , <xref:System.Byte> <xref:System.Char> <xref:System.Int16> <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64> , , ve değerlerden örtülü dönüşümleri destekler. Aşağıdaki örnek, bir <xref:System.Decimal> değişkene değer atamada bu örtük dönüşümlerin bazılarını göstermektedir.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Belirli bir dil derleyicisi özel işleçleri desteklerse, kendi özel türlerinizde de örtülü dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, işaret ve büyüklük gösterimi kullanan `ByteWithSign` imzalı bir byte veri türünün kısmi bir uygulamasını sağlar. Değerlerin ve <xref:System.Byte> <xref:System.SByte> değerlerin örtülü `ByteWithSign` olarak dönüştürülmesini destekler.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 İstemci kodu `ByteWithSign` daha sonra bir <xref:System.Byte> <xref:System.SByte> değişkeni bildirebilir ve aşağıdaki örnekte görüldüğü gibi, herhangi bir açık dönüştürme gerçekleştirmeden veya herhangi bir döküm işleçleri kullanmadan değişkeni ve değerleri atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Açık İşleçli Açık Dönüştürme  
 Dönüştürmeleri daraltma, hedef türden daha geniş bir aralığa veya daha büyük bir üye listesine sahip olan varolan bir türün değerinden yeni bir değer oluşturulmasını gerektirir. Bir daraltma dönüşümü veri kaybıyla sonuçlanabildiğinden, derleyiciler genellikle dönüştürmenin bir dönüştürme yöntemine veya bir yayımlama işlecine yapılan bir çağrı yoluyla açık hale getirilmesini gerektirir. Yani, dönüştürmenin, geliştirici kodunda açıkça işlenmesi gerekir.  
  
> [!NOTE]
> Dönüşümleri daraltmak için bir dönüştürme yöntemi veya döküm operatörü gerektirmesinin temel amacı, geliştiricinin <xref:System.OverflowException> veri kaybı veya kod olarak işlenebilecek bir şekilde bilgi sini sağlamaktır. Ancak, bazı derleyiciler bu gereksinimi ılımlı hale getirebilir. Örneğin, Visual Basic'te `Option Strict` kapalıysa (varsayılan ayarı), Visual Basic derleyicisi dönüşümleri dolaylı olarak daraltmaya çalışır.  
  
 Örneğin, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64> ve veri türleri, aşağıdaki <xref:System.Int32> tabloda gösterdiği gibi, veri türünü aşan aralıkları vardır.  
  
|Tür|Int32 aralığıyla karşılaştırma|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>'den <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyüktür <xref:System.Int64.MinValue?displayProperty=nameWithType> ve (daha büyük bir negatif <xref:System.Int32.MinValue?displayProperty=nameWithType>aralığı vardır) daha azdır.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>'den <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyüktür.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>'den <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyüktür.|  
  
 Bu tür daraltma dönüşümleri işlemek için ,.NET Framework türleri bir `Explicit` işleç tanımlamak için izin verir. Tek tek dil derleyicileri bu işleci kendi sözdizimini <xref:System.Convert> kullanarak uygulayabilir veya dönüştürmeyi gerçekleştirmek için sınıfın bir üyesi çağrılabilir. <xref:System.Convert> (Sınıf hakkında daha fazla bilgi için, bu konuda daha sonra [Sınıf'ı Dönüştür'e](#the-convert-class) bakın.) Aşağıdaki örnekte, bu potansiyel olarak kapsama alanı dışında tamsayı değerlerinin değerlere açık <xref:System.Int32> dönüşümünün işlenmeleri için dil özelliklerinin kullanımı gösterilmektedir.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Açık dönüştürmeler farklı dillerde farklı sonuçlar üretebilir ve bu sonuçlar ilgili <xref:System.Convert> yöntemtarafından döndürülen değerden farklı olabilir. Örneğin, 12.63251 <xref:System.Double> değeri bir <xref:System.Int32>,, hem Visual Basic `CInt` yöntemine hem <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> de .NET Framework yöntemine dönüştürülürse, 13 değerini döndürmek <xref:System.Double> için .03'lük bir değer ini tamamlar, ancak C# `(int)` işleci 12 değerini döndürmek <xref:System.Double> için küçültür. Benzer şekilde, C# `(int)` işleci Boolean-to-tamsayı dönüştürmeyi desteklemez, ancak Visual Basic `CInt` yöntemi -1 değerini `true` dönüştürür. Diğer taraftan, <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> yöntem 1 değerini `true` dönüştürür.  
  
 Derleyicilerin çoğu, açık dönüştürmelerin denetlenen veya denetlenmeyen bir şekilde yapılmasına olanak tanır. Denetlenen bir dönüştürme yapıldığında, <xref:System.OverflowException> dönüştürülecek türün değeri hedef türün aralığının dışında olduğunda bir atma işlemi yapılır. Aynı koşullarda denetlenmeyen bir dönüştürme yapıldığında, dönüştürme bir özel durum oluşturmayabilir, fakat davranış tam olarak tanımsız hale gelir ve sonuç olarak hatalı bir değer oluşabilir.  
  
> [!NOTE]
> C#'da, denetlenen dönüşümler, anahtar `checked` kelimeyi bir döküm operatörüyle birlikte `/checked+` kullanarak veya derleyici seçeneğini belirterek gerçekleştirilebilir. Tam tersine, işaretlenmemiş dönüşümler, anahtar `unchecked` kelimeyi döküm operatörüyle birlikte kullanarak veya `/checked-` derleyici seçeneğini belirterek gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenmez. Visual Basic'te, projenin **Gelişmiş Derleyici Ayarları** iletişim kutusundaki üstbilgi **taşmasını kaldır onay** kutusunu temizleyerek veya `/removeintchecks-` derleyici seçeneğini belirterek denetlenen dönüşümler gerçekleştirilebilir. Tersine, projenin **Gelişmiş Derleyici Ayarları** iletişim kutusunda ki `/removeintchecks+` **tamsayı taşmasını denetle** onay kutusunu seçerek veya derleyici seçeneğini belirterek denetlenmemiş dönüşümler gerçekleştirilebilir. Varsayılan olarak, açık dönüştürmeler denetlenir.  
  
 Aşağıdaki C# örneği, `checked` `unchecked` a <xref:System.Byte> aralığının dışındaki bir değer bir <xref:System.Byte>. Denetlenen dönüştürme bir özel durum atar, ancak denetlenmemiş <xref:System.Byte> dönüştürme değişkene atar. <xref:System.Byte.MaxValue?displayProperty=nameWithType>  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Belirli bir dil derleyicisi özel aşırı yüklü işleçleri desteklerse, kendi özel türlerinizde de açık dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek, işaret ve büyüklük gösterimi kullanan `ByteWithSign` imzalı bir byte veri türünün kısmi bir uygulamasını sağlar. Değerlerin ve <xref:System.Int32> <xref:System.UInt32> değerlerin açık `ByteWithSign` bir şekilde dönüştürülmesini destekler.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 İstemci kodu `ByteWithSign` daha sonra bir <xref:System.Int32> <xref:System.UInt32> değişkeni bildirebilir ve aşağıdaki örnekte görüldüğü gibi, atamalar bir döküm işleci veya dönüştürme yöntemi içeriyorsa, değişkeni ve değerleri atayabilir.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>IConvertible Arabirimi  
 Her türün ortak bir dil çalışma zamanı taban türüne dönüştürülmesini <xref:System.IConvertible> desteklemek için .NET Framework arabirimi sağlar. Uygulama türünün aşağıdakileri sağlaması gerekir:  
  
- Uygulama türünün <xref:System.TypeCode> döndürür yöntemi.  
  
- Uygulama türünü her yaygın dil çalışma zamanı taban<xref:System.Boolean>türüne <xref:System.DateTime> <xref:System.Decimal>(, , <xref:System.Byte>, , , <xref:System.Double>, vb. vb.) dönüştürme yöntemleri.  
  
- Uygulama türünün bir örneğini başka bir belirtilen türe dönüştürmek için genelleştirilmiş bir dönüştürme yöntemi. Desteklenmeyen dönüşümler bir <xref:System.InvalidCastException>.  
  
 Her ortak dil çalışma zamanı taban <xref:System.Boolean>türü <xref:System.Byte> <xref:System.Char>(yani, <xref:System.Double> <xref:System.Int16>, <xref:System.Int32> <xref:System.Int64>, <xref:System.SByte> <xref:System.DateTime> <xref:System.Single>, <xref:System.String> <xref:System.UInt16> <xref:System.Decimal>, <xref:System.UInt32>, <xref:System.UInt64>, , <xref:System.DBNull> , <xref:System.Enum> , , <xref:System.IConvertible> , , , ve ), yanı sıra ve türleri, arabirimi uygulamak. Ancak, bunlar açık arabirim uygulamalarıdır; dönüştürme yöntemi, aşağıdaki örnekte <xref:System.IConvertible> görüldüğü gibi yalnızca bir arabirim değişkeni üzerinden çağrılabilir. Bu örnek, <xref:System.Int32> bir değeri <xref:System.Char> eşdeğer değerine dönüştürür.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Dönüştürme yöntemini, uygulama türünde değil, kendi arabiriminde çağırma gereksinimi, açık arabirim uygulamalarını görece pahalılaştırır. Bunun yerine, ortak dil çalışma zamanı <xref:System.Convert> taban türleri arasında dönüştürmek için sınıfın uygun üyesini aramanızı öneririz. Daha fazla bilgi için, sonraki bölüme bakın, [Sınıf dönüştür](#the-convert-class).  
  
> [!NOTE]
> <xref:System.IConvertible> .NET Framework tarafından <xref:System.Convert> sağlanan arabirim ve sınıfa ek olarak, tek tek diller de dönüşüm gerçekleştirmenin yollarını sağlayabilir. Örneğin, C# döküm operatörleri kullanır; Visual Basic derleyici tarafından uygulanan dönüşüm `CType` `CInt`işlevlerini `DirectCast`kullanır, , ve .  
  
 <xref:System.IConvertible> Arabirim çoğunlukla .NET Framework'deki temel türler arasındaki dönüşümü desteklemek üzere tasarlanmıştır. Ancak, arabirim, o türün diğer özel türlere dönüştürülmesini desteklemek için özel bir tür tarafından da uygulanabilir. Daha fazla bilgi için, bu konuda daha sonra [ChangeType Yöntemi ile Özel Dönüşümler](#custom-conversions-with-the-changetype-method) bölümüne bakın.

## <a name="the-convert-class"></a>Dönüştürme Sınıfı
 Her temel türün <xref:System.IConvertible> arabirimi uygulaması bir tür dönüştürme gerçekleştirmek için <xref:System.Convert?displayProperty=nameWithType> çağrılabilir, ancak sınıfın yöntemlerini çağırmak, bir temel türden diğerine dönüştürmenin önerilen dilden bağımsız yoludur. Ayrıca, <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntem belirli bir özel türden başka bir türe dönüştürmek için kullanılabilir.  
  
### <a name="conversions-between-base-types"></a>Temel Türler Arasında Dönüştürme  
 Sınıf, <xref:System.Convert> temel türler arasında dönüşüm gerçekleştirmek için dilden bağımsız bir yol sağlar ve ortak dil çalışma zamanını hedefleyen tüm dilleriçin kullanılabilir. Hem genişletme hem de daraltma dönüşümleri için tam bir yöntem <xref:System.InvalidCastException> kümesi sağlar ve desteklenmeyen dönüşümler için <xref:System.DateTime> (örneğin, bir değerin tamsayı değerine dönüştürülmesi gibi) bir yöntem kümesi atar. Denetimli bir bağlamda dönüştürmeleri daraltma <xref:System.OverflowException> gerçekleştirilir ve dönüşüm başarısız olursa bir atılmıştır.  
  
> [!IMPORTANT]
> <xref:System.Convert> Sınıf, her temel türe dönüştürme yöntemleri içerdiğinden, her temel türün <xref:System.IConvertible> açık arabirimi uygulamasını çağırma gereksinimini ortadan kaldırır.  
  
 Aşağıdaki örnekte, <xref:System.Convert?displayProperty=nameWithType> .NET Framework taban türleri arasında birkaç genişletme ve daraltma dönüşümleri gerçekleştirmek için sınıfın kullanımı gösteriş verilmiştir.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 Bazı durumlarda, özellikle kayan nokta değerlerine dönüştürüldüğünde, bir dönüştürme, <xref:System.OverflowException>bir . Aşağıdaki örnekte bu kesinlik kaybı gösterilmektedir. İlk durumda, bir <xref:System.Decimal> değer , <xref:System.Double>bir . dönüştürüldüğünde daha az kesinlik (daha az önemli basamak) vardır İkinci durumda, dönüştürmeyi tamamlamak için bir <xref:System.Double> değer 42,72'den 43'e yuvarlanır.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 <xref:System.Convert> Sınıf tarafından desteklenen hem genişletme hem de daraltma dönüşümlerini listeleyen bir tablo için, Dönüşüm Tabloları [Yazın'a](../../../docs/standard/base-types/conversion-tables.md)bakın.  

### <a name="custom-conversions-with-the-changetype-method"></a>ChangeType Yöntemiyle Özel Dönüştürmeler  
 Temel türlerin her birine dönüşümleri desteklemenin yanı <xref:System.Convert> sıra, sınıf özel bir türü bir veya daha fazla önceden tanımlanmış türe dönüştürmek için kullanılabilir. Bu dönüştürme, <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> `value` parametre yöntemine bir çağrı yıkıyor yöntemi ile gerçekleştirilir. Bu, `value` parametre tarafından temsil edilen nesnenin <xref:System.IConvertible> arabirimin uygulanmasını sağlaması gerektiği anlamına gelir.  
  
> [!NOTE]
> Ve <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemler dönüştürülen <xref:System.Type> hedef türünü belirtmek için `value` bir nesne kullandığından, derleme zamanında türü bilinmeyen bir nesneye dinamik dönüştürme gerçekleştirmek için kullanılabilirler. Ancak, uygulama <xref:System.IConvertible> nın `value` yine de bu dönüşümü desteklemesi gerektiğini unutmayın.  
  
 Aşağıdaki örnek, bir <xref:System.IConvertible> `TemperatureCelsius` nesnenin bir nesneye dönüştürülmesine izin veren `TemperatureFahrenheit` arabirimin olası bir uygulamasını göstermektedir ve bunun tersi de mümkündür. Örnek, `Temperature` <xref:System.IConvertible> arabirimi uygulayan ve <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi geçersiz kılan bir taban sınıf tanımlar. `TemperatureCelsius` Türemiş `TemperatureFahrenheit` ve sınıfların `ToType` her `ToString` biri taban sınıfın yöntemlerini ve yöntemlerini geçersiz kılar.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Aşağıdaki örnek, nesneleri <xref:System.IConvertible> `TemperatureCelsius` `TemperatureFahrenheit` nesnelere dönüştürmek için bu uygulamalara yapılan birkaç çağrıyı ve bunun tam tersini göstermektedir.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>TypeConverter Sınıfı  
 .NET Framework ayrıca <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> sınıfı genişleterek ve tür dönüştürücüsü bir <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> öznitelik aracılığıyla türle ilişkilendirerek özel bir tür için bir tür dönüştürücü tanımlamanızı sağlar. Aşağıdaki tablo, bu yaklaşım ve özel bir <xref:System.IConvertible> tür için arabirim uygulama arasındaki farkları vurgulamaktadır.  
  
> [!NOTE]
> Tasarım zamanı desteği, yalnızca kendisi için tanımlanmış bir tür dönüştürücüsü varsa, özel bir tür için sağlanabilir.  
  
|TypeConverter kullanılarak dönüştürme|IConvertible kullanılarak dönüştürme|  
|------------------------------------|-----------------------------------|  
|Ayrı bir sınıf türetilerek özel bir tür <xref:System.ComponentModel.TypeConverter>için uygulanır. Bu türemiş sınıf bir <xref:System.ComponentModel.TypeConverterAttribute> öznitelik uygulayarak özel türü ile ilişkilidir.|Dönüştürme yapmak için özel bir tür tarafından uygulanır. Türdeki bir kullanıcı, <xref:System.IConvertible> türüzerinde bir dönüştürme yöntemi çağırır.|  
|Hem tasarım zamanında hem de çalışma zamanında kullanılabilir.|Yalnızca çalışma zamanında kullanılabilir.|  
|Yansıma kullanır; bu nedenle, dönüşüm tarafından <xref:System.IConvertible>etkin daha yavaştır.|Yansıma kullanmaz.|  
|özel türden diğer veri türlerine ve diğer veri türlerinden özel türe olmak üzere, iki yönlü tür dönüştürmelerine olanak tanır. Örneğin, tanımlanan <xref:System.ComponentModel.TypeConverter> bir `MyType` için `MyType` dönüşümler <xref:System.String>sağlar <xref:System.String> , `MyType`ve için .|Özel bir türden diğer veri türlerine dönüştürmeye olanak tanır, fakat diğer veri türlerinden özel türe dönüştürmeye olanak tanımaz.|  
  
 Dönüşümleri gerçekleştirmek için tür dönüştürücüleri kullanma <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>hakkında daha fazla bilgi için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tür Dönüştürme Tabloları](../../../docs/standard/base-types/conversion-tables.md)
