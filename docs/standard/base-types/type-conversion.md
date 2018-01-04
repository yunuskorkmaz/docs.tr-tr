---
title: ".NET Framework'te Tür Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 643a1c7d8dd141a8d898af61ba8302f46207321b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="type-conversion-in-the-net-framework"></a>.NET Framework'te Tür Dönüştürme
<a name="top"></a>Değerine sahip olabilir, olası değerleri aralığı ayrılmış alanı miktarı gibi öznitelikleri tanımlar bir ilişkili türü, her bir değeri yok ve üyeleri olan kullanılabilir hale getirir. Birçok değer, tek bir türden fazlası olarak ifade edilebilir. Örneğin, 4 değeri bir tamsayı olarak veya bir kayan nokta değeri olarak ifade edilebilir. Tür dönüştürme, eski bir türün değerine eşit olan, yeni türde bir değer oluşturur, fakat özgün nesnenin kimliğini (veya tam değerini) koruması gerekmez.  
  
 .NET Framework otomatik olarak aşağıdaki dönüşümleri destekler:  
  
-   Türetilmiş bir sınıf dönüştürme için bir temel sınıf. Bu, örneğin, herhangi bir sınıf veya yapı örneği için dönüştürülebilir anlamına gelir bir <xref:System.Object> örneği.  Bu dönüştürme atama veya dönüştürme işleci gerektirmez.  
  
-   Dönüştürme temel sınıfından geri özgün türetilmiş sınıf. C# ' ta atama işleci bu dönüştürme gerektirir. Visual Basic'te gerektirdiği `CType` işleci varsa `Option Strict` açıktır.  
  
-   Bu arabirim temsil eden bir arabirim nesnesi için bir arabirimi uygulayan bir tür dönüştürme. Bu dönüştürme atama veya dönüştürme işleci gerektirmez.  
  
-   Bir arabirim nesneden arabirimi uygulayan geri özgün türüne dönüştürme.  C# ' ta atama işleci bu dönüştürme gerektirir. Visual Basic'te gerektirdiği `CType` işleci varsa `Option Strict` açıktır.  
  
 Bu otomatik dönüşümler yanı sıra [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] özel tür dönüştürme desteği çeşitli özellikler sunar. Bunlar aşağıdakileri içerir:  
  
-   `Implicit` Türleri arasında kullanılabilir genişletme dönüşümler tanımlar işleci. Daha fazla bilgi için bkz: [Implicit işleci örtük dönüştürmeye](#implicit_conversion_with_the_implicit_operator) bölümü.  
  
-   `Explicit` Türleri arasında kullanılabilir daraltma dönüşümleri tanımlar işleci. Daha fazla bilgi için bkz: [açık işleciyle açık dönüşüm](#explicit_conversion_with_the_explicit_operator) bölümü.  
  
-   <xref:System.IConvertible> Dönüştürmeleri temel .NET Framework veri türlerinin her biri için tanımlar arabirimi. Daha fazla bilgi için bkz: [IConvertible arabirimi](#the_iconvertible_interface) bölümü.  
  
-   <xref:System.Convert> Yöntemleri uygulamak yöntemler kümesi sağlar sınıfı <xref:System.IConvertible> arabirimi. Daha fazla bilgi için bkz:[Dönüştür sınıfı](#Convert) bölümü.  
  
-   <xref:System.ComponentModel.TypeConverter> Herhangi bir türü belirtilen bir türün dönüştürme desteklemek için genişletilmiş bir taban sınıf sınıfı. Daha fazla bilgi için bkz: [Typeconverter'a sınıfı](#the_typeconverter_class) bölümü.  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Örtülü İşleçle Örtülü Dönüştürme  
 Genişletme dönüştürmeleri, varolan bir türün değerinden, hedef türe göre daha kısıtlayıcı bir aralığı veya daha kısıtlayıcı bir üye listesi olan yeni bir değer oluşturmayı gerektirir. Genişletme dönüştürmeleri, (kesinlik kaybıyla sonuçlanabilir olsalar da) veri kaybıyla sonuçlanmaz. Veriler kaybedilemeyeceğinden, derleyiciler, açık bir dönüştürme yöntemi veya bir yayın işleci kullanılmadan, dönüştürmeyi örtülü olarak veya saydam olarak işleyebilir.  
  
> [!NOTE]
>  Örtülü bir dönüştürme uygulayan kod bir dönüştürme yöntemi çağırabilir veya bir yayımlama işleci kullanabilir olsa da, örtülü dönüştürmeleri destekleyen derleyiciler tarafından kullanılmaları gerekmez.  
  
 Örneğin, <xref:System.Decimal> türünü destekler gelen örtük dönüşümler <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>, ve <xref:System.UInt64> değerleri. Aşağıdaki örnek değerleri atanmasında bu örtük dönüşümler bazıları gösterilmektedir bir <xref:System.Decimal> değişkeni.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Belirli bir dil derleyicisi özel işleçleri desteklerse, kendi özel türlerinizde de örtülü dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek adlı imzalı byte veri türü kısmi bir uygulamasını sağlar `ByteWithSign` oturum büyüklük gösterimini kullanır. Örtük dönüşümünü destekleyen <xref:System.Byte> ve <xref:System.SByte> değerler `ByteWithSign` değerleri.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 İstemci kodu sonra bildirebilirsiniz bir `ByteWithSign` değişkeni ve atayın <xref:System.Byte> ve <xref:System.SByte> açık bir dönüştürme gerçekleştirmek veya aşağıdaki örnekte gösterildiği gibi tüm atama işleçleri kullanarak olmadan değerleri.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Başa dön](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Açık İşleçli Açık Dönüştürme  
 Dönüştürmeleri daraltma, hedef türden daha geniş bir aralığa veya daha büyük bir üye listesine sahip olan varolan bir türün değerinden yeni bir değer oluşturulmasını gerektirir. Bir daraltma dönüşümü veri kaybıyla sonuçlanabildiğinden, derleyiciler genellikle dönüştürmenin bir dönüştürme yöntemine veya bir yayımlama işlecine yapılan bir çağrı yoluyla açık hale getirilmesini gerektirir. Yani, dönüştürmenin, geliştirici kodunda açıkça işlenmesi gerekir.  
  
> [!NOTE]
>  Daraltma dönüşümleri Geliştirici veri kaybı olasılığı haberdar olmak için dönüştürme yöntemini veya atama işleci gerektiren ana amacı veya bir <xref:System.OverflowException> böylece kodu işlenebilir. Ancak, bazı derleyiciler bu gereksinimi ılımlı hale getirebilir. Örneğin, Visual Basic, eğer içinde `Option Strict` olduğu (kendi varsayılan ayarı kapalı), Visual Basic derleyici daraltma dönüşümleri örtük olarak gerçekleştirmek dener.  
  
 Örneğin, <xref:System.UInt32>, <xref:System.Int64>, ve <xref:System.UInt64> veri türlerine sahip, aşan aralıkları <xref:System.Int32> aşağıdaki tabloda gösterildiği gibi veri türü.  
  
|Tür|Int32 aralığıyla karşılaştırma|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>Daha fazla <xref:System.Int32.MaxValue?displayProperty=nameWithType>, ve <xref:System.Int64.MinValue?displayProperty=nameWithType> küçüktür (büyük negatif aralığından daha vardır) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>Daha fazla <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>Daha fazla <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Bu tür daraltma dönüşümleri işlemek için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tanımlamak türlerine izin verir bir `Explicit` işleci. Ayrı dil derleyicileri sonra kendi söz dizimi ya da bir üyesi kullanarak bu işleci uygulamak <xref:System.Convert> sınıfı, dönüştürme gerçekleştirmek için çağrılabilir. (Hakkında daha fazla bilgi için <xref:System.Convert> sınıfı için bkz: [Dönüştür sınıfı](#Convert) bu konunun devamındaki.) Aşağıdaki örnekte bu büyük olasılıkla çıkış aralığın tamsayı değerleri açık dönüştürme işlemek için dile özellikleri kullanımını göstermektedir <xref:System.Int32> değerleri.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Açık dönüşümler farklı dillerde farklı sonuçlar üretir ve bu sonuçları karşılık gelen tarafından döndürülen değer farklı olabilir <xref:System.Convert> yöntemi. Örneğin, varsa <xref:System.Double> değeri 12.63251 dönüştürülür bir <xref:System.Int32>, Visual Basic `CInt` yöntemi ve .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> yöntemi yuvarlak <xref:System.Double> 13, ancak C# değerini döndürmek için `(int)` işleci kesen <xref:System.Double> 12 değerini döndürmek için. Benzer şekilde, C# `(int)` Boolean tamsayı dönüştürmesi ancak Visual Basic işleci desteklemez `CInt` yöntemi bir değerine dönüştürür `true` -1. Diğer taraftan, <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> yöntemi bir değerine dönüştürür `true` 1.  
  
 Derleyicilerin çoğu, açık dönüştürmelerin denetlenen veya denetlenmeyen bir şekilde yapılmasına olanak tanır. Denetlenmiş dönüştürme gerçekleştirildiğinde, bir <xref:System.OverflowException> dönüştürülecek türü değeri hedef türü aralık dışında olduğunda oluşturulur. Aynı koşullarda denetlenmeyen bir dönüştürme yapıldığında, dönüştürme bir özel durum oluşturmayabilir, fakat davranış tam olarak tanımsız hale gelir ve sonuç olarak hatalı bir değer oluşabilir.  
  
> [!NOTE]
>  İşaretli C# ' ta kullanarak dönüştürme yapılabilir `checked` anahtar sözcüğü bir atama işleci ile birlikte veya belirterek `/checked+` derleyici seçeneği. Buna karşılık, denetlenmeyen dönüşümleri kullanılarak gerçekleştirilebilir `unchecked` anahtar sözcüğü atama işleci ile birlikte veya belirterek `/checked-` derleyici seçeneği. Varsayılan olarak, açık dönüştürmeler denetlenmez. Visual Basic'te dönüşümleri temizleyerek yapılabilir işaretli **kaldırmak tamsayı taşma denetimleri** projenin onay kutusuna **Gelişmiş derleyici ayarları** iletişim kutusu, veya belirterek`/removeintchecks-`derleyici seçeneği. Buna karşılık, denetlenmeyen dönüşümleri seçerek gerçekleştirilebilir **kaldırmak tamsayı taşma denetimleri** onay kutusunu projenin **Gelişmiş derleyici ayarları** iletişim kutusu veya belirterek`/removeintchecks+`derleyici seçeneği. Varsayılan olarak, açık dönüştürmeler denetlenir.  
  
 Aşağıdaki C# örnek kullanır `checked` ve `unchecked` davranışı bir değer zaman aralığının dışında farkı göstermek için anahtar sözcükler bir <xref:System.Byte> dönüştürülür bir <xref:System.Byte>. Checked dönüştürme bir özel durum oluşturur, ancak denetlenmeyen dönüştürme atar <xref:System.Byte.MaxValue?displayProperty=nameWithType> için <xref:System.Byte> değişkeni.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Belirli bir dil derleyicisi özel aşırı yüklü işleçleri desteklerse, kendi özel türlerinizde de açık dönüştürmeler tanımlayabilirsiniz. Aşağıdaki örnek adlı imzalı byte veri türü kısmi bir uygulamasını sağlar `ByteWithSign` oturum büyüklük gösterimini kullanır. Açık dönüşümünü destekleyen <xref:System.Int32> ve <xref:System.UInt32> değerler `ByteWithSign` değerleri.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 İstemci kodu sonra bildirebilirsiniz bir `ByteWithSign` değişkeni ve atayın <xref:System.Int32> ve <xref:System.UInt32> atamaları aşağıdaki örnekte gösterildiği gibi bir atama işleci veya bir dönüştürme yöntemi eklerseniz değerleri.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Başa dön](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>IConvertible Arabirimi  
 Ortak dil çalışma zamanı temel türün herhangi bir tür dönüştürme desteklemek için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sağlar <xref:System.IConvertible> arabirimi. Uygulama türünün aşağıdakileri sağlaması gerekir:  
  
-   Döndüren bir yöntem <xref:System.TypeCode> uygulama türü.  
  
-   Uygulama dönüştürme yöntemleri her ortak dil çalışma zamanı temel türü için yazın (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, vb.).  
  
-   Uygulama türünün bir örneğini başka bir belirtilen türe dönüştürmek için genelleştirilmiş bir dönüştürme yöntemi. Desteklenmez dönüşümleri throw bir <xref:System.InvalidCastException>.  
  
 Her ortak dil çalışma zamanı temel türü (diğer bir deyişle, <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>, ve <xref:System.UInt64>), yanı sıra <xref:System.DBNull> ve <xref:System.Enum> türleri, uygulayan <xref:System.IConvertible> arabirimi. Ancak, açık arabirim uygulamaları bunlar; dönüştürme yöntemi yalnızca aracılığıyla çağrılabilir bir <xref:System.IConvertible> aşağıdaki örnekte gösterildiği gibi arabirimi değişkeni. Bu örnek dönüştürür bir <xref:System.Int32> değeri eşdeğerine <xref:System.Char> değeri.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Dönüştürme yöntemini, uygulama türünde değil, kendi arabiriminde çağırma gereksinimi, açık arabirim uygulamalarını görece pahalılaştırır. Bunun yerine, uygun üyesi çağrı öneririz <xref:System.Convert> ortak dil çalışma zamanı temel türleri arasında dönüştürme için sınıf. Daha fazla bilgi için sonraki bölüme bakın [Dönüştür sınıfı](#Convert).  
  
> [!NOTE]
>  Ek olarak <xref:System.IConvertible> arabirimi ve <xref:System.Convert> sınıfı tarafından sağlanan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], tek tek dilleri dönüştürme gerçekleştirmek için yollar da sağlayabilir. Örneğin, C# atama işleçleri kullanır; Visual Basic derleyici uygulanan dönüştürme işlevleri gibi kullanır `CType`, `CInt`, ve `DirectCast`.  
  
 Çoğunlukla, <xref:System.IConvertible> arabirimi temel türler arasında dönüştürme desteklemek üzere tasarlanmıştır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Ancak, arabirim, o türün diğer özel türlere dönüştürülmesini desteklemek için özel bir tür tarafından da uygulanabilir. Daha fazla bilgi için bkz [özel dönüştürmeler ChangeType yöntemi ile](#ChangeType) bu konuda daha sonra.  
  
 [Başa dön](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Dönüştürme Sınıfı  
 Ancak her temel türün <xref:System.IConvertible> yöntemleri çağrılırken bir tür dönüştürme gerçekleştirmek için arabirim uygulamasına çağrılabilir <xref:System.Convert?displayProperty=nameWithType> temel bir türden diğerine dönüştürmek için önerilen dilden yol bir sınıftır. Ayrıca, <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi, belirtilen özel türünden başka bir türüne dönüştürmek için kullanılabilir.  
  
### <a name="conversions-between-base-types"></a>Temel Türler Arasında Dönüştürme  
 <xref:System.Convert> Sınıf temel türleri arasında dönüştürme gerçekleştirmek için bir dilden yöntem sunar ve ortak dil çalışma zamanı hedefleyen tüm diller için kullanılabilir. Hem genişletme ve daraltma dönüşümleri için eksiksiz bir yöntem sağlar ve oluşturur bir <xref:System.InvalidCastException> desteklenmez dönüştürmeleri için (dönüştürülmesi gibi bir <xref:System.DateTime> değer bir tamsayı değeri için). Daraltma dönüşümleri, denetlenen bir bağlamında gerçekleştirilir ve bir <xref:System.OverflowException> dönüştürme başarısız olursa oluşturulur.  
  
> [!IMPORTANT]
>  Çünkü <xref:System.Convert> sınıfı için ve her taban türünden dönüştürmek için yöntemler içerir, her temel türün çağırmak için ihtiyacını ortadan kaldıran <xref:System.IConvertible> açık arabirim uygulaması.  
  
 Aşağıdaki örnek kullanımını göstermektedir <xref:System.Convert?displayProperty=nameWithType> birkaç genişletme ve daraltma dönüşümleri .NET Framework temel türleri arasında gerçekleştirmek için sınıf.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 Değil throw olsa bile bazı durumlarda, özellikle kayan nokta değerlerine gelen ve giden dönüştürülürken dönüştürme duyarlık kaybı gerektirebilir bir <xref:System.OverflowException>. Aşağıdaki örnekte bu kesinlik kaybı gösterilmektedir. İlk durumda, bir <xref:System.Decimal> daha az duyarlık (daha az önemli basamak) değerine sahip olduğunda bu dönüştürülür için bir <xref:System.Double>. İkinci durumda, bir <xref:System.Double> değeri yuvarlanır 42.72 43 için dönüştürme işlemini tamamlamak için.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Hem genişletme ve daraltma dönüşümleri tarafından desteklenen listeleyen bir tablo için <xref:System.Convert> sınıfı için bkz: [tür dönüştürme tabloları](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>ChangeType Yöntemiyle Özel Dönüştürmeler  
 Dönüştürmeleri temel türlerinin her biri için destekleme yanı sıra <xref:System.Convert> sınıfı, bir özel tür bir veya daha fazla önceden tanımlanmış türlerine dönüştürmek için kullanılabilir. Bu dönüştürme tarafından gerçekleştirilen <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> sırayla yapılan bir çağrı sarmalar yöntemi <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> yöntemi `value` parametresi. Tarafından temsil edilen nesne buna `value` parametresi uygulaması sağlamalıdır <xref:System.IConvertible> arabirimi.  
  
> [!NOTE]
>  Çünkü <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> ve <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri kullanın bir <xref:System.Type> hedef türe belirtmek için nesne `value` olan dönüştürülür, bunlar derleme zamanında türü bilinen değil bir nesne için dinamik bir dönüştürme gerçekleştirmek için kullanılabilir. Ancak, dikkat edin <xref:System.IConvertible> uyarlamasını `value` hala bu dönüştürme desteklemesi gerekir.  
  
 Aşağıdaki örnek, olası bir uygulamasına gösterilmektedir <xref:System.IConvertible> arabirimi bir `TemperatureCelsius` dönüştürüleceğini nesnesinin bir `TemperatureFahrenheit` nesne tersi. Örnek bir temel sınıf tanımlar `Temperature`, uygulayan <xref:System.IConvertible> arabirimi ve geçersiz kılmalar <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi. Türetilmiş `TemperatureCelsius` ve `TemperatureFahrenheit` her geçersiz kılma sınıfları `ToType` ve `ToString` yöntemleri temel sınıf.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Aşağıdaki örnekte, bunlar birkaç çağrı gösterilmektedir <xref:System.IConvertible> dönüştürmek için uygulamaları `TemperatureCelsius` nesneleri `TemperatureFahrenheit` nesneleri ve tersi.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Başa dön](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>TypeConverter Sınıfı  
 .NET Framework ayrıca özel bir tür için tür dönüştürücüsünü genişleterek tanımlamanıza olanak verir <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> sınıfı ve türü dönüştürücü üzerinden türüyle ilişkilendirme bir <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> özniteliği. Aşağıdaki tabloda bu yaklaşım arasındaki farklar vurgular ve uygulama <xref:System.IConvertible> özel bir tür için arabirim.  
  
> [!NOTE]
>  Tasarım zamanı desteği, yalnızca kendisi için tanımlanmış bir tür dönüştürücüsü varsa, özel bir tür için sağlanabilir.  
  
|TypeConverter kullanılarak dönüştürme|IConvertible kullanılarak dönüştürme|  
|------------------------------------|-----------------------------------|  
|Özel bir tür için ayrı bir sınıftan türetilen tarafından uygulanan <xref:System.ComponentModel.TypeConverter>. Bu türetilmiş sınıf uygulayarak özel türüyle ilişkili bir <xref:System.ComponentModel.TypeConverterAttribute> özniteliği.|Dönüştürme yapmak için özel bir tür tarafından uygulanır. Bir kullanıcı türü çağıran bir <xref:System.IConvertible> türünün dönüştürme yöntemi.|  
|Hem tasarım zamanında hem de çalışma zamanında kullanılabilir.|Yalnızca çalışma zamanında kullanılabilir.|  
|Yansıma kullanır; Bu nedenle, etkin dönüştürme daha yavaştır <xref:System.IConvertible>.|Yansıma kullanmaz.|  
|özel türden diğer veri türlerine ve diğer veri türlerinden özel türe olmak üzere, iki yönlü tür dönüştürmelerine olanak tanır. Örneğin, bir <xref:System.ComponentModel.TypeConverter> için tanımlanan `MyType` gelen dönüştürmeler sağlar `MyType` için <xref:System.String>, gelen ve giden <xref:System.String> için `MyType`.|Özel bir türden diğer veri türlerine dönüştürmeye olanak tanır, fakat diğer veri türlerinden özel türe dönüştürmeye olanak tanımaz.|  
  
 Dönüştürme gerçekleştirmek için tür dönüştürücüleri kullanma hakkında daha fazla bilgi için bkz: <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert?displayProperty=nameWithType>  
 <xref:System.IConvertible>  
 [Tür Dönüştürme Tabloları](../../../docs/standard/base-types/conversion-tables.md)
