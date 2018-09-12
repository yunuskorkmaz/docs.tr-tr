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
ms.openlocfilehash: 2d039e591e1f61a7be18dc224845f82b107d918f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699952"
---
# <a name="type-conversion-in-the-net-framework"></a>.NET Framework'te Tür Dönüştürme
<a name="top"></a> Her değerin değere, sahip olabileceği olası değerler aralığı ayrılan alan miktarını gibi öznitelikleri tanımlayan ilişkili bir türü vardır ve onun üyeleri kullanılabilir hale getirir. Birçok değer, tek bir türden fazlası olarak ifade edilebilir. Örneğin, 4 değeri bir tamsayı olarak veya bir kayan nokta değeri olarak ifade edilebilir. Tür dönüştürme, eski bir türün değerine eşit olan, yeni türde bir değer oluşturur, fakat özgün nesnenin kimliğini (veya tam değerini) koruması gerekmez.  
  
 .NET Framework, aşağıdaki dönüştürmeleri otomatik olarak destekler:  
  
-   Bir temel sınıf dönüştürme türetilmiş sınıf. Bu, örneğin, herhangi bir sınıf veya yapının örneği için dönüştürülebilir anlamına gelir bir <xref:System.Object> örneği.  Bu dönüştürme atama veya dönüştürme işleci gerektirmez.  
  
-   Bir taban sınıftan dönüştürme özgün türetilmiş sınıfa yedekleyin. C# ' ta bu dönüştürme atama işleci gerektirir. Visual Basic'te gerektiren `CType` işleci, `Option Strict` açıktır.  
  
-   Bu arabirimi temsil eden bir arabirim nesne için bir arabirimi uygulayan bir tür dönüştürme. Bu dönüştürme atama veya dönüştürme işleci gerektirmez.  
  
-   Arabirimi nesneden bir arabirimi uygulayan yeniden orijinal türüne dönüştürme.  C# ' ta bu dönüştürme atama işleci gerektirir. Visual Basic'te gerektiren `CType` işleci, `Option Strict` açıktır.  
  
 Otomatik dönüştürmeler yanı sıra [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] özel tür dönüştürmeyi destekleyen çeşitli özellikler sağlar. Bunlar aşağıdakileri içerir:  
  
-   `Implicit` Türleri arasında kullanılabilir genişletme dönüştürmelerini tanımlayan işleci. Daha fazla bilgi için [işleçle örtülü dönüştürme](#implicit_conversion_with_the_implicit_operator) bölümü.  
  
-   `Explicit` Türler arasında kullanılabilir daraltma dönüştürmelerini tanımlayan işleci. Daha fazla bilgi için [açık işleçli açık dönüştürme](#explicit_conversion_with_the_explicit_operator) bölümü.  
  
-   <xref:System.IConvertible> Temel .NET Framework veri türlerinin her biri için dönüştürmelerini tanımlayan arabirimi. Daha fazla bilgi için [IConvertible arabirimi](#the_iconvertible_interface) bölümü.  
  
-   <xref:System.Convert> Yöntemleri uygulayan yöntemler kümesi sağlar sınıfını <xref:System.IConvertible> arabirimi. Daha fazla bilgi için [dönüştürme sınıfı](#Convert) bölümü.  
  
-   <xref:System.ComponentModel.TypeConverter> Belirtilen bir türün herhangi bir tür dönüştürme desteklemek için genişletilebilen bir temel sınıf olan sınıf. Daha fazla bilgi için [TypeConverter sınıfı](#the_typeconverter_class) bölümü.  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Örtülü İşleçle Örtülü Dönüştürme  
 Genişletme dönüştürmeleri, varolan bir türün değerinden, hedef türe göre daha kısıtlayıcı bir aralığı veya daha kısıtlayıcı bir üye listesi olan yeni bir değer oluşturmayı gerektirir. Genişletme dönüştürmeleri, (kesinlik kaybıyla sonuçlanabilir olsalar da) veri kaybıyla sonuçlanmaz. Veriler kaybedilemeyeceğinden, derleyiciler, açık bir dönüştürme yöntemi veya bir yayın işleci kullanılmadan, dönüştürmeyi örtülü olarak veya saydam olarak işleyebilir.  
  
> [!NOTE]
>  Örtülü bir dönüştürme uygulayan kod bir dönüştürme yöntemi çağırabilir veya bir yayımlama işleci kullanabilir olsa da, örtülü dönüştürmeleri destekleyen derleyiciler tarafından kullanılmaları gerekmez.  
  
 Örneğin, <xref:System.Decimal> türüne örtük dönüşümlere destekler <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>, ve <xref:System.UInt64> değerleri. Aşağıdaki örnekte, değerler atamada bu örtülü dönüştürmelerin bazıları gösterilmektedir bir <xref:System.Decimal> değişkeni.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Belirli bir dil derleyicisi özel işleçleri desteklerse, kendi özel türlerinizde de örtülü dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnekte adlı bir işaretli bayt veri türünün kısmi bir uygulamasını sağlar `ByteWithSign` işaret ve büyüklük gösterimi kullanan. Örtülü dönüşümünü destekler <xref:System.Byte> ve <xref:System.SByte> değerler `ByteWithSign` değerleri.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 İstemci kodu daha sonra bildirebilirsiniz bir `ByteWithSign` değişkeni ve atayın <xref:System.Byte> ve <xref:System.SByte> olmadan açık dönüştürmeler yapmadan veya işleçler kullanarak aşağıdaki örnekte gösterildiği gibi değerleri.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Başa dön](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Açık İşleçli Açık Dönüştürme  
 Dönüştürmeleri daraltma, hedef türden daha geniş bir aralığa veya daha büyük bir üye listesine sahip olan varolan bir türün değerinden yeni bir değer oluşturulmasını gerektirir. Bir daraltma dönüşümü veri kaybıyla sonuçlanabildiğinden, derleyiciler genellikle dönüştürmenin bir dönüştürme yöntemine veya bir yayımlama işlecine yapılan bir çağrı yoluyla açık hale getirilmesini gerektirir. Yani, dönüştürmenin, geliştirici kodunda açıkça işlenmesi gerekir.  
  
> [!NOTE]
>  Daraltma dönüştürmeleri Geliştirici geliştiriciyi veri kaybı sağlamak için bir dönüştürme yöntemi veya yayımlama işlecinin gerekli ana amacı veya <xref:System.OverflowException> böylece kodda işlenebilir. Ancak, bazı derleyiciler bu gereksinimi ılımlı hale getirebilir. Örneğin, Visual Basic, eğer içinde `Option Strict` olduğunu (varsayılan ayar devre dışı), Visual Basic Derleyicisi daraltma dönüştürmelerini örtülü olarak dener.  
  
 Örneğin, <xref:System.UInt32>, <xref:System.Int64>, ve <xref:System.UInt64> veri türlerine sahip aşan aralıklara <xref:System.Int32> aşağıdaki tabloda gösterildiği gibi veri türü.  
  
|Tür|Int32 aralığıyla karşılaştırma|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> büyüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType>, ve <xref:System.Int64.MinValue?displayProperty=nameWithType> küçüktür (eksi aralığı daha büyüktür daha vardır) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType> büyüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType> büyüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Bu tür daraltma dönüştürmelerini işlemek için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] türleri tanımlamak sağlayan bir `Explicit` işleci. Bireysel dil derleyicileri daha sonra kendi sözdizimlerini veya üyesi kullanarak bu işleci uygulamak <xref:System.Convert> sınıf dönüştürme yapmak için çağrılabilir. (Hakkında daha fazla bilgi için <xref:System.Convert> sınıfı [dönüştürme sınıfı](#Convert) bu konunun devamındaki.) Bu çıkış aralık büyük olasılıkla tam sayı değerlerine açıkça dönüştürülmesini işlemek için dil özelliklerinin kullanımı aşağıdaki örnekte <xref:System.Int32> değerleri.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Açık dönüştürmeler farklı dillerde farklı sonuçlar üretebilir ve bu sonuçlar ilgili tarafından döndürülen değer farklı olabilir <xref:System.Convert> yöntemi. Örneğin, varsa <xref:System.Double> değerinin 12.63251 bir <xref:System.Int32>, hem Visual Basic `CInt` yöntemi ve .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> round yöntemi <xref:System.Double> 13, ancak C# değerini döndürmek için `(int)` işleci keser <xref:System.Double> 12 değerini döndürmek için. Benzer şekilde, C# `(int)` işleç Boole boolean'dan tamsayıya dönüştürmeyi, ancak Visual Basic desteklemiyor `CInt` yöntemi değerini dönüştürür `true` -1. Öte yandan, <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> yöntemi değerini dönüştürür `true` 1.  
  
 Derleyicilerin çoğu, açık dönüştürmelerin denetlenen veya denetlenmeyen bir şekilde yapılmasına olanak tanır. Denetlenen bir dönüştürme yapıldığında, bir <xref:System.OverflowException> dönüştürülecek türün değeri hedef türün aralığı dışında olduğunda oluşturulur. Aynı koşullarda denetlenmeyen bir dönüştürme yapıldığında, dönüştürme bir özel durum oluşturmayabilir, fakat davranış tam olarak tanımsız hale gelir ve sonuç olarak hatalı bir değer oluşabilir.  
  
> [!NOTE]
>  İşaretli C# ' ta dönüştürmeleri kullanarak gerçekleştirilebilir `checked` anahtar sözcüğü bir yayım işleciyle birlikte veya belirterek `/checked+` derleyici seçeneği. Buna karşılık, denetlenmeyen dönüştürmeler kullanarak gerçekleştirilebilir `unchecked` anahtar sözcüğü yayım işleciyle birlikte veya belirterek `/checked-` derleyici seçeneği. Varsayılan olarak, açık dönüştürmeler denetlenmez. Visual Basic'te temizleyerek dönüştürmeler uygulanabilir işaretli **tamsayı taşması denetimlerini Kaldır** projenin onay kutusuna **Gelişmiş derleyici ayarları** iletişim kutusu veya belirterek`/removeintchecks-`derleyici seçeneği. Buna karşılık, denetlenmeyen dönüştürmeler seçerek gerçekleştirilebilir **tamsayı taşması denetimlerini Kaldır** projenin onay kutusuna **Gelişmiş derleyici ayarları** iletişim kutusu veya belirterek`/removeintchecks+`derleyici seçeneği. Varsayılan olarak, açık dönüştürmeler denetlenir.  
  
 Aşağıdaki C# örneği kullanan `checked` ve `unchecked` değeri zaman aralığının dışında davranıştaki farkı göstermek için anahtar sözcükler bir <xref:System.Byte> dönüştürülür bir <xref:System.Byte>. Denetlenen dönüştürmeler bir özel durum oluşturur, fakat denetlenmeyen dönüştürmeler atar <xref:System.Byte.MaxValue?displayProperty=nameWithType> için <xref:System.Byte> değişkeni.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Belirli bir dil derleyicisi özel aşırı yüklü işleçleri desteklerse, kendi özel türlerinizde de açık dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnekte adlı bir işaretli bayt veri türünün kısmi bir uygulamasını sağlar `ByteWithSign` işaret ve büyüklük gösterimi kullanan. Açıkça dönüştürülmesini destekler <xref:System.Int32> ve <xref:System.UInt32> değerler `ByteWithSign` değerleri.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 İstemci kodu daha sonra bildirebilirsiniz bir `ByteWithSign` değişkeni ve atayın <xref:System.Int32> ve <xref:System.UInt32> atamaları aşağıdaki örnekte gösterildiği gibi bir yayım işleci veya bir dönüştürme yöntemi içeriyorsa değerleri.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Başa dön](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>IConvertible Arabirimi  
 Bir ortak dil çalışma zamanı temel türüne, herhangi bir tür dönüştürme desteklemek için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sağlar <xref:System.IConvertible> arabirimi. Uygulama türünün aşağıdakileri sağlaması gerekir:  
  
-   Döndüren bir yöntem <xref:System.TypeCode> uygulama türü.  
  
-   Her ortak dil çalışma zamanı temel türüne için uygulama dönüştürme yöntemleri yazın (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, vb.).  
  
-   Uygulama türünün bir örneğini başka bir belirtilen türe dönüştürmek için genelleştirilmiş bir dönüştürme yöntemi. Desteklenmeyen dönüştürmeler throw bir <xref:System.InvalidCastException>.  
  
 Her ortak dil çalışma zamanı temel türüne (diğer bir deyişle, <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>, ve <xref:System.UInt64>), hem de <xref:System.DBNull> ve <xref:System.Enum> türleri uygulayan <xref:System.IConvertible> arabirimi. Ancak, bunlar açık arabirim uygulamalarıdır; dönüştürme yöntemi yalnızca yoluyla çağrılabilir bir <xref:System.IConvertible> aşağıdaki örnekte gösterildiği gibi arabirim değişkeni. Bu örnek bir <xref:System.Int32> değerini onun dengi <xref:System.Char> değeri.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Dönüştürme yöntemini, uygulama türünde değil, kendi arabiriminde çağırma gereksinimi, açık arabirim uygulamalarını görece pahalılaştırır. Bunun yerine, uygun üyesini çağırmanızı öneririz <xref:System.Convert> ortak dil çalışma zamanı temel türleri arasında dönüştürme için sınıf. Daha fazla bilgi için sonraki bölüme bakın [dönüştürme sınıfı](#Convert).  
  
> [!NOTE]
>  Ek olarak <xref:System.IConvertible> arabirimi ve <xref:System.Convert> sınıfı tarafından sağlanan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], bireysel diller de dönüştürmeleri uygulamak için yollar sağlayabilir. Örneğin, C# atama işleçleri kullanır; Visual Basic derleyici tarafından uygulanan dönüştürme işlevlerini gibi kullanır `CType`, `CInt`, ve `DirectCast`.  
  
 Çoğunlukla, <xref:System.IConvertible> arabirimi içinde temel türler arasında dönüştürmeyi desteklemek için tasarlanan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Ancak, arabirim, o türün diğer özel türlere dönüştürülmesini desteklemek için özel bir tür tarafından da uygulanabilir. Daha fazla bilgi için konudaki [ChangeType yöntemiyle özel dönüştürmeler](#ChangeType) bu konuda.  
  
 [Başa dön](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Dönüştürme Sınıfı  
 Ancak her bir temel türün <xref:System.IConvertible> arabirim uygulaması yöntemlerini çağırmak bir tür dönüştürmesi yapmak için çağrılabilir <xref:System.Convert?displayProperty=nameWithType> sınıfı, bir temel türden diğerine dönüştürün için önerilen dilden bağımsız yoldur. Ayrıca, <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi, belirtilen bir özel türden başka bir türe dönüştürmek için kullanılabilir.  
  
### <a name="conversions-between-base-types"></a>Temel Türler Arasında Dönüştürme  
 <xref:System.Convert> Sınıfı, temel türler arasında dönüştürmeler gerçekleştirmek için dilden bağımsız bir yol sağlar ve ortak dil çalışma zamanını hedefleyen tüm diller için kullanılabilir. Hem genişletme ve daraltma dönüştürmeleri için tam bir yöntemler kümesi sağlar ve oluşturur bir <xref:System.InvalidCastException> desteklenmeyen dönüştürmeler için (dönüştürme gibi bir <xref:System.DateTime> değeri bir tamsayı değerine). Daraltma dönüştürmeleri denetlenen bir bağlamda gerçekleştirilir ve <xref:System.OverflowException> dönüştürme başarısız olursa oluşturulur.  
  
> [!IMPORTANT]
>  Çünkü <xref:System.Convert> sınıfı için ve her bir temel türe dönüştürme yapma yöntemleri içerir, her bir temel türün çağırma ihtiyacını ortadan <xref:System.IConvertible> açık arabirim uygulaması.  
  
 Aşağıdaki örnek, kullanımını gösterir <xref:System.Convert?displayProperty=nameWithType> çeşitli genişlete ve daraltma .NET Framework türleri arasında dönüştürmeler gerçekleştirmek için sınıf.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 Bazı durumlarda, özellikle ve kayan nokta değerlerine dönüştürme yaparken olsa da oluşturmaz kesinlik kaybı bir dönüştürme gerektirebilir bir <xref:System.OverflowException>. Aşağıdaki örnekte bu kesinlik kaybı gösterilmektedir. İlk durumda, bir <xref:System.Decimal> değerinin kesinliği (daha az önemli basamak) için dönüştürüldüğünde bir <xref:System.Double>. İkinci durumda, bir <xref:System.Double> değer yuvarlanır 42.72 43 için Dönüştürmeyi tamamlamak.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Genişletme ve daraltma dönüşümleri tarafından desteklenen listeleyen bir tablo için <xref:System.Convert> sınıfı [tür dönüştürme tabloları](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>ChangeType Yöntemiyle Özel Dönüştürmeler  
 Her temel türlerin birine yapılan dönüştürmeleri destekleyen yanı sıra <xref:System.Convert> sınıfı, bir özel tür bir veya daha fazla önceden tanımlı türe dönüştürmek için kullanılabilir. Bu dönüştürme tarafından gerçekleştirilen <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> sırayla bir çağrı sarılır yöntemi <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> yöntemi `value` parametresi. Tarafından temsil edilen nesnenin buna `value` parametresi bir uygulamasını sağlaması <xref:System.IConvertible> arabirimi.  
  
> [!NOTE]
>  Çünkü <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> ve <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemlerini kullanma bir <xref:System.Type> hedef türü belirtmek için nesne `value` olan dönüştürüldüğü türü değil derleme zamanında bilinen bir nesneye dinamik dönüştürme yapmak için kullanılabilirler. Ancak, unutmayın <xref:System.IConvertible> uygulaması `value` hala bu dönüştürmeyi desteklemesi gerekir.  
  
 Aşağıdaki örnekte, olası bir uygulaması gösterilmektedir <xref:System.IConvertible> arabirimi bir `TemperatureCelsius` dönüştürülecek nesne bir `TemperatureFahrenheit` nesne geçme veya tam tersi. Örnek, bir temel sınıf tanımlar `Temperature`, uygulayan <xref:System.IConvertible> arabirimi ve geçersiz kılmalar <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi. Türetilmiş `TemperatureCelsius` ve `TemperatureFahrenheit` her bir geçersiz kılma sınıfları `ToType` ve `ToString` temel sınıf yöntemleri.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Aşağıdaki örnekte, bunları çeşitli çağrılar gösterilmektedir <xref:System.IConvertible> dönüştürmek `TemperatureCelsius` nesneleri için `TemperatureFahrenheit` nesneleri ve bunun tersi de geçerlidir.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Başa dön](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>TypeConverter Sınıfı  
 .NET Framework ayrıca genişleterek bir özel tür için bir tür dönüştürücüsü tanımlamanıza olanak sağlayan <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> sınıfı ve tür dönüştürücüsünü yoluyla türle ilişkilendirerek bir <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> özniteliği. Aşağıdaki tabloda, bu yaklaşım arasındaki farklar vurgulanmaktadır ve uygulama <xref:System.IConvertible> özel bir tür için arabirim.  
  
> [!NOTE]
>  Tasarım zamanı desteği, yalnızca kendisi için tanımlanmış bir tür dönüştürücüsü varsa, özel bir tür için sağlanabilir.  
  
|TypeConverter kullanılarak dönüştürme|IConvertible kullanılarak dönüştürme|  
|------------------------------------|-----------------------------------|  
|Özel bir tür için ayrı bir sınıftan türetme tarafından uygulanan <xref:System.ComponentModel.TypeConverter>. Bu türetilmiş bir sınıf uygulayarak özel türle ilişkilendirilir bir <xref:System.ComponentModel.TypeConverterAttribute> özniteliği.|Dönüştürme yapmak için özel bir tür tarafından uygulanır. Bir kullanıcı türü çağıran bir <xref:System.IConvertible> türüne dönüştürme yöntemi.|  
|Hem tasarım zamanında hem de çalışma zamanında kullanılabilir.|Yalnızca çalışma zamanında kullanılabilir.|  
|Yansıma kullanır; Bu nedenle, tarafından etkinleştirilen dönüştürmeden daha yavaştır <xref:System.IConvertible>.|Yansıma kullanmaz.|  
|özel türden diğer veri türlerine ve diğer veri türlerinden özel türe olmak üzere, iki yönlü tür dönüştürmelerine olanak tanır. Örneğin, bir <xref:System.ComponentModel.TypeConverter> için tanımlanan `MyType` Dönüştürmelere olanak tanır `MyType` için <xref:System.String>, gelen ve giden <xref:System.String> için `MyType`.|Özel bir türden diğer veri türlerine dönüştürmeye olanak tanır, fakat diğer veri türlerinden özel türe dönüştürmeye olanak tanımaz.|  
  
 Dönüştürmeler gerçekleştirmek için tür dönüştürücüleri kullanma hakkında daha fazla bilgi için bkz. <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert?displayProperty=nameWithType>  
- <xref:System.IConvertible>  
- [Tür Dönüştürme Tabloları](../../../docs/standard/base-types/conversion-tables.md)
