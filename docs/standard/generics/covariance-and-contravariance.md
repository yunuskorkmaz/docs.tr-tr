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
ms.openlocfilehash: 909b03588d2a41f667bfa117a5cecb420b125088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708403"
---
# <a name="covariance-and-contravariance-in-generics"></a>Genel Türlerde Kovaryans ve Kontravaryans
Tutarlılık ve kontravariance, başlangıçta belirtilenden daha türemiş bir tür (daha spesifik) veya daha az türemiş (daha az özel) kullanma yeteneğini ifade eden terimlerdir. Genel tür parametreleri, genel türleri atamakta ve kullanmakta daha fazla esneklik sağlamak için birlikte değişme ve değişken karşıtlığını destekler. Bir tür sisteminden söz ederken, birlikte değişme, değişken karşıtlığı ve değişmezlik terimlerinin tanımları aşağıdaki gibidir. Örnekler, adlı `Base` bir taban sınıf ve `Derived`türetilmiş bir sınıf.  
  
- `Covariance`  
  
     Başlangıçta belirtilenden daha türetilmiş bir tür kullanmanıza olanak sağlar.  
  
     Bir örneğini `IEnumerable<Derived>` (Visual`IEnumerable(Of Derived)` Basic'te) bir tür `IEnumerable<Base>`değişkenine atayabilirsiniz.  
  
- `Contravariance`  
  
     Orijinal olarak belirtilenden daha genel (daha az türetilmiş) bir tür belirtmenize olanak tanır.  
  
     Bir örneğini `Action<Base>` (Visual`Action(Of Base)` Basic'te) bir tür `Action<Derived>`değişkenine atayabilirsiniz.  
  
- `Invariance`  
  
     Yalnızca orijinal olarak belirtilen türü kullanabileceğiniz anlamına gelir; bu nedenle, değişmez bir genel tür parametresi birlikte değişken veya değişken karşıtı değildir.  
  
     Bir örneğini `List<Base>` (Visual`List(Of Base)` Basic'te) bir tür `List<Derived>` değişkenine veya tam tersi atayamazsınız.  
  
 Eşdeğişken türü parametreleri, aşağıdaki kodda gösterildiği gibi, sıradan [Polimorfizme](../../csharp/programming-guide/classes-and-structs/polymorphism.md)çok benzeyen atamalar yapmanızı sağlar.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 Sınıf <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.IEnumerable%601> arabirimi uygular, `List<Derived>` bu`List(Of Derived)` nedenle (Visual `IEnumerable<Derived>`Basic' de) uygular. Birlikte değişken tür parametresi geri kalanını yapar.  
  
 Diğer taraftan, birlikte değişkenlik mantığa aykırı görünüyor. Aşağıdaki örnek, bir tür `Action<Base>` temsilcisi`Action(Of Base)` oluşturur (Visual Basic'te) ve sonra `Action<Derived>`bu temsilciyi tür değişkenine atar.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Geri gibi görünüyor, ancak derleyen ve çalışan, tür açısından güvenli koddur. Lambda ifadesi atandığı temsilciyle eşleşir, bu nedenle bir parametre türü `Base` alan ve geri dönüş değeri olmayan bir yöntem tanımlar. Temsilcinin tür parametresi `Action<Derived>` `T` kontrdeğişken olduğundan, elde edilen <xref:System.Action%601> temsilci bir tür değişkenine atanabilir. Bir parametre türü `T` belirttiğinden kod tür güvenlidir. Tür `Action<Base>` temsilcisi, türün `Action<Derived>`bir temsilcisi gibi çağrıldığınızda, bağımsız değişkeni `Derived`türde olmalıdır. Yöntemin parametresi türünden `Base`olduğundan, bu bağımsız değişken her zaman temel yönteme güvenli bir şekilde geçirilebilir.  
  
 Genel olarak, birlikte değişken türünde bir parametre bir temsilcinin dönüş türü olarak kullanılabilir ve değişken karşıtı türü parametreler parametre türleri olarak kullanılabilir. Bir arabirim için, birlikte değişken türü parametreler arabirimin yöntemlerinin dönüş türleri olarak kullanılabilir ve değişken karşıtı türü parametreler arabirimin yöntemlerinin parametre türleri olarak kullanılabilir.  
  
 Covariance ve kontravaryans topluca *varyans*olarak adlandırılır. Ortak değişken veya kontraktür işaretlenmemiş genel bir tür *parametreye değişmez*denir. Genel dil çalışma zamanında değişken ile ilgili gerçeklerin kısa bir özeti:  
  
- .NET Framework 4'te, varyant türü parametreleri genel arabirim ve genel temsilci türleri ile sınırlıdır.  
  
- Bir genel arabirim veya genel temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
- Değişken yalnızca başvuru türleri için geçerlidir; değişken türünde bir parametre için bir değer türü belirtirseniz, bu tür parametresi, sonuç olarak oluşturulan tür için değişmezdir.  
  
- Değişken, temsilci birleşimi için geçerli değildir. Diğer bir deyişle, iki `Action<Derived>` tür `Action<Base>` `Action(Of Derived)` temsilcisi `Action(Of Base)` ve (ve Visual Basic) göz önüne alındığında, ikinci temsilciyi ilkimle birleştiremezsiniz, ancak sonuç yazı güvenli olacaktır. Varyans, ikinci temsilcinin bir tür `Action<Derived>`değişkenine atanmasına izin verir, ancak temsilciler yalnızca türleri tam olarak eşleşirse birleştirebilir.

<a name="InterfaceCovariantTypeParameters"></a>
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Birlikte Değişen Tür Parametreleriyle Genel Arabirimler  
 .NET Framework 4 ile başlayarak, çeşitli genel arabirimler birlikte varyant türü parametreleri vardır; örneğin: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Linq.IQueryable%601>, <xref:System.Linq.IGrouping%602>, ve . Bu arabirimlerin tüm tür parametreleri birlikte değişen olduğundan, tür parametreleri yalnızca üyelerin dönüş türleri için kullanılır.  
  
 Aşağıdaki örnekte, birlikte değişen tür parametreleri gösterilmektedir. Örnek iki `Base` tür tanımlar: (Visual `PrintBases` `IEnumerable<Base>` `IEnumerable(Of Base)` Basic) alır ve öğeleri yazdırır adlı statik bir yöntem vardır. `Derived`'den `Base`devralır. Örnek, `List<Derived>` boş (Visual`List(Of Derived)` Basic'te) oluşturur ve bu türün `PrintBases` döküm olmadan bir `IEnumerable<Base>` tür değişkenine geçirilebilen ve atanabileceğini gösterir. <xref:System.Collections.Generic.List%601>uygular <xref:System.Collections.Generic.IEnumerable%601>, tek bir eşvaryant türü parametresi vardır. Eşdeğişken türü parametresi, `IEnumerable<Derived>` `IEnumerable<Base>`bir örneğinin '' yerine kullanılabilmesinin nedenidir.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Değişken Karşıtı Genel Tür Parametrelerle Genel Arabirimler  
 .NET Framework 4'ten başlayarak, birkaç genel arabirimde karşıt tür parametreleri vardır; örneğin: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, <xref:System.Collections.Generic.IEqualityComparer%601>ve . Bu arabirimlerin yalnızca değişken karşıtı türde parametreleri olduğundan, tür parametreleri yalnızca arabirimlerin üyelerinde parametre türleri olarak kullanılır.  
  
 Aşağıdaki örnekte, değişken karşıtı tür parametreleri gösterilmektedir. Örnek, `Area` bir özelliği`MustInherit` olan soyut `Shape` (Visual Basic'te) sınıf tanımlar. Örnek, `IComparer<Shape>` (Visual`IComparer(Of Shape)` `ShapeAreaComparer` Basic'te) uygulayan bir sınıfı da tanımlar. <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> Yöntemin uygulanması `Area` özelliğin değerine bağlıdır, bu `ShapeAreaComparer` nedenle nesneleri alana göre sıralamak `Shape` için kullanılabilir.  
  
 Sınıf `Circle` devralır `Shape` ve `Area`geçersiz kılar. Örnek, (Visual <xref:System.Collections.Generic.SortedSet%601> `Circle` `IComparer<Circle>` `IComparer(Of Circle)` Basic'te) alan bir oluşturucu kullanarak bir nesne oluşturur. Ancak, bir `IComparer<Circle>`, örnek geçen `ShapeAreaComparer` bir nesne, `IComparer<Shape>`uygular. Genel arabirimin tür parametresi`Shape``Circle` <xref:System.Collections.Generic.IComparer%601> karşıt olduğundan, kod daha türetilmiş bir tür () bir karşılayıcı için çağrıda bulunurken, örnek daha az türetilmiş tür () bir karşılayıcı geçirebilir.  
  
 Yeni `Circle` bir nesne , `SortedSet<Circle>`(Visual `IComparer<Shape>.Compare` Basic`IComparer(Of Shape).Compare` yöntemi) `ShapeAreaComparer` yeni bir öğe ye yeni bir öğe ile karşılaştırıldığında her zaman denir yeni bir nesne eklendiğinde. Yöntemin parametre türü`Shape`( ) geçirilen türe göre daha`Circle`az türetilmiş ( ), bu nedenle çağrı türü güvenlidir. Kontrayanlık, `ShapeAreaComparer` herhangi bir tek türden oluşan bir koleksiyonun yanı `Shape`sıra.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Değişken Türü Parametrelerle Genel Temsilciler  
 .NET Framework 4'te, `Func` genel temsilciler <xref:System.Func%602>, eşdeğişken dönüş türleri ve kontradavaryant parametre türleri vardır. Genel `Action` temsilciler, örneğin, <xref:System.Action%602>karşıt parametre türleri vardır. Bu, temsilcilerin daha fazla türemiş parametre türüne ve `Func` (genel temsilciler durumunda) daha az türetilmiş iade türüne sahip değişkenlere atanabileceği anlamına gelir.  
  
> [!NOTE]
> `Func` Genel temsilcilerin son genel tür parametresi, temsilci imzasındaki iade değerinin türünü belirtir. Diğer genel tür`out` parametreleri kontrdeğişken (anahtar`in` kelime) ise, eşanlamlıdır.  
  
 Aşağıdaki kod bunu göstermektedir. Kodun ilk parçası adlı bir `Base`sınıf tanımlar `Derived` , `Base`bir sınıf adlı, `static` bir`Shared` sınıf, bir `MyMethod`sınıf, bir yöntem ile başka bir sınıf (Visual Basic) adlı . Yöntem bir örneğini `Base` alır ve `Derived`''nin bir örneğini döndürür. (Bağımsız değişken bir örneği `Derived` `MyMethod` ise , döndürür; bağımsız `Base` `MyMethod` değişken bir örneği `Derived`ise , yeni bir örneği döndürür.) `Main()`Yani, örnek `Func<Base, Derived>` (Visual`Func(Of Base, Derived)` Basic'te) `MyMethod`bir örneğini oluşturur ve değişkende `f1`depolar.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 İkinci kod parçası, temsilcinin bir tür `Func<Base, Base>` değişkenine`Func(Of Base, Base)` (Visual Basic'te) atanabileceğini gösterir, çünkü dönüş türü eş değişkendir.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Üçüncü kod parçası, parametre türü karşıt olduğundan, `Func<Derived, Derived>` `Func(Of Derived, Derived)` temsilcinin bir tür değişkenine (Visual Basic'te) atanabileceğini gösterir.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Kodun son parçası, temsilcinin karşıt parametre `Func<Derived, Base>` türü`Func(Of Derived, Base)` ve eşdeğişken dönüş türünün etkilerini birleştirerek bir tür değişkenine (Visual Basic) atanabileceğini gösterir.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Genel ve Genel Olmayan Temsilcilerde Değişken  
 Önceki kodda, imza `MyMethod` tam olarak yapılandırılan genel temsilcinin `Func<Base, Derived>` `Func(Of Base, Derived)` imzasıyla eşleşir: (Visual Basic'te). Örnek, tüm temsilci türleri genel temsilci türünden <xref:System.Func%602>oluşturuldukça, bu genel temsilcinin daha çok türemiş parametre türü ve daha az türetilmiş iade türüolan değişkenlerde veya yöntem parametrelerinde depolanabileceğini gösterir.  
  
 Bu önemli bir noktadır. Genel temsilcilerin tür parametrelerindeki covariance ve contravariance'ın etkileri, sıradan temsilci bağlamasında ki covariance ve contravariance'ın etkilerine benzer (bkz. [Delegelerde Varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Temsilcilerdeki Varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Ancak, temsilci bağlamadaki değişken, yalnızca değişken türde parametreleri olan genel temsilci türleriyle değil, tüm temsilci türleriyle birlikte çalışır. Ayrıca, temsilci bağlamada değişken, bir yöntemin daha kısıtlayıcı parametre türleri ve daha az kısıtlayıcı dönüş türü olan herhangi bir temsilciye bağlanmasına olanak tanırken, genel temsilcilerin atanması yalnızca her iki temsilci türünün de aynı genel tür tanımından oluşturulması durumunda çalışır.  
  
 Aşağıdaki örnekte, temsilci bağlamadaki değişkenin ve genel tür parametrelerindeki değişkenin birleşik etkisi gösterilmektedir. Örnek, en az türetilmiş ( )`Type1`den en türetilmiş`Type3`( ) üç tür içeren bir tür hiyerarşisi tanımlar. Normal temsilci bağlamadaki varyans, parametre `Type1` türü ne ve bir parametre `Type3` türü `Type2` ve bir geri dönüş türü olan `Type2`genel bir temsilciye dönüş türü olan bir yöntemi bağlamak için kullanılır. Elde edilen genel temsilci daha sonra, genel temsilci türü parametresi ve genel tür `Type3` parametrelerinin karşıtlığını ve kontrayansını kullanarak bir dönüş türüne `Type1`sahip olan başka bir değişkene atanır. İkinci atama, hem değişken türünü hem de temsilci türünün aynı genel tür <xref:System.Func%602>tanımından oluşturulmasını gerektirir, bu durumda, .  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="defining-variant-generic-interfaces-and-delegates"></a>Değişken Genel Arabirimleri ve Temsilcileri Tanımlama
 .NET Framework 4 ile başlayarak Visual Basic ve C# arabirimlerin ve temsilcilerin genel tür parametrelerini ortak veya karşıt olarak işaretlemenizi sağlayan anahtar kelimelere sahiptir.  
  
> [!NOTE]
> .NET Framework sürüm 2.0 ile başlayarak, genel dil çalışma zamanı, genel tür parametrelerinde değişken açıklamalarını destekler. .NET Framework 4'ten önce, bu ek açıklamalara sahip genel bir sınıfı tanımlamanın tek yolu, sınıfı [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) ile derleyerek veya dinamik bir derlemeye yayırak Microsoft ara dilini (MSIL) kullanmaktır.  
  
 Ortak varyant türü parametresi `out` anahtar kelimeyle (Visual`Out` Basic'teki anahtar kelime, `+` [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)için) işaretlenir. Birlikte değişken türünde bir parametreyi, bir arabirime ait olan bir yöntemin dönüş değeri olarak veya bir temsilcinin dönüş türü olarak kullanabilirsiniz. Birlikte değişken türünde bir parametreyi, arabirim yöntemleri için genel türde bir kısıtlayıcı olarak kullanamazsınız.  
  
> [!NOTE]
> Bir arabirimin bir yöntemi genel temsilci türünde bir parametreye sahipse, arabirim türünün birlikte değişken türünde bir parametresi, temsilci türünün değişken karşıtı türünde bir parametresini belirtmek için kullanılabilir.  
  
 Karşıt tür `in` parametresi anahtar kelimeyle`In` (Visual Basic'teki anahtar kelime, `-` [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)için) işaretlenir. Değişken karşıtı türde bir parametreyi, bir arabirime ait olan bir yöntemin bir parametresinin türü olarak veya bir temsilcinin bir parametresinin türü olarak kullanabilirsiniz. Değişken karşıtı türde bir parametreyi, bir arabirim yöntemi için genel türde bir kısıtlama olarak kullanabilirsiniz.  
  
 Yalnızca arabirim türlerinin ve temsilci türlerinin değişken türünde parametreleri olabilir. Bir arabirim veya temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
 Visual Basic ve C#, birlikte değişken veya değişken karşıtı türde parametrelerin kullanılmasına ilişkin kuralların ihlal edilmesine veya arabirimlerden ve temsilcilerden başka türde tür parametrelerine birlikte değişken veya değişken karşıtı ek açıklamalar eklenmesine izin vermez. [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) bu tür denetimleri <xref:System.TypeLoadException> gerçekleştirmez, ancak kuralları ihlal eden bir tür yüklemeye çalışırsanız bir atılır.  
  
 Bilgi ve örnek kod için Genel [Arabirimlerde Varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Genel Arabirimlerde Varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)bakın.  

## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Değişken Genel Arabirim ve Temsilci Türleri Listesi
 .NET Framework 4'te, aşağıdaki arabirim ve temsilci türleri eşdeğişken ve/veya karşıt tür parametrelerine sahiptir.  
  
|Tür|Birlikte değişken türde parametreler|Değişken karşıtı türde parametreler|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>Hedef<xref:System.Action%6016>||Evet|  
|<xref:System.Comparison%601>||Evet|  
|<xref:System.Converter%602>|Evet|Evet|  
|<xref:System.Func%601>|Evet||  
|<xref:System.Func%602>Hedef<xref:System.Func%6017>|Evet|Evet|  
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

- [Covariance ve Contravariance (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Covariance ve Contravariance (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Temsilcilerde Varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Temsilcilerde Varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
