---
title: Genel Türlerde Kovaryans ve Kontravaryans
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18244ab0473ca4de97e8b6e4eb84151d3a1a5b6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692970"
---
# <a name="covariance-and-contravariance-in-generics"></a>Genel Türlerde Kovaryans ve Kontravaryans
<a name="top"></a> Kovaryans ve kontravaryans daha türetilmiş türde (ayrıntılı) veya orijinal olarak belirtilenden daha az türetilmiş bir tür (less yazımına özgü) kullanma olanağı için başvuran terimlerdir. Genel tür parametreleri, genel türleri atamakta ve kullanmakta daha fazla esneklik sağlamak için birlikte değişme ve değişken karşıtlığını destekler. Bir tür sisteminden söz ederken, birlikte değişme, değişken karşıtlığı ve değişmezlik terimlerinin tanımları aşağıdaki gibidir. Örneklerde adlı bir temel sınıf varsayılmaktadır `Base` ve adlı bir türetilmiş sınıf `Derived`.  
  
-   `Covariance`  
  
     Orijinal olarak belirtilenden daha fazla türetilmiş bir tür belirtmenize olanak sağlar.  
  
     Örneği atayabilirsiniz `IEnumerable<Derived>` (`IEnumerable(Of Derived)` Visual Basic'te) türünde bir değişkene `IEnumerable<Base>`.  
  
-   `Contravariance`  
  
     Orijinal olarak belirtilenden daha genel (daha az türetilmiş) bir tür belirtmenize olanak tanır.  
  
     Örneği atayabilirsiniz `Action<Base>` (`Action(Of Base)` Visual Basic'te) türünde bir değişkene `Action<Derived>`.  
  
-   `Invariance`  
  
     Yalnızca orijinal olarak belirtilen türü kullanabileceğiniz anlamına gelir; bu nedenle, değişmez bir genel tür parametresi birlikte değişken veya değişken karşıtı değildir.  
  
     Örneği atanamaz `List<Base>` (`List(Of Base)` Visual Basic'te) türünde bir değişkene `List<Derived>` ya da tam tersi.  
  
 Birlikte değişken tür parametreleri etkinleştirme sıradan gibi ara atamalar yapmanıza [çok biçimlilik](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md)aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601> Sınıfının Implements <xref:System.Collections.Generic.IEnumerable%601> arabirim, bunu `List<Derived>` (`List(Of Derived)` Visual Basic'te) uygulayan `IEnumerable<Derived>`. Birlikte değişken tür parametresi geri kalanını yapar.  
  
 Diğer taraftan, birlikte değişkenlik mantığa aykırı görünüyor. Aşağıdaki örnek, bir temsilci türü oluşturur. `Action<Base>` (`Action(Of Base)` Visual Basic'te) ve ardından bu temsilci türünde bir değişkene atar `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Geri gibi görünüyor, ancak derleyen ve çalışan, tür açısından güvenli koddur. Türünde bir parametre alan bir yöntem tanımlar için lambda ifadesi için atandığı temsilciyle eşleşir `Base` ve, dönüş değeri yok. Sonuç olarak oluşan temsilci türünde bir değişkene atanabilir `Action<Derived>` çünkü tür parametresi `T` , <xref:System.Action%601> değişken karşıtı temsilcisidir. Kod tür bakımından güvenlidir çünkü `T` parametre türünü belirtir. Temsilci türünün `Action<Base>` türünde bir temsilci kabul edildiğinde çağrılan `Action<Derived>`, bağımsız değişken türü olmalıdır `Derived`. Yöntemin parametresi türünde olduğu için bu bağımsız değişken her zaman arka plandaki yönteme güvenli bir şekilde geçirilebilir `Base`.  
  
 Genel olarak, birlikte değişken türünde bir parametre bir temsilcinin dönüş türü olarak kullanılabilir ve değişken karşıtı türü parametreler parametre türleri olarak kullanılabilir. Bir arabirim için, birlikte değişken türü parametreler arabirimin yöntemlerinin dönüş türleri olarak kullanılabilir ve değişken karşıtı türü parametreler arabirimin yöntemlerinin parametre türleri olarak kullanılabilir.  
  
 Kovaryans ve kontravaryans topluca denir *varyansı*. Birlikte değişken olarak işaretlenmemiş bir genel tür parametresi veya değişken karşıtı olarak adlandırılır *sabit*. Genel dil çalışma zamanında değişken ile ilgili gerçeklerin kısa bir özeti:  
  
-   İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], değişken türünde parametreler genel arabirimle ve genel temsilci türleriyle için Yasak.  
  
-   Bir genel arabirim veya genel temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
-   Değişken yalnızca başvuru türleri için geçerlidir; değişken türünde bir parametre için bir değer türü belirtirseniz, bu tür parametresi, sonuç olarak oluşturulan tür için değişmezdir.  
  
-   Değişken, temsilci birleşimi için geçerli değildir. Diğer bir deyişle, türlerinde iki temsilci olduğunda verilen `Action<Derived>` ve `Action<Base>` (`Action(Of Derived)` ve `Action(Of Base)` Visual Basic'te), sonuç tür bakımından güvenli olacak olsa da, ikinci temsilciyi birinciyle birleştiremezsiniz. Farkı verir ikinci bir temsilci türünde bir değişkene atanması `Action<Derived>`, fakat temsilciler yalnızca türleri tam olarak eşleşirse.  
  
 Aşağıdaki alt kısımlarda, değişkenle birlikte ve değişken karşıtı tür parametreleri ayrıntılı olarak açıklanmaktadır:  
  
-   [Birlikte değişen tür parametreleriyle genel arabirimler](#InterfaceCovariantTypeParameters)  
  
-   [Değişken karşıtı genel tür parametrelerle genel arabirimler](#InterfaceCovariantTypeParameters)  
  
-   [Değişken genel temsilcilerin tür parametreleri](#DelegateVariantTypeParameters)  
  
-   [Değişken genel arabirimleri ve temsilcileri tanımlama](#DefiningVariantTypeParameters)  
  
-   [Değişken genel arabirim ve temsilci türlerinin listesi](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Birlikte Değişen Tür Parametreleriyle Genel Arabirimler  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], çeşitli genel arabirimlerin birlikte değişen türde parametreleri vardır; örneğin: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, ve <xref:System.Linq.IGrouping%602>. Bu arabirimlerin tüm tür parametreleri birlikte değişen olduğundan, tür parametreleri yalnızca üyelerin dönüş türleri için kullanılır.  
  
 Aşağıdaki örnekte, birlikte değişen tür parametreleri gösterilmektedir. Örnekte iki tür tanımlanmaktadır: `Base` adlı statik bir yöntem olan `PrintBases` almayan bir `IEnumerable<Base>` (`IEnumerable(Of Base)` Visual Basic'te) ve öğeleri yazdıran. `Derived` devralınan `Base`. Boş bir örnek oluşturur `List<Derived>` (`List(Of Derived)` Visual Basic'te) ve bu tür için geçirilebileceğini gösterir `PrintBases` ve türünde bir değişkene atanan `IEnumerable<Base>` olmadan. <xref:System.Collections.Generic.List%601> uygulayan <xref:System.Collections.Generic.IEnumerable%601>, bir tek birlikte değişen türde parametresi vardır. Birlikte değişken tür parametresi nedeni budur örneği `IEnumerable<Derived>` yerine kullanılan `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Değişken Karşıtı Genel Tür Parametrelerle Genel Arabirimler  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], çeşitli genel arabirimlerin değişken karşıtı türde parametreleri vardır; örneğin: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, ve <xref:System.Collections.Generic.IEqualityComparer%601>. Bu arabirimlerin yalnızca değişken karşıtı türde parametreleri olduğundan, tür parametreleri yalnızca arabirimlerin üyelerinde parametre türleri olarak kullanılır.  
  
 Aşağıdaki örnekte, değişken karşıtı tür parametreleri gösterilmektedir. Örnek bir Özet tanımlar (`MustInherit` Visual Basic'te) `Shape` sınıfıyla birlikte bir `Area` özelliği. Örnek ayrıca tanımlar bir `ShapeAreaComparer` uygulayan sınıf `IComparer<Shape>` (`IComparer(Of Shape)` Visual Basic'te). Uygulamasını <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> yöntemi değerini temel alarak `Area` özelliği, bu nedenle `ShapeAreaComparer` sıralamak için kullanılan `Shape` nesnelerini alana göre.  
  
 `Circle` Sınıfından devralan `Shape` ve geçersiz kılmaları `Area`. Örnek bir <xref:System.Collections.Generic.SortedSet%601> , `Circle` alan bir Oluşturucu kullanarak, nesneleri bir `IComparer<Circle>` (`IComparer(Of Circle)` Visual Basic'te). Ancak, geçirmek yerine bir `IComparer<Circle>`, örnek geçen bir `ShapeAreaComparer` uygulayan nesne `IComparer<Shape>`. Örnek daha az türetilmiş bir türde bir karşılaştırıcı geçirebilir (`Shape`) kod daha türetilmiş bir tür için bir karşılaştırıcı çağırdığında (`Circle`), çünkü tür parametresi <xref:System.Collections.Generic.IComparer%601> genel arabirim değişken karşıtı olduğu.  
  
 Yeni bir `Circle` eklenir `SortedSet<Circle>`, `IComparer<Shape>.Compare` yöntemi (`IComparer(Of Shape).Compare` yöntem Visual Basic'te), `ShapeAreaComparer` nesne, yeni bir öğe var olan bir öğeye kıyasla her zaman çağrılır. Yöntemin parametre türü (`Shape`), geçirilmekte türünden daha az türetilmiş (`Circle`), çağrı tür bakımından güvenli olacak şekilde. Kontravaryans sağlayan `ShapeAreaComparer` öğesinden türetilen türler, karma koleksiyonu yanı sıra tek herhangi bir türde bir koleksiyonu sıralamak için `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Değişken Türü Parametrelerle Genel Temsilciler  
 İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], `Func` gibi genel temsilcilerinin <xref:System.Func%602>, birlikte değişken dönüş türleri ve değişken karşıtı parametre türleri vardır. `Action` Gibi genel temsilcilerinin <xref:System.Action%602>, değişken karşıtı parametre türleri vardır. Bu temsilciler daha fazla türetilmiş parametre türleri değişkenlere atanması anlamına gelir ve (durumunda `Func` genel temsilciler) daha az türetilmiş dönüş türleri.  
  
> [!NOTE]
>  Son genel tür parametresi `Func` genel temsilcilerin dönüş değeri türünü temsilci imzasında belirtir. Birlikte değişken olduğu (`out` anahtar sözcüğü), bir genel tür parametre değişken karşıtıdır (`in` anahtar sözcüğü).  
  
 Aşağıdaki kod bunu göstermektedir. İlk kod parçası adlı bir sınıf tanımlar `Base`, adlı bir sınıf `Derived` devralan `Base`ve başka bir sınıf ile bir `static` yöntemi (`Shared` Visual Basic'te) adlı `MyMethod`. Yöntem bir örneğini alır `Base` ve örneğini döndürür `Derived`. (Bağımsız değişken bir örneği ise `Derived`, `MyMethod` bağımsız değişken bir örneği ise onu döndürür; `Base`, `MyMethod` yeni bir örneğini döndürür `Derived`.) İçinde `Main()`, örnek örneği oluşturur `Func<Base, Derived>` (`Func(Of Base, Derived)` Visual Basic'te) temsil eden `MyMethod`ve bunu bir değişkende depolar `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 İkinci kod parçası temsilci türünde bir değişken atanabileceğini göstermektedir `Func<Base, Base>` (`Func(Of Base, Base)` Visual Basic'te), dönüş türü birlikte değişken olduğu için.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Üçüncü kod parçası temsilci türünde bir değişken atanabileceğini göstermektedir `Func<Derived, Derived>` (`Func(Of Derived, Derived)` Visual Basic'te), parametre türü değişken karşıtı olduğundan.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Son kod parçası temsilci türünde bir değişken atanabileceğini göstermektedir `Func<Derived, Base>` (`Func(Of Derived, Base)` Visual Basic'te), etkilerini değişken karşıtı parametre türünün ve birlikte değişken dönüş türü.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Genel ve Genel Olmayan Temsilcilerde Değişken  
 Önceki kodda, imzası `MyMethod` oluşturulan genel temsilcinin imzasını tam olarak eşleşir: `Func<Base, Derived>` (`Func(Of Base, Derived)` Visual Basic'te). Tüm temsilci türleri Genel temsilci türünden oluşturulduğu sürece, bu genel temsilcinin değişkenleri veya daha fazla türetilmiş parametre türleri yöntem parametreleri depolanabilir ve daha az türetilmiş dönüş türleri örnek gösterir <xref:System.Func%602>.  
  
 Bu önemli bir noktadır. Kovaryans ve kontravaryans, genel temsilcilerin tür parametrelerindeki etkileri sıradan temsilci bağlamadaki etkilerini Kovaryans ve kontravaryans benzer (bkz [Temsilcilerde varyans](https://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)). Ancak, temsilci bağlamadaki değişken, yalnızca değişken türde parametreleri olan genel temsilci türleriyle değil, tüm temsilci türleriyle birlikte çalışır. Ayrıca, temsilci bağlamada değişken, bir yöntemin daha kısıtlayıcı parametre türleri ve daha az kısıtlayıcı dönüş türü olan herhangi bir temsilciye bağlanmasına olanak tanırken, genel temsilcilerin atanması yalnızca her iki temsilci türünün de aynı genel tür tanımından oluşturulması durumunda çalışır.  
  
 Aşağıdaki örnekte, temsilci bağlamadaki değişkenin ve genel tür parametrelerindeki değişkenin birleşik etkisi gösterilmektedir. Örneğin, gelen en az üç tür içeren bir tür hiyerarşisi tanımlanmaktadır türetilmiş (`Type1`) en çok türetilene (`Type3`). Sıradan temsilci bağlamada değişken parametre türü bir yöntemi bağlamak için kullanılan `Type1` ve dönüş türü `Type3` temsilci parametre türüne sahip `Type2` ve dönüş türü `Type2`. Sonuç olarak oluşan genel temsilci daha sonra genel temsilci türü türünde bir parametreye sahip başka bir değişkene atanır `Type3` ve dönüş türü `Type1`, Kovaryans ve kontravaryans, genel tür parametrelerinin kullanarak. İkinci atama, hem değişken türünün hem de temsilci türüyle aynı genel tür tanımından, bu durumda, kendisinden oluşturulacağı gerektirir <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Değişken Genel Arabirimleri ve Temsilcileri Tanımlama  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Visual Basic ve C#, arabirimlerin genel tür parametreleri işaretlemek etkinleştirmeniz ve temsilcilerini birlikte değişken olarak anahtar sözcükler veya değişken karşıtı sahip.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, genel dil çalışma zamanı, genel tür parametrelerinde değişken açıklamalarını destekler. Öncesinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], bu ek açıklamaları içeren genel bir sınıf tanımlamanın tek yolu, Microsoft Ara dilini (MSIL) sınıfı içeren derlemeyi ya da kullanmaktır [Ilasm.exe (IL derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) veya dinamik yayma derleme.  
  
 Birlikte değişken tür parametresi ile işaretlenmiş `out` anahtar sözcüğü (`Out` Visual Basic'teki `+` için [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Birlikte değişken türünde bir parametreyi, bir arabirime ait olan bir yöntemin dönüş değeri olarak veya bir temsilcinin dönüş türü olarak kullanabilirsiniz. Birlikte değişken türünde bir parametreyi, arabirim yöntemleri için genel türde bir kısıtlayıcı olarak kullanamazsınız.  
  
> [!NOTE]
>  Bir arabirimin bir yöntemi genel temsilci türünde bir parametreye sahipse, arabirim türünün birlikte değişken türünde bir parametresi, temsilci türünün değişken karşıtı türünde bir parametresini belirtmek için kullanılabilir.  
  
 Değişken karşıtı tür parametresi ile işaretlenmiş `in` anahtar sözcüğü (`In` Visual Basic'teki `-` için [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Değişken karşıtı türde bir parametreyi, bir arabirime ait olan bir yöntemin bir parametresinin türü olarak veya bir temsilcinin bir parametresinin türü olarak kullanabilirsiniz. Değişken karşıtı türde bir parametreyi, bir arabirim yöntemi için genel türde bir kısıtlama olarak kullanabilirsiniz.  
  
 Yalnızca arabirim türlerinin ve temsilci türlerinin değişken türünde parametreleri olabilir. Bir arabirim veya temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
 Visual Basic ve C#, birlikte değişken veya değişken karşıtı türde parametrelerin kullanılmasına ilişkin kuralların ihlal edilmesine veya arabirimlerden ve temsilcilerden başka türde tür parametrelerine birlikte değişken veya değişken karşıtı ek açıklamalar eklenmesine izin vermez. [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) tür denetimler gerçekleştirmez ancak <xref:System.TypeLoadException> kuralları ihlal eden bir tür yüklemeyi denerseniz oluşturulur.  
  
 Bilgi ve örnek kod için bkz. [genel arabirimlerde varyans](https://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a).  
  
 [Başa dön](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Değişken Genel Arabirim ve Temsilci Türleri Listesi  
 İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], aşağıdaki arabirim ve temsilci türlerinin birlikte değişken olması ve/veya değişken karşıtı türde parametreleri.  
  
|Tür|Birlikte değişken türde parametreler|Değişken karşıtı türde parametreler|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601> Hedef <xref:System.Action%6016>||Evet|  
|<xref:System.Comparison%601>||Evet|  
|<xref:System.Converter%602>|Evet|Evet|  
|<xref:System.Func%601>|Evet||  
|<xref:System.Func%602> Hedef <xref:System.Func%6017>|Evet|Evet|  
|<xref:System.IComparable%601>||Evet|  
|<xref:System.Predicate%601>||Evet|  
|<xref:System.Collections.Generic.IComparer%601>||Evet|  
|<xref:System.Collections.Generic.IEnumerable%601>|Evet||  
|<xref:System.Collections.Generic.IEnumerator%601>|Evet||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Evet|  
|<xref:System.Linq.IGrouping%602>|Evet||  
|<xref:System.Linq.IOrderedEnumerable%601>|Evet||  
|<xref:System.Linq.IOrderedQueryable%601>|Evet||  
|<xref:System.Linq.IQueryable%601>|Evet||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kovaryans ve kontravaryans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kovaryans ve kontravaryans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Temsilcilerde Varyans](https://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)
