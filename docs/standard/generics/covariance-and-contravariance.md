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
ms.openlocfilehash: b11b5fc93d9b7289e62d6abc9d3ca19027a107c5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287564"
---
# <a name="covariance-and-contravariance-in-generics"></a>Genel Türlerde Kovaryans ve Kontravaryans
Kovaryans ve değişken Varyans, başlangıçta belirtilenden daha fazla türetilmiş bir tür (daha fazla özel) veya daha az türetilmiş bir tür (daha az özel) kullanma olanağına işaret eden terimlerdir. Genel tür parametreleri, genel türleri atamakta ve kullanmakta daha fazla esneklik sağlamak için birlikte değişme ve değişken karşıtlığını destekler. Bir tür sisteminden söz ederken, birlikte değişme, değişken karşıtlığı ve değişmezlik terimlerinin tanımları aşağıdaki gibidir. Örneklerde adlı bir temel sınıf `Base` ve adlı türetilmiş bir sınıf varsayılır `Derived` .  
  
- `Covariance`  
  
     Özgün olarak belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.  
  
     `IEnumerable<Derived>`Türünde bir değişkene (Visual Basic) bir örneği atayabilirsiniz `IEnumerable(Of Derived)` `IEnumerable<Base>` .  
  
- `Contravariance`  
  
     Orijinal olarak belirtilenden daha genel (daha az türetilmiş) bir tür belirtmenize olanak tanır.  
  
     `Action<Base>`Türünde bir değişkene (Visual Basic) bir örneği atayabilirsiniz `Action(Of Base)` `Action<Derived>` .  
  
- `Invariance`  
  
     Yalnızca orijinal olarak belirtilen türü kullanabileceğiniz anlamına gelir; bu nedenle, değişmez bir genel tür parametresi birlikte değişken veya değişken karşıtı değildir.  
  
     (Visual Basic) bir örneğini, `List<Base>` `List(Of Base)` `List<Derived>` veya tam tersi bir değişkene atayamazsınız.  
  
 Covaryant türü parametreleri, aşağıdaki kodda gösterildiği gibi sıradan çok [biçimlilik](../../csharp/programming-guide/classes-and-structs/polymorphism.md)gibi görünen atamalar yapmayı sağlar.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601>Sınıfı <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygular, bu nedenle `List<Derived>` ( `List(Of Derived)` Visual Basic) uygular `IEnumerable<Derived>` . Birlikte değişken tür parametresi geri kalanını yapar.  
  
 Diğer taraftan, birlikte değişkenlik mantığa aykırı görünüyor. Aşağıdaki örnek, türünde bir temsilci oluşturur `Action<Base>` ( `Action(Of Base)` Visual Basic) ve ardından bu temsilciyi, türünde bir değişkene atar `Action<Derived>` .  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Geri gibi görünüyor, ancak derleyen ve çalışan, tür açısından güvenli koddur. Lambda ifadesi, atandığı temsilciyle eşleşir, bu nedenle, türünde bir parametre alan `Base` ve dönüş değeri olmayan bir yöntemi tanımlar. Temsilcinin tür parametresi değişken karşıtı olduğundan, ortaya çıkan temsilci bir tür değişkenine atanabilir `Action<Derived>` `T` <xref:System.Action%601> . `T`Bir parametre türü belirttiğinden kod tür güvenlidir. Türünün temsilcisi, `Action<Base>` türü bir temsilciymiş gibi çağrıldığında `Action<Derived>` , bağımsız değişkeninin türünde olması gerekir `Derived` . Metodun parametresi türünde olduğundan, bu bağımsız değişken her zaman temeldeki yönteme güvenli şekilde geçirilebilir `Base` .  
  
 Genel olarak, birlikte değişken türünde bir parametre bir temsilcinin dönüş türü olarak kullanılabilir ve değişken karşıtı türü parametreler parametre türleri olarak kullanılabilir. Bir arabirim için, birlikte değişken türü parametreler arabirimin yöntemlerinin dönüş türleri olarak kullanılabilir ve değişken karşıtı türü parametreler arabirimin yöntemlerinin parametre türleri olarak kullanılabilir.  
  
 Kovaryans ve değişken Varyans, toplu olarak *fark*olarak adlandırılır. Birlikte değişken veya değişken karşıtı olarak işaretlenmemiş genel tür parametresi, *sabit*olarak adlandırılır. Genel dil çalışma zamanında değişken ile ilgili gerçeklerin kısa bir özeti:  
  
- .NET Framework 4 ' te, değişken tür parametreleri genel arabirim ve genel temsilci türleriyle kısıtlıdır.  
  
- Bir genel arabirim veya genel temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
- Değişken yalnızca başvuru türleri için geçerlidir; değişken türünde bir parametre için bir değer türü belirtirseniz, bu tür parametresi, sonuç olarak oluşturulan tür için değişmezdir.  
  
- Değişken, temsilci birleşimi için geçerli değildir. Diğer bir deyişle, iki tür temsilci `Action<Derived>` ve `Action<Base>` ( `Action(Of Derived)` ve `Action(Of Base)` Visual Basic), sonuç tür kullanımı güvenli olsa da, ikinci temsilciyi birinciyle birleştiremezsiniz. Varyans, ikinci temsilcinin türünde bir değişkene atanmasına izin verir `Action<Derived>` , ancak temsilciler yalnızca türleri tam olarak eşleşiyorsa birleştirebilir.

<a name="InterfaceCovariantTypeParameters"></a>
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Birlikte Değişen Tür Parametreleriyle Genel Arabirimler  
 .NET Framework 4 ' te başlayarak, bazı genel arabirimlerin birlikte değişken tür parametreleri vardır; Örneğin: <xref:System.Collections.Generic.IEnumerable%601> ,, <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Linq.IQueryable%601> , ve <xref:System.Linq.IGrouping%602> . Bu arabirimlerin tüm tür parametreleri birlikte değişen olduğundan, tür parametreleri yalnızca üyelerin dönüş türleri için kullanılır.  
  
 Aşağıdaki örnekte, birlikte değişen tür parametreleri gösterilmektedir. Örnek iki tür tanımlar: `Base` `PrintBases` `IEnumerable<Base>` ( `IEnumerable(Of Base)` Visual Basic) alan ve öğeleri yazdıran adlı statik bir yöntemi vardır. `Derived`öğesinden devralır `Base` . Örnek boş `List<Derived>` ( `List(Of Derived)` Visual Basic) oluşturur ve bu türün, `PrintBases` atama olmadan bir değişken türüne geçirilebileceğini ve atanabileceğini gösterir `IEnumerable<Base>` . <xref:System.Collections.Generic.List%601><xref:System.Collections.Generic.IEnumerable%601>tek bir covaryant türü parametresine sahip olan uygular. Covaryant türü parametresi, yerine bir örneğinin kullanılma nedenidir `IEnumerable<Derived>` `IEnumerable<Base>` .  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Değişken Karşıtı Genel Tür Parametrelerle Genel Arabirimler  
 .NET Framework 4 ' te başlayarak, bazı genel arabirimlerin değişken tür parametreleri vardır; Örneğin: <xref:System.Collections.Generic.IComparer%601> , <xref:System.IComparable%601> , ve <xref:System.Collections.Generic.IEqualityComparer%601> . Bu arabirimlerin yalnızca değişken karşıtı türde parametreleri olduğundan, tür parametreleri yalnızca arabirimlerin üyelerinde parametre türleri olarak kullanılır.  
  
 Aşağıdaki örnekte, değişken karşıtı tür parametreleri gösterilmektedir. Örnek, bir soyut ( `MustInherit` Visual Basic) `Shape` sınıfında bir `Area` özelliği tanımlar. Örnek ayrıca `ShapeAreaComparer` uygulayan bir sınıf tanımlar `IComparer<Shape>` ( `IComparer(Of Shape)` Visual Basic). <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType>Yönteminin uygulanması özelliğin değerine dayalıdır `Area` , bu nedenle `ShapeAreaComparer` `Shape` nesneleri alana göre sıralamak için kullanılabilir.  
  
 `Circle`Sınıfı devralır `Shape` ve geçersiz kılar `Area` . Örnek <xref:System.Collections.Generic.SortedSet%601> `Circle` , `IComparer<Circle>` ( `IComparer(Of Circle)` Visual Basic içinde) alan bir Oluşturucu kullanarak bir nesne oluşturur. Ancak, bir geçirmek yerine, `IComparer<Circle>` örnek, `ShapeAreaComparer` uygulayan bir nesnesi geçirir `IComparer<Shape>` . Örnek, `Shape` `Circle` genel arabirimin tür parametresi değişken karşıtı olduğundan, kod daha türetilmiş bir türün () bir karşılaştırıcısı için çağrı yaparken daha az türetilmiş bir tür () karşılaştırıcısı geçirebilir <xref:System.Collections.Generic.IComparer%601> .  
  
 Öğesine yeni bir `Circle` nesne eklendiğinde `SortedSet<Circle>` , `IComparer<Shape>.Compare` nesnesinin yöntemi ( `IComparer(Of Shape).Compare` Visual Basic yöntemi), `ShapeAreaComparer` her yeni öğe varolan bir öğeyle karşılaştırıldığı zaman çağrılır. Metodun () parametre türü, `Shape` geçirilmekte olan türden daha az türetilir ( `Circle` ), bu nedenle çağrı tür güvenlidir. Değişken Varyans, `ShapeAreaComparer` tek bir türün bir koleksiyonunu ve ' den türetilen bir tür karma koleksiyonunu sıralamanıza olanak sağlar `Shape` .  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Değişken Türü Parametrelerle Genel Temsilciler  
 .NET Framework 4 ' te, gibi `Func` genel temsilcilerin <xref:System.Func%602> birlikte değişken dönüş türleri ve değişken karşıtı parametre türleri vardır. Gibi `Action` genel temsilcilerin değişken karşıtı <xref:System.Action%602> parametre türleri vardır. Bu, temsilcilerin daha fazla türetilmiş parametre türüne sahip değişkenlere atanabileceği ve (Genel Temsilciler söz konusu olduğunda `Func` ) daha az türetilmiş dönüş türlerinden atanabileceği anlamına gelir.  
  
> [!NOTE]
> Genel temsilcilerin son genel tür parametresi, `Func` temsilci imzasında döndürülen değerin türünü belirtir. Değişkenle birlikte değişken ( `out` anahtar sözcük) ve diğer genel tür parametreleri değişken karşıtı ( `in` anahtar sözcük).  
  
 Aşağıdaki kod bunu göstermektedir. İlk kod parçası adlı bir sınıfı `Base` , devralan adlı bir sınıfı `Derived` `Base` ve `static` adlı bir yöntemi (Visual Basic) olan başka bir sınıfı tanımlar `Shared` `MyMethod` . Yöntemi bir örneğini alır `Base` ve bir örneğini döndürür `Derived` . (Bağımsız değişken öğesinin bir örneği ise `Derived` , `MyMethod` döndürür; bağımsız değişken öğesinin bir örneği ise `Base` , `MyMethod` Yeni bir örneğini döndürür `Derived` .) ' De `Main()` , örnek, `Func<Base, Derived>` `Func(Of Base, Derived)` öğesini temsil eden (Visual Basic olarak) bir örneğini oluşturur `MyMethod` ve bunu değişkende depolar `f1` .  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 İkinci kod parçası, temsilcinin tür bir değişkene atanabildiğinden `Func<Base, Base>` ( `Func(Of Base, Base)` Visual Basic), dönüş türü birlikte değişken olduğundan gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Üçüncü kod parçası, temsilci türünde bir değişkene atanabildiğinden `Func<Derived, Derived>` ( `Func(Of Derived, Derived)` Visual Basic), parametre türü değişken karşıtı olduğundan gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Son kod parçası, temsilcinin, değişken karşıtı `Func<Derived, Base>` `Func(Of Derived, Base)` parametre türünün ve covaryant dönüş türünün etkilerini birleştiren bir tür değişkenine (Visual Basic) atanabileceği gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Genel ve Genel Olmayan Temsilcilerde Değişken  
 Önceki kodda, imzası `MyMethod` oluşturulan genel temsilcinin imzasıyla tam olarak eşleşir: `Func<Base, Derived>` ( `Func(Of Base, Derived)` Visual Basic). Örnek, tüm temsilci türleri genel temsilci türünden oluşturulduğu sürece, bu genel temsilcinin daha fazla türetilmiş parametre türüne ve daha az türetilmiş dönüş türüne sahip değişkenlerde veya yöntem parametrelerinde depolanabileceğini gösterir <xref:System.Func%602> .  
  
 Bu önemli bir noktadır. Genel temsilcilerin tür parametrelerindeki Kovaryans ve değişken farkının etkileri, sıradan temsilci bağlamasındaki Kovaryans ve değişken varyans efektlerine benzerdir ( [temsilcilerin Içindeki varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [temsillerdeki varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)gibi). Ancak, temsilci bağlamadaki değişken, yalnızca değişken türde parametreleri olan genel temsilci türleriyle değil, tüm temsilci türleriyle birlikte çalışır. Ayrıca, temsilci bağlamada değişken, bir yöntemin daha kısıtlayıcı parametre türleri ve daha az kısıtlayıcı dönüş türü olan herhangi bir temsilciye bağlanmasına olanak tanırken, genel temsilcilerin atanması yalnızca her iki temsilci türünün de aynı genel tür tanımından oluşturulması durumunda çalışır.  
  
 Aşağıdaki örnekte, temsilci bağlamadaki değişkenin ve genel tür parametrelerindeki değişkenin birleşik etkisi gösterilmektedir. Örnek, en az türetilen ( `Type1` ) ile en türetilmiş () arasında üç tür içeren bir tür hiyerarşisi tanımlar `Type3` . Normal temsilci bağlamasındaki Varyans, parametre türü ve dönüş türü olan bir yöntemi bir parametre türü `Type1` `Type3` `Type2` ve dönüş türü olan genel bir temsilciye bağlamak için kullanılır `Type2` . Sonuçta elde edilen genel temsilci, genel `Type3` `Type1` tür parametrelerinin Kovaryans ve değişken varyans kullanılarak genel temsilci türü bir parametreye ve dönüş türüne sahip olan başka bir değişkene atanır. İkinci atama, aynı genel tür tanımından, bu durumda, hem değişken türünün hem de temsilci türünün oluşturulmasını gerektirir <xref:System.Func%602> .  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="defining-variant-generic-interfaces-and-delegates"></a>Değişken Genel Arabirimleri ve Temsilcileri Tanımlama
 .NET Framework 4 ' ten başlayarak, Visual Basic ve C# ' nin genel tür parametrelerini birlikte değişken veya değişken karşıtı olarak işaretlemenizi sağlayan anahtar kelimeleridir.  
  
> [!NOTE]
> .NET Framework sürüm 2.0 ile başlayarak, genel dil çalışma zamanı, genel tür parametrelerinde değişken açıklamalarını destekler. .NET Framework 4 ' ten önce, bu ek açıklamaları içeren genel bir sınıf tanımlamanın tek yolu, sınıfı [Ilasm. exe (Il Assembler)](../../framework/tools/ilasm-exe-il-assembler.md) ile derleyerek veya dinamik bir derlemede yayarak Microsoft ara dili 'NI (MSIL) kullanmaktır.  
  
 Birlikte değişken tür parametresi, `out` MSIL derleyicisi için Visual Basic anahtar sözcüğüyle `Out` (anahtar sözcüğüyle `+` ) işaretlenir. [MSIL Assembler](../../framework/tools/ilasm-exe-il-assembler.md) Birlikte değişken türünde bir parametreyi, bir arabirime ait olan bir yöntemin dönüş değeri olarak veya bir temsilcinin dönüş türü olarak kullanabilirsiniz. Birlikte değişken türünde bir parametreyi, arabirim yöntemleri için genel türde bir kısıtlayıcı olarak kullanamazsınız.  
  
> [!NOTE]
> Bir arabirimin bir yöntemi genel temsilci türünde bir parametreye sahipse, arabirim türünün birlikte değişken türünde bir parametresi, temsilci türünün değişken karşıtı türünde bir parametresini belirtmek için kullanılabilir.  
  
 Değişken karşıtı bir tür parametresi, `in` MSIL derleyicisi için Visual Basic anahtar sözcüğüyle ( `In` anahtar sözcüğüyle `-` ) işaretlenir [MSIL Assembler](../../framework/tools/ilasm-exe-il-assembler.md). Değişken karşıtı türde bir parametreyi, bir arabirime ait olan bir yöntemin bir parametresinin türü olarak veya bir temsilcinin bir parametresinin türü olarak kullanabilirsiniz. Değişken karşıtı türde bir parametreyi, bir arabirim yöntemi için genel türde bir kısıtlama olarak kullanabilirsiniz.  
  
 Yalnızca arabirim türlerinin ve temsilci türlerinin değişken türünde parametreleri olabilir. Bir arabirim veya temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
 Visual Basic ve C#, birlikte değişken veya değişken karşıtı türde parametrelerin kullanılmasına ilişkin kuralların ihlal edilmesine veya arabirimlerden ve temsilcilerden başka türde tür parametrelerine birlikte değişken veya değişken karşıtı ek açıklamalar eklenmesine izin vermez. [MSIL](../../framework/tools/ilasm-exe-il-assembler.md) derleyicisi böyle denetimler gerçekleştirmez, ancak <xref:System.TypeLoadException> kuralları ihlal eden bir tür yüklemeye çalışırsanız bir oluşturulur.  
  
 Bilgi ve örnek kod için bkz. [Genel Arabirimlerde Varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Genel arabirimlerde varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  

## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Değişken Genel Arabirim ve Temsilci Türleri Listesi
 .NET Framework 4 ' te, aşağıdaki arabirim ve temsilci türlerinde birlikte değişken ve/veya değişken karşıtı tür parametreleri vardır.  
  
|Tür|Birlikte değişken türde parametreler|Değişken karşıtı türde parametreler|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>Hedef<xref:System.Action%6016>||Yes|  
|<xref:System.Comparison%601>||Yes|  
|<xref:System.Converter%602>|Yes|Yes|  
|<xref:System.Func%601>|Yes||  
|<xref:System.Func%602>Hedef<xref:System.Func%6017>|Yes|Yes|  
|<xref:System.IComparable%601>||Yes|  
|<xref:System.Predicate%601>||Yes|  
|<xref:System.Collections.Generic.IComparer%601>||Yes|  
|<xref:System.Collections.Generic.IEnumerable%601>|Yes||  
|<xref:System.Collections.Generic.IEnumerator%601>|Yes||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Yes|  
|<xref:System.Linq.IGrouping%602>|Yes||  
|<xref:System.Linq.IOrderedEnumerable%601>|Yes||  
|<xref:System.Linq.IOrderedQueryable%601>|Yes||  
|<xref:System.Linq.IQueryable%601>|Yes||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kovaryans ve değişken varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kovaryans ve değişken varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Temsilcilerde varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Temsilcilerde varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
