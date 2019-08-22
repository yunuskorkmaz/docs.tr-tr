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
ms.openlocfilehash: 26a1df8829a9b6398876658bdb5697ab3e6f87c8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666451"
---
# <a name="covariance-and-contravariance-in-generics"></a>Genel Türlerde Kovaryans ve Kontravaryans
<a name="top"></a>Kovaryans ve değişken Varyans, başlangıçta belirtilenden daha fazla türetilmiş bir tür (daha fazla özel) veya daha az türetilmiş bir tür (daha az özel) kullanma olanağına işaret eden terimlerdir. Genel tür parametreleri, genel türleri atamakta ve kullanmakta daha fazla esneklik sağlamak için birlikte değişme ve değişken karşıtlığını destekler. Bir tür sisteminden söz ederken, birlikte değişme, değişken karşıtlığı ve değişmezlik terimlerinin tanımları aşağıdaki gibidir. Örneklerde adlı bir temel sınıf `Base` ve adlı `Derived`türetilmiş bir sınıf varsayılır.  
  
- `Covariance`  
  
     Özgün olarak belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.  
  
     Türünde`IEnumerable(Of Derived)` `IEnumerable<Derived>` birdeğişkene(VisualBasic)birörneğiatayabilirsiniz`IEnumerable<Base>`.  
  
- `Contravariance`  
  
     Orijinal olarak belirtilenden daha genel (daha az türetilmiş) bir tür belirtmenize olanak tanır.  
  
     Türünde`Action(Of Base)` `Action<Base>` birdeğişkene(VisualBasic)birörneğiatayabilirsiniz`Action<Derived>`.  
  
- `Invariance`  
  
     Yalnızca orijinal olarak belirtilen türü kullanabileceğiniz anlamına gelir; bu nedenle, değişmez bir genel tür parametresi birlikte değişken veya değişken karşıtı değildir.  
  
     `List<Base>` `List<Derived>` (VisualBasic)birörneğini,veyatamtersibirdeğişkeneatayamazsınız.`List(Of Base)`  
  
 Covaryant türü parametreleri, aşağıdaki kodda gösterildiği gibi sıradan çok [biçimlilik](../../csharp/programming-guide/classes-and-structs/polymorphism.md)gibi görünen atamalar yapmayı sağlar.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 `List<Derived>` `List(Of Derived)` Sınıfı arabirimini uygular, bu nedenle (Visual Basic) uygular `IEnumerable<Derived>`. <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.IEnumerable%601> Birlikte değişken tür parametresi geri kalanını yapar.  
  
 Diğer taraftan, birlikte değişkenlik mantığa aykırı görünüyor. Aşağıdaki örnek, türünde `Action<Base>` bir temsilci oluşturur (`Action(Of Base)` Visual Basic) ve ardından bu temsilciyi, türünde `Action<Derived>`bir değişkene atar.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Geri gibi görünüyor, ancak derleyen ve çalışan, tür açısından güvenli koddur. Lambda ifadesi, atandığı temsilciyle eşleşir, bu nedenle, türünde `Base` bir parametre alan ve dönüş değeri olmayan bir yöntemi tanımlar. Temsilcinin tür parametresi `Action<Derived>` `T` değişken karşıtı olduğundan, ortaya çıkan temsilci bir tür değişkenine atanabilir. <xref:System.Action%601> Bir parametre türü `T` belirttiğinden kod tür güvenlidir. Türünün temsilcisi `Action<Base>` , türü `Action<Derived>`bir temsilciymiş gibi çağrıldığında, bağımsız değişkeninin türünde `Derived`olması gerekir. Metodun parametresi türünde `Base`olduğundan, bu bağımsız değişken her zaman temeldeki yönteme güvenli şekilde geçirilebilir.  
  
 Genel olarak, birlikte değişken türünde bir parametre bir temsilcinin dönüş türü olarak kullanılabilir ve değişken karşıtı türü parametreler parametre türleri olarak kullanılabilir. Bir arabirim için, birlikte değişken türü parametreler arabirimin yöntemlerinin dönüş türleri olarak kullanılabilir ve değişken karşıtı türü parametreler arabirimin yöntemlerinin parametre türleri olarak kullanılabilir.  
  
 Kovaryans ve değişken Varyans, toplu olarak *fark*olarak adlandırılır. Birlikte değişken veya değişken karşıtı olarak işaretlenmemiş genel tür parametresi, *sabit*olarak adlandırılır. Genel dil çalışma zamanında değişken ile ilgili gerçeklerin kısa bir özeti:  
  
- .NET Framework 4 ' te, değişken tür parametreleri genel arabirim ve genel temsilci türleriyle kısıtlıdır.  
  
- Bir genel arabirim veya genel temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
- Değişken yalnızca başvuru türleri için geçerlidir; değişken türünde bir parametre için bir değer türü belirtirseniz, bu tür parametresi, sonuç olarak oluşturulan tür için değişmezdir.  
  
- Değişken, temsilci birleşimi için geçerli değildir. Diğer bir deyişle `Action<Derived>` , iki tür temsilci ve `Action<Base>` (`Action(Of Derived)` ve `Action(Of Base)` Visual Basic), sonuç tür kullanımı güvenli olsa da, ikinci temsilciyi birinciyle birleştiremezsiniz. Varyans, ikinci temsilcinin türünde `Action<Derived>`bir değişkene atanmasına izin verir, ancak temsilciler yalnızca türleri tam olarak eşleşiyorsa birleştirebilir.  
  
 Aşağıdaki alt kısımlarda, değişkenle birlikte ve değişken karşıtı tür parametreleri ayrıntılı olarak açıklanmaktadır:  
  
- [Birlikte değişken tür parametrelerine sahip genel arabirimler](#InterfaceCovariantTypeParameters)  
  
- [Değişken karşıtı genel tür parametrelerine sahip genel arabirimler](#InterfaceCovariantTypeParameters)  
  
- [Değişken tür parametrelerine sahip genel Temsilciler](#DelegateVariantTypeParameters)  
  
- [VARIANT genel arabirimleri ve temsilcileri tanımlama](#DefiningVariantTypeParameters)  
  
- [Değişken genel arabirim ve temsilci türlerinin listesi](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Birlikte Değişen Tür Parametreleriyle Genel Arabirimler  
 .NET Framework 4 ' te başlayarak, bazı genel arabirimlerin birlikte değişken tür parametreleri vardır; <xref:System.Collections.Generic.IEnumerable%601>örneğin: <xref:System.Collections.Generic.IEnumerator%601> ,,<xref:System.Linq.IGrouping%602>, ve. <xref:System.Linq.IQueryable%601> Bu arabirimlerin tüm tür parametreleri birlikte değişen olduğundan, tür parametreleri yalnızca üyelerin dönüş türleri için kullanılır.  
  
 Aşağıdaki örnekte, birlikte değişen tür parametreleri gösterilmektedir. Örnek iki tür `Base` tanımlar: `IEnumerable<Base>` ( `PrintBases` `IEnumerable(Of Base)` Visual Basic) alan ve öğeleri yazdıran adlı statik bir yöntemi vardır. `Derived`öğesinden `Base`devralır. Örnek boş `List<Derived>` (`List(Of Derived)` Visual Basic) oluşturur ve bu `PrintBases` türün, atama olmadan bir değişken türüne `IEnumerable<Base>` geçirilebileceğini ve atanabileceğini gösterir. <xref:System.Collections.Generic.List%601>tek <xref:System.Collections.Generic.IEnumerable%601>bir covaryant türü parametresine sahip olan uygular. Covaryant türü parametresi, `IEnumerable<Derived>` `IEnumerable<Base>`yerine bir örneğinin kullanılma nedenidir.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Değişken Karşıtı Genel Tür Parametrelerle Genel Arabirimler  
 .NET Framework 4 ' te başlayarak, bazı genel arabirimlerin değişken tür parametreleri vardır; Örneğin: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, ve <xref:System.Collections.Generic.IEqualityComparer%601>. Bu arabirimlerin yalnızca değişken karşıtı türde parametreleri olduğundan, tür parametreleri yalnızca arabirimlerin üyelerinde parametre türleri olarak kullanılır.  
  
 Aşağıdaki örnekte, değişken karşıtı tür parametreleri gösterilmektedir. Örnek, bir soyut (`MustInherit` Visual Basic) `Shape` sınıfında bir `Area` özelliği tanımlar. Örnek ayrıca uygulayan `ShapeAreaComparer` `IComparer<Shape>` bir sınıf tanımlar (`IComparer(Of Shape)` Visual Basic). <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> Yönteminin `Area` uygulanması özelliğin değerine dayalıdır, bu nedenle `ShapeAreaComparer` nesneleri alana göre sıralamak `Shape` için kullanılabilir.  
  
 Sınıfı devralır `Shape` ve geçersiz kılar `Area`. `Circle` Örnek, <xref:System.Collections.Generic.SortedSet%601> `IComparer<Circle>` ( `Circle` VisualBasiciçinde)alanbirOluşturucukullanarak`IComparer(Of Circle)` bir nesne oluşturur. Ancak, bir `IComparer<Circle>`geçirmek yerine, örnek, uygulayan `IComparer<Shape>`bir `ShapeAreaComparer` nesnesi geçirir. Örnek, <xref:System.Collections.Generic.IComparer%601> genel arabirimin tür parametresi değişken karşıtı olduğundan, kod daha`Shape`türetilmiş bir türün (`Circle`) bir karşılaştırıcısı için çağrı yaparken daha az türetilmiş bir tür () karşılaştırıcısı geçirebilir.  
  
 `Circle` Öğesineyeni`IComparer<Shape>.Compare` bir nesne eklendiğinde`IComparer(Of Shape).Compare` , nesnesinin`ShapeAreaComparer` yöntemi (Visual Basic yöntemi), her yeni öğe varolan bir öğeyle karşılaştırıldığı zaman çağrılır. `SortedSet<Circle>` Metodun (`Shape`) parametre türü, geçirilmekte olan türden daha az türetilir (`Circle`), bu nedenle çağrı tür güvenlidir. Değişken Varyans, `ShapeAreaComparer` tek bir türün bir koleksiyonunu ve ' den `Shape`türetilen bir tür karma koleksiyonunu sıralamanıza olanak sağlar.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Değişken Türü Parametrelerle Genel Temsilciler  
 .NET Framework 4 `Func` ' te, gibi genel temsilcilerin <xref:System.Func%602>birlikte değişken dönüş türleri ve değişken karşıtı parametre türleri vardır. Gibi genel temsilcilerin <xref:System.Action%602>değişken karşıtı parametre türleri vardır. `Action` Bu, temsilcilerin daha fazla türetilmiş parametre türüne sahip değişkenlere atanabileceği ve ( `Func` Genel Temsilciler söz konusu olduğunda) daha az türetilmiş dönüş türlerinden atanabileceği anlamına gelir.  
  
> [!NOTE]
>  `Func` Genel temsilcilerin son genel tür parametresi, temsilci imzasında döndürülen değerin türünü belirtir. Değişkenle birlikte değişken (`out` anahtar sözcük) ve diğer genel tür parametreleri değişken karşıtı (`in` anahtar sözcük).  
  
 Aşağıdaki kod bunu göstermektedir. İlk kod parçası adlı `Base`bir sınıfı, devralan `Base`adlı `Derived` bir sınıfı ve adlı `MyMethod`bir `static` yöntemi (`Shared` Visual Basic) olan başka bir sınıfı tanımlar. Yöntemi bir örneğini `Base` alır ve bir `Derived`örneğini döndürür. (Bağımsız değişken öğesinin `Derived`bir örneği ise, `MyMethod` döndürür; bağımsız değişken öğesinin `Base`bir örneği ise, `MyMethod` yeni bir örneğini `Derived`döndürür.) ' `Main()`De, örnek, öğesini temsil `MyMethod`eden `Func<Base, Derived>` (`Func(Of Base, Derived)` Visual Basic olarak) bir örneğini oluşturur ve bunu değişkende `f1`depolar.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 İkinci kod parçası, temsilcinin tür `Func<Base, Base>` bir değişkene atanabildiğinden (`Func(Of Base, Base)` Visual Basic), dönüş türü birlikte değişken olduğundan gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Üçüncü kod parçası, temsilci türünde `Func<Derived, Derived>` bir değişkene atanabildiğinden (`Func(Of Derived, Derived)` Visual Basic), parametre türü değişken karşıtı olduğundan gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Son kod parçası, temsilcinin, değişken karşıtı parametre türünün ve covaryant dönüş türünün etkilerini birleştiren `Func<Derived, Base>` bir`Func(Of Derived, Base)` tür değişkenine (Visual Basic) atanabileceği gösterilmektedir.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Genel ve Genel Olmayan Temsilcilerde Değişken  
 Önceki kodda, imzası `MyMethod` oluşturulan genel temsilcinin imzasıyla tam olarak eşleşir: `Func<Base, Derived>` (`Func(Of Base, Derived)` Visual Basic). Örnek, tüm temsilci türleri genel temsilci türünden <xref:System.Func%602>oluşturulduğu sürece, bu genel temsilcinin daha fazla türetilmiş parametre türüne ve daha az türetilmiş dönüş türüne sahip değişkenlerde veya yöntem parametrelerinde depolanabileceğini gösterir.  
  
 Bu önemli bir noktadır. Genel temsilcilerin tür parametrelerindeki Kovaryans ve değişken varyans etkileri, sıradan temsilci bağlamasındaki Kovaryans ve değişken varyans efektlerine benzer (bkz. [TemsilcilerdeC#()](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve temsilcilerde varyans ( [ Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Ancak, temsilci bağlamadaki değişken, yalnızca değişken türde parametreleri olan genel temsilci türleriyle değil, tüm temsilci türleriyle birlikte çalışır. Ayrıca, temsilci bağlamada değişken, bir yöntemin daha kısıtlayıcı parametre türleri ve daha az kısıtlayıcı dönüş türü olan herhangi bir temsilciye bağlanmasına olanak tanırken, genel temsilcilerin atanması yalnızca her iki temsilci türünün de aynı genel tür tanımından oluşturulması durumunda çalışır.  
  
 Aşağıdaki örnekte, temsilci bağlamadaki değişkenin ve genel tür parametrelerindeki değişkenin birleşik etkisi gösterilmektedir. Örnek, en az türetilen`Type1`() ile en türetilmiş (`Type3`) arasında üç tür içeren bir tür hiyerarşisi tanımlar. Normal temsilci bağlamasındaki Varyans, parametre türü `Type1` ve dönüş türü olan bir yöntemi `Type3` bir parametre türü `Type2` ve dönüş türü `Type2`olan genel bir temsilciye bağlamak için kullanılır. Sonuçta elde edilen genel temsilci, genel tür parametrelerinin Kovaryans ve değişken varyans kullanılarak genel temsilci türü bir parametreye `Type3` ve dönüş `Type1`türüne sahip olan başka bir değişkene atanır. İkinci atama, aynı genel tür tanımından, bu durumda <xref:System.Func%602>, hem değişken türünün hem de temsilci türünün oluşturulmasını gerektirir.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Değişken Genel Arabirimleri ve Temsilcileri Tanımlama  
 .NET Framework 4 ' ten başlayarak, Visual Basic ve C# arabirimlerin ve temsilcilerin genel tür parametrelerini birlikte değişken veya değişken karşıtı olarak işaretlemenizi sağlayan anahtar sözcüklere sahip olursunuz.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, genel dil çalışma zamanı, genel tür parametrelerinde değişken açıklamalarını destekler. .NET Framework 4 ' ten önce, bu ek açıklamaları içeren genel bir sınıf tanımlamanın tek yolu, sınıfı [Ilasm. exe (Il Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) ile derleyerek veya dinamik bir derlemede yayarak Microsoft ara dili 'NI (MSIL) kullanmaktır.  
  
 Birlikte değişken `out` tür parametresi, [MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md)derleyicisi `+` için Visual Basic anahtar sözcüğüyle`Out` (anahtar sözcüğüyle) işaretlenir. Birlikte değişken türünde bir parametreyi, bir arabirime ait olan bir yöntemin dönüş değeri olarak veya bir temsilcinin dönüş türü olarak kullanabilirsiniz. Birlikte değişken türünde bir parametreyi, arabirim yöntemleri için genel türde bir kısıtlayıcı olarak kullanamazsınız.  
  
> [!NOTE]
>  Bir arabirimin bir yöntemi genel temsilci türünde bir parametreye sahipse, arabirim türünün birlikte değişken türünde bir parametresi, temsilci türünün değişken karşıtı türünde bir parametresini belirtmek için kullanılabilir.  
  
 Değişken karşıtı bir `in` tür parametresi, [MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md)derleyicisi `-` için Visual Basic anahtar`In` sözcüğüyle (anahtar sözcüğüyle) işaretlenir. Değişken karşıtı türde bir parametreyi, bir arabirime ait olan bir yöntemin bir parametresinin türü olarak veya bir temsilcinin bir parametresinin türü olarak kullanabilirsiniz. Değişken karşıtı türde bir parametreyi, bir arabirim yöntemi için genel türde bir kısıtlama olarak kullanabilirsiniz.  
  
 Yalnızca arabirim türlerinin ve temsilci türlerinin değişken türünde parametreleri olabilir. Bir arabirim veya temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
 Visual Basic ve C#, birlikte değişken veya değişken karşıtı türde parametrelerin kullanılmasına ilişkin kuralların ihlal edilmesine veya arabirimlerden ve temsilcilerden başka türde tür parametrelerine birlikte değişken veya değişken karşıtı ek açıklamalar eklenmesine izin vermez. [MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md) derleyicisi böyle denetimler gerçekleştirmez, ancak kuralları ihlal eden bir <xref:System.TypeLoadException> tür yüklemeye çalışırsanız bir oluşturulur.  
  
 Bilgi ve örnek kod için bkz. [Genel Arabirimlerde Varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Genel Arabirimlerde Varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
 [Başa dön](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Değişken Genel Arabirim ve Temsilci Türleri Listesi  
 .NET Framework 4 ' te, aşağıdaki arabirim ve temsilci türlerinde birlikte değişken ve/veya değişken karşıtı tür parametreleri vardır.  
  
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

- [Kovaryans ve değişken varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kovaryans ve değişken varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Temsilcilerde varyans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Temsilcilerde varyans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
