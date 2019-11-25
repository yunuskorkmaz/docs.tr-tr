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
ms.openlocfilehash: ee8cc1b677ad6f6c2718c155edbba632df38dbd3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974693"
---
# <a name="covariance-and-contravariance-in-generics"></a>Genel Türlerde Kovaryans ve Kontravaryans
Kovaryans ve değişken Varyans, başlangıçta belirtilenden daha fazla türetilmiş bir tür (daha fazla özel) veya daha az türetilmiş bir tür (daha az özel) kullanma olanağına işaret eden terimlerdir. Genel tür parametreleri, genel türleri atamakta ve kullanmakta daha fazla esneklik sağlamak için birlikte değişme ve değişken karşıtlığını destekler. Bir tür sisteminden söz ederken, birlikte değişme, değişken karşıtlığı ve değişmezlik terimlerinin tanımları aşağıdaki gibidir. Örneklerde `Base` adlı bir temel sınıf ve `Derived`adlı türetilmiş bir sınıf varsayılır.  
  
- `Covariance`  
  
     Özgün olarak belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.  
  
     `IEnumerable<Base>`türünde bir değişkene bir `IEnumerable<Derived>` (Visual Basic`IEnumerable(Of Derived)`) örneği atayabilirsiniz.  
  
- `Contravariance`  
  
     Orijinal olarak belirtilenden daha genel (daha az türetilmiş) bir tür belirtmenize olanak tanır.  
  
     `Action<Derived>`türünde bir değişkene bir `Action<Base>` (Visual Basic`Action(Of Base)`) örneği atayabilirsiniz.  
  
- `Invariance`  
  
     Yalnızca orijinal olarak belirtilen türü kullanabileceğiniz anlamına gelir; bu nedenle, değişmez bir genel tür parametresi birlikte değişken veya değişken karşıtı değildir.  
  
     Bir `List<Base>` (Visual Basic`List(Of Base)`) örneğini `List<Derived>` türünde bir değişkene atayamazsınız veya bunun tersini yapamazsınız.  
  
 Covaryant türü parametreleri, aşağıdaki kodda gösterildiği gibi sıradan çok [biçimlilik](../../csharp/programming-guide/classes-and-structs/polymorphism.md)gibi görünen atamalar yapmayı sağlar.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601> sınıfı <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygular, bu nedenle `List<Derived>` (Visual Basic`List(Of Derived)`) `IEnumerable<Derived>`uygular. Birlikte değişken tür parametresi geri kalanını yapar.  
  
 Diğer taraftan, birlikte değişkenlik mantığa aykırı görünüyor. Aşağıdaki örnek, `Action<Base>` (`Action(Of Base)` Visual Basic) türünde bir temsilci oluşturur ve bu temsilciyi `Action<Derived>`türünde bir değişkene atar.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Geri gibi görünüyor, ancak derleyen ve çalışan, tür açısından güvenli koddur. Lambda ifadesi, atandığı temsilciyle eşleşir, bu nedenle `Base` türünde bir parametre alan ve dönüş değeri olmayan bir yöntemi tanımlar. <xref:System.Action%601> temsilcisinin tür parametresi `T` değişken karşıtı olduğundan, elde edilen temsilci `Action<Derived>` türünde bir değişkene atanabilir. `T` bir parametre türü belirttiğinden, kod tür açısından güvenlidir. `Action<Base>` temsilci türü, `Action<Derived>`türünde bir temsilciymiş gibi çağrıldığında, bağımsız değişkeninin `Derived`türünde olması gerekir. Metodun parametresi `Base`türünde olduğundan, bu bağımsız değişken her zaman temeldeki yönteme güvenli şekilde geçirilebilir.  
  
 Genel olarak, birlikte değişken türünde bir parametre bir temsilcinin dönüş türü olarak kullanılabilir ve değişken karşıtı türü parametreler parametre türleri olarak kullanılabilir. Bir arabirim için, birlikte değişken türü parametreler arabirimin yöntemlerinin dönüş türleri olarak kullanılabilir ve değişken karşıtı türü parametreler arabirimin yöntemlerinin parametre türleri olarak kullanılabilir.  
  
 Kovaryans ve değişken Varyans, toplu olarak *fark*olarak adlandırılır. Birlikte değişken veya değişken karşıtı olarak işaretlenmemiş genel tür parametresi, *sabit*olarak adlandırılır. Genel dil çalışma zamanında değişken ile ilgili gerçeklerin kısa bir özeti:  
  
- .NET Framework 4 ' te, değişken tür parametreleri genel arabirim ve genel temsilci türleriyle kısıtlıdır.  
  
- Bir genel arabirim veya genel temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
- Değişken yalnızca başvuru türleri için geçerlidir; değişken türünde bir parametre için bir değer türü belirtirseniz, bu tür parametresi, sonuç olarak oluşturulan tür için değişmezdir.  
  
- Değişken, temsilci birleşimi için geçerli değildir. Diğer bir deyişle, `Action<Derived>` ve `Action<Base>` (`Action(Of Derived)` ve `Action(Of Base)` Visual Basic) iki temsilci verildiğinde, sonuç tür kullanımı güvenli olsa da, ikinci temsilciyi birinciyle birleştiremezsiniz. Varyans, ikinci temsilcinin `Action<Derived>`türünde bir değişkene atanmasına izin verir, ancak temsilciler yalnızca türleri tam olarak eşleşiyorsa birleştirebilirler.

<a name="InterfaceCovariantTypeParameters"></a>
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Birlikte Değişen Tür Parametreleriyle Genel Arabirimler  
 .NET Framework 4 ' te başlayarak, bazı genel arabirimlerin birlikte değişken tür parametreleri vardır; Örneğin: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>ve <xref:System.Linq.IGrouping%602>. Bu arabirimlerin tüm tür parametreleri birlikte değişen olduğundan, tür parametreleri yalnızca üyelerin dönüş türleri için kullanılır.  
  
 Aşağıdaki örnekte, birlikte değişen tür parametreleri gösterilmektedir. Örnek iki tür tanımlar: `Base`, `IEnumerable<Base>` (`IEnumerable(Of Base)` Visual Basic) alan `PrintBases` adlı statik bir metoda sahiptir ve öğeleri yazdırır. `Derived` `Base`devralır. Örnek, boş bir `List<Derived>` (Visual Basic`List(Of Derived)`) oluşturur ve bu türün `PrintBases` 'ye geçirilebileceğini ve atama olmadan `IEnumerable<Base>` türünde bir değişkene atandığını gösterir. <xref:System.Collections.Generic.List%601>, tek bir covaryant türü parametresine sahip <xref:System.Collections.Generic.IEnumerable%601>uygular. Covaryant türü parametresi, `IEnumerable<Base>`yerine bir `IEnumerable<Derived>` örneğinin kullanılma nedenidir.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Değişken Karşıtı Genel Tür Parametrelerle Genel Arabirimler  
 .NET Framework 4 ' te başlayarak, bazı genel arabirimlerin değişken tür parametreleri vardır; Örneğin: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>ve <xref:System.Collections.Generic.IEqualityComparer%601>. Bu arabirimlerin yalnızca değişken karşıtı türde parametreleri olduğundan, tür parametreleri yalnızca arabirimlerin üyelerinde parametre türleri olarak kullanılır.  
  
 Aşağıdaki örnekte, değişken karşıtı tür parametreleri gösterilmektedir. Örnek, bir `Area` özelliği olan `Shape` sınıfında bir soyut (`MustInherit` Visual Basic) tanımlar. Örnek ayrıca, `IComparer<Shape>` uygulayan bir `ShapeAreaComparer` sınıfını tanımlar (`IComparer(Of Shape)` Visual Basic). <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> yönteminin uygulanması `Area` özelliğinin değerini temel alır, bu nedenle `ShapeAreaComparer` `Shape` nesneleri alana göre sıralamak için kullanılabilir.  
  
 `Circle` sınıfı `Shape` devralır ve geçersiz kılmalar `Area`. Örnek, `IComparer<Circle>` (`IComparer(Of Circle)` Visual Basic) alan bir Oluşturucu kullanarak `Circle` nesneleri <xref:System.Collections.Generic.SortedSet%601> oluşturur. Ancak, bir `IComparer<Circle>`geçirmek yerine, örnek `IComparer<Shape>`uygulayan bir `ShapeAreaComparer` nesnesi geçirir. Bu örnek, <xref:System.Collections.Generic.IComparer%601> genel arabiriminin tür parametresi değişken karşıtı olduğundan, kod daha türetilmiş bir tür karşılaştırıcıyı (`Circle`) aradığında, daha az türetilmiş bir tür karşılaştırıcısı geçirebilir (`Shape`).  
  
 `SortedSet<Circle>`yeni bir `Circle` nesnesi eklendiğinde, yeni öğe var olan bir öğeyle karşılaştırıldığı her seferinde Visual Basic nesnesinin `IComparer<Shape>.Compare` yöntemi (`ShapeAreaComparer``IComparer(Of Shape).Compare` yöntemi) çağırılır. Metodun (`Shape`) parametre türü, geçirilmekte olan türden daha az türetilir (`Circle`), bu nedenle çağrı tür güvenlidir. Değişken Varyans, `ShapeAreaComparer` her türlü tek türdeki bir koleksiyonu ve `Shape`türetilen bir karma tür koleksiyonunu sıralamanıza olanak sağlar.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Değişken Türü Parametrelerle Genel Temsilciler  
 .NET Framework 4 ' te, <xref:System.Func%602>gibi `Func` genel temsilcilerin birlikte değişken dönüş türleri ve değişken karşıtı parametre türleri vardır. <xref:System.Action%602>gibi `Action` genel temsilcilerin değişken karşıtı parametre türleri vardır. Bu, temsilcilerin daha fazla türetilmiş parametre türüne sahip değişkenlere atanabileceği ve (`Func` Genel Temsilciler durumunda) daha az türetilmiş dönüş türleri olması anlamına gelir.  
  
> [!NOTE]
> `Func` genel temsilcilerin son genel tür parametresi, temsilci imzasında döndürülen değerin türünü belirtir. Değişkenle birlikte değişken (`out` anahtar sözcüğü), diğer genel tür parametreleri değişken karşıtı (`in` anahtar sözcüktür).  
  
 Aşağıdaki kod bunu göstermektedir. İlk kod parçası `Base`adlı bir sınıfı, `Base`devralan `Derived` adlı bir sınıfı ve`Shared` adlı `static` bir yöntemi olan başka bir sınıfı tanımlar. Yöntemi bir `Base` örneğini alır ve `Derived`örneğini döndürür. (Bağımsız değişken bir `Derived`örneğidir `MyMethod` döndürür; bağımsız değişken bir `Base`örneğidir `MyMethod` yeni bir `Derived`örneğini döndürür.) `Main()`, örnek, `MyMethod`temsil eden bir `Func<Base, Derived>` örneği (`Func(Of Base, Derived)` Visual Basic) oluşturur ve `f1`değişkenine depolar.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 İkinci kod parçası, temsilcinin `Func<Base, Base>` (`Func(Of Base, Base)` Visual Basic) türünde bir değişkene atanabildiğinden, dönüş türü birlikte değişken olduğundan gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Üçüncü kod parçası, temsilci `Func<Derived, Derived>` (`Func(Of Derived, Derived)` Visual Basic) türünde bir değişkene atanabildiğinden, parametre türü değişken karşıtı olduğundan gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Son kod parçası, temsilcinin, değişken karşıtı parametre türünün ve covaryant dönüş türünün etkilerini birleştiren `Func<Derived, Base>` (`Func(Of Derived, Base)` Visual Basic) türünde bir değişkene atanabilirler.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Genel ve Genel Olmayan Temsilcilerde Değişken  
 Yukarıdaki kodda `MyMethod` imzası, oluşturulan genel temsilcinin imzasıyla tamamen eşleşir: `Func<Base, Derived>` (Visual Basic içinde`Func(Of Base, Derived)`). Örnek, bu genel temsilcinin daha fazla türetilmiş parametre türleri ve daha az türetilmiş dönüş türleri olan değişkenlerde veya yöntem parametrelerinde depolanabileceğini, tüm temsilci türlerinin <xref:System.Func%602>genel temsilci türünden oluşturulduğu sürece gösterir.  
  
 Bu önemli bir noktadır. Genel temsilcilerin tür parametrelerindeki Kovaryans ve değişken varyans etkileri, sıradan temsilci bağlamasındaki Kovaryans ve değişken varyans efektlerine benzerdir ( [temsilcilerinC#()](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [temsillerdeki varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)içindeki varyansı görün). Ancak, temsilci bağlamadaki değişken, yalnızca değişken türde parametreleri olan genel temsilci türleriyle değil, tüm temsilci türleriyle birlikte çalışır. Ayrıca, temsilci bağlamada değişken, bir yöntemin daha kısıtlayıcı parametre türleri ve daha az kısıtlayıcı dönüş türü olan herhangi bir temsilciye bağlanmasına olanak tanırken, genel temsilcilerin atanması yalnızca her iki temsilci türünün de aynı genel tür tanımından oluşturulması durumunda çalışır.  
  
 Aşağıdaki örnekte, temsilci bağlamadaki değişkenin ve genel tür parametrelerindeki değişkenin birleşik etkisi gösterilmektedir. Örnek, en az türetilen (`Type1`) en türetilmiş (`Type3`) türünden üç tür içeren bir tür hiyerarşisi tanımlar. Sıradan temsilci bağlamasındaki Varyans, `Type1` parametre türüyle bir `Type3` dönüş türü ve bir `Type2` parametre türü ve `Type2`dönüş türü olan bir genel temsilciye bir yöntemi bağlamak için kullanılır. Sonuçta elde edilen genel temsilci, genel temsilci türü bir parametreye sahip `Type3` ve dönüş `Type1`türü bir parametreye sahip olan başka bir değişkene atanır, bu da genel tür parametrelerinin Kovaryans ve değişken varyans. İkinci atama hem değişken türü hem de temsilci türünün aynı genel tür tanımından oluşturulmasını gerektirir, bu durumda <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="defining-variant-generic-interfaces-and-delegates"></a>Değişken Genel Arabirimleri ve Temsilcileri Tanımlama
 .NET Framework 4 ' ten başlayarak, Visual Basic ve C# arabirimlerin ve temsilcilerin genel tür parametrelerini birlikte değişken veya değişken karşıtı olarak işaretlemenizi sağlayan anahtar sözcüklere sahip olursunuz.  
  
> [!NOTE]
> .NET Framework sürüm 2.0 ile başlayarak, genel dil çalışma zamanı, genel tür parametrelerinde değişken açıklamalarını destekler. .NET Framework 4 ' ten önce, bu ek açıklamaları içeren genel bir sınıf tanımlamanın tek yolu, sınıfı [Ilasm. exe (Il Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) ile derleyerek veya dinamik bir derlemede yayarak Microsoft ara dili 'NI (MSIL) kullanmaktır.  
  
 Covaryant türü parametresi, Visual Basic`Out` anahtar sözcüğüyle ( [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)için `+`) `out` işaretlenir. Birlikte değişken türünde bir parametreyi, bir arabirime ait olan bir yöntemin dönüş değeri olarak veya bir temsilcinin dönüş türü olarak kullanabilirsiniz. Birlikte değişken türünde bir parametreyi, arabirim yöntemleri için genel türde bir kısıtlayıcı olarak kullanamazsınız.  
  
> [!NOTE]
> Bir arabirimin bir yöntemi genel temsilci türünde bir parametreye sahipse, arabirim türünün birlikte değişken türünde bir parametresi, temsilci türünün değişken karşıtı türünde bir parametresini belirtmek için kullanılabilir.  
  
 Değişken karşıtı bir tür parametresi, Visual Basic`In` anahtar sözcüğüyle ( [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)için `-`) `in` işaretlenir. Değişken karşıtı türde bir parametreyi, bir arabirime ait olan bir yöntemin bir parametresinin türü olarak veya bir temsilcinin bir parametresinin türü olarak kullanabilirsiniz. Değişken karşıtı türde bir parametreyi, bir arabirim yöntemi için genel türde bir kısıtlama olarak kullanabilirsiniz.  
  
 Yalnızca arabirim türlerinin ve temsilci türlerinin değişken türünde parametreleri olabilir. Bir arabirim veya temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
 Visual Basic ve C#, birlikte değişken veya değişken karşıtı türde parametrelerin kullanılmasına ilişkin kuralların ihlal edilmesine veya arabirimlerden ve temsilcilerden başka türde tür parametrelerine birlikte değişken veya değişken karşıtı ek açıklamalar eklenmesine izin vermez. [MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md) derleyicisi bu tür denetimleri gerçekleştirmez, ancak kuralları ihlal eden bir tür yüklemeyi denerseniz bir <xref:System.TypeLoadException> oluşturulur.  
  
 Bilgi ve örnek kod için bkz. [Genel Arabirimlerde Varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Genel Arabirimlerde Varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  

## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Değişken Genel Arabirim ve Temsilci Türleri Listesi
 .NET Framework 4 ' te, aşağıdaki arabirim ve temsilci türlerinde birlikte değişken ve/veya değişken karşıtı tür parametreleri vardır.  
  
|Tür|Birlikte değişken türde parametreler|Değişken karşıtı türde parametreler|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%6016> <xref:System.Action%601>||Evet|  
|<xref:System.Comparison%601>||Evet|  
|<xref:System.Converter%602>|Evet|Evet|  
|<xref:System.Func%601>|Evet||  
|<xref:System.Func%6017> <xref:System.Func%602>|Evet|Evet|  
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

- [Kovaryans ve değişken varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kovaryans ve değişken varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Temsilcilerde varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Temsilcilerde varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
