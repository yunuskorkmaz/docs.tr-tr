---
title: "Genel Türlerde Kovaryans ve Kontravaryans"
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
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2abd4c772c02c431ecb73139be7f620fe04d5d82
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="covariance-and-contravariance-in-generics"></a>Genel Türlerde Kovaryans ve Kontravaryans
<a name="top"></a>Kovaryans ve kontravaryans daha az kullanacak şekilde özelliği başvuran koşulları'nı (daha az belirli) türetilmiş veya daha fazla başlangıçta belirtilenden türü (daha fazla özel) türetilmiş markalarıdır. Genel tür parametreleri, genel türleri atamakta ve kullanmakta daha fazla esneklik sağlamak için birlikte değişme ve değişken karşıtlığını destekler. Bir tür sisteminden söz ederken, birlikte değişme, değişken karşıtlığı ve değişmezlik terimlerinin tanımları aşağıdaki gibidir. Adlı bir temel sınıf örnekleri varsayın `Base` ve adlı türetilmiş bir sınıf `Derived`.  
  
-   `Covariance`  
  
     İlk olarak belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.  
  
     Örneği atayabilirsiniz `IEnumerable<Derived>` (`IEnumerable(Of Derived)` Visual Basic'te) türünde bir değişken için `IEnumerable<Base>`.  
  
-   `Contravariance`  
  
     Orijinal olarak belirtilenden daha genel (daha az türetilmiş) bir tür belirtmenize olanak tanır.  
  
     Örneği atayabilirsiniz `IEnumerable<Base>` (`IEnumerable(Of Base)` Visual Basic'te) türünde bir değişken için `IEnumerable<Derived>`.  
  
-   `Invariance`  
  
     Yalnızca orijinal olarak belirtilen türü kullanabileceğiniz anlamına gelir; bu nedenle, değişmez bir genel tür parametresi birlikte değişken veya değişken karşıtı değildir.  
  
     Örneği atayamazsınız `IEnumerable<Base>` (`IEnumerable(Of Base)` Visual Basic'te) türünde bir değişken için `IEnumerable<Derived>` veya tam tersi.  
  
 Eşdeğişken tür parametreleri etkinleştirmek sıradan benzer Ara atamaları yapmanızı [çok biçimlilik](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md)aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601> Uygulayan sınıf <xref:System.Collections.Generic.IEnumerable%601> arabirim, bunu `List<Derived>` (`List(Of Derived)` Visual Basic'te) uygulayan `IEnumerable<Derived>`. Birlikte değişken tür parametresi geri kalanını yapar.  
  
 Diğer taraftan, birlikte değişkenlik mantığa aykırı görünüyor. Aşağıdaki örnek, bir temsilci türü oluşturur `Action<Base>` (`Action(Of Base)` Visual Basic'te) ve ardından bu temsilci türündeki bir değişkene atar `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Geri gibi görünüyor, ancak derleyen ve çalışan, tür açısından güvenli koddur. Lambda ifadesi türünde bir parametre alan bir yöntem tanımlar için atanan için temsilci eşleşen `Base` ve dönüş değeri yok. Sonuçta elde edilen temsilci türünde bir değişken atanabilir `Action<Derived>` çünkü tür parametresi `T` , <xref:System.Action%601> karşıtı temsilcisidir. Tür kullanımı uyumlu kod olduğundan `T` bir parametre türü belirtir. Zaman temsilci türü `Action<Base>` bir temsilci türü kabul edildiğinde çağrılan `Action<Derived>`, bağımsız değişken türü olmalıdır `Derived`. Yöntemin parametre türü olduğundan bu bağımsız değişken her zaman temel yönteme güvenle geçirilebilir `Base`.  
  
 Genel olarak, birlikte değişken türünde bir parametre bir temsilcinin dönüş türü olarak kullanılabilir ve değişken karşıtı türü parametreler parametre türleri olarak kullanılabilir. Bir arabirim için, birlikte değişken türü parametreler arabirimin yöntemlerinin dönüş türleri olarak kullanılabilir ve değişken karşıtı türü parametreler arabirimin yöntemlerinin parametre türleri olarak kullanılabilir.  
  
 Kovaryans ve kontravaryans topluca denir *farkı*. Eşdeğişken işaretlenmemiş genel tür parametresi veya karşıtı olarak adlandırılır *değişmez*. Genel dil çalışma zamanında değişken ile ilgili gerçeklerin kısa bir özeti:  
  
-   İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], değişken türü parametreleri genel arabirim ve genel temsilci türleri için kısıtlanmış.  
  
-   Bir genel arabirim veya genel temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
-   Değişken yalnızca başvuru türleri için geçerlidir; değişken türünde bir parametre için bir değer türü belirtirseniz, bu tür parametresi, sonuç olarak oluşturulan tür için değişmezdir.  
  
-   Değişken, temsilci birleşimi için geçerli değildir. Diğer bir deyişle, iki temsilciler türlerinin verilen `Action<Derived>` ve `Action<Base>` (`Action(Of Derived)` ve `Action(Of Base)` Visual Basic'te), sonuç türü güvenli olsa da ilk ikinci temsilci birleştiremez. Farkı verir türündeki bir değişkene atanacak ikinci temsilci `Action<Derived>`, ancak temsilcileri yalnızca kendi türlerinin tam olarak eşleşmesi durumunda birleştirebilirsiniz.  
  
 Aşağıdaki alt kısımlarda, değişkenle birlikte ve değişken karşıtı tür parametreleri ayrıntılı olarak açıklanmaktadır:  
  
-   [Eşdeğişken tür parametreleri ile genel arabirimler](#InterfaceCovariantTypeParameters)  
  
-   [Genel arabirimler karşıtı genel tür parametreleri ile](#InterfaceCovariantTypeParameters)  
  
-   [Genel temsilciler değişken ile tür parametreleri](#DelegateVariantTypeParameters)  
  
-   [Değişken genel arabirimler ve temsilciler tanımlama](#DefiningVariantTypeParameters)  
  
-   [Değişken genel arabirim ve temsilci türleri listesi](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Birlikte Değişen Tür Parametreleriyle Genel Arabirimler  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], birkaç genel arabirimler eşdeğişken türü parametrelerine sahip; örneğin: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, ve <xref:System.Linq.IGrouping%602>. Bu arabirimlerin tüm tür parametreleri birlikte değişen olduğundan, tür parametreleri yalnızca üyelerin dönüş türleri için kullanılır.  
  
 Aşağıdaki örnekte, birlikte değişen tür parametreleri gösterilmektedir. İki tür örnek tanımlar: `Base` sahip adlı bir statik yöntem `PrintBases` alan bir `IEnumerable<Base>` (`IEnumerable(Of Base)` Visual Basic'te) ve öğeleri yazdırır. `Derived`öğesinden devralınan `Base`. Boş bir örnek oluşturur `List<Derived>` (`List(Of Derived)` Visual Basic'te) ve bu tür için geçirilebileceği gösterilmektedir `PrintBases` ve türü değişkenine atanan `IEnumerable<Base>` atama olmadan. <xref:System.Collections.Generic.List%601>uygulayan <xref:System.Collections.Generic.IEnumerable%601>, tek bir eşdeğişken türü parametresine sahiptir. Eşdeğişken tür parametresi neden nedeni örneği `IEnumerable<Derived>` yerine kullanılan `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Değişken Karşıtı Genel Tür Parametrelerle Genel Arabirimler  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], birkaç genel arabirimler karşıtı türü parametrelerine sahip; örneğin: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, ve <xref:System.Collections.Generic.IEqualityComparer%601>. Bu arabirimlerin yalnızca değişken karşıtı türde parametreleri olduğundan, tür parametreleri yalnızca arabirimlerin üyelerinde parametre türleri olarak kullanılır.  
  
 Aşağıdaki örnekte, değişken karşıtı tür parametreleri gösterilmektedir. Örnek, bir Özet tanımlar (`MustInherit` Visual Basic'te) `Shape` ile sınıf bir `Area` özelliği. Örnek ayrıca tanımlar bir `ShapeAreaComparer` uygulayan sınıf `IComparer<Shape>` (`IComparer(Of Shape)` Visual Basic'te). Uygulaması <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> yöntemi değeri temel alarak `Area` özelliği, bu nedenle `ShapeAreaComparer` sıralamak için kullanılan `Shape` alana göre nesneleri.  
  
 `Circle` Sınıfının devraldığı `Shape` ve geçersiz kılmalar `Area`. Örnekte bir <xref:System.Collections.Generic.SortedSet%601> , `Circle` nesneleri, alan oluşturucu kullanılarak bir `IComparer<Circle>` (`IComparer(Of Circle)` Visual Basic'te). Ancak, geçirme yerine bir `IComparer<Circle>`, örnek geçirmeden bir `ShapeAreaComparer` uygulayan nesne `IComparer<Shape>`. Bu örnek daha az türetilmiş bir türün bir karşılaştırıcı geçirebilirsiniz (`Shape`) kodu daha türetilmiş bir tür bir karşılaştırıcı için çağırdığında (`Circle`), çünkü tür parametresi <xref:System.Collections.Generic.IComparer%601> genel arabirimidir karşıtı.  
  
 Yeni bir `Circle` nesne eklenmiş olup `SortedSet<Circle>`, `IComparer<Shape>.Compare` yöntemi (`IComparer(Of Shape).Compare` yöntemi Visual Basic'te), `ShapeAreaComparer` nesne varolan öğeyi yeni bir öğesi ile karşılaştırıldığında her zaman çağrılır. Yönteminin parametre türü (`Shape`) geçirilmiş türü daha az türetilmiş (`Circle`), çağrı güvenli türüdür. Değişken karşıtı etkinleştirir `ShapeAreaComparer` herhangi bir tek türde bir koleksiyonu yanı sıra, türetilen tür, karma koleksiyonu sıralamak için `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Değişken Türü Parametrelerle Genel Temsilciler  
 İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], `Func` gibi genel temsilciler <xref:System.Func%602>, eşdeğişken dönüş türleri ve karşıtı parametre türleri vardır. `Action` Gibi genel temsilciler <xref:System.Action%602>, karşıtı parametre türleri vardır. Bu temsilcileri daha fazla parametre türleri türetilmiş değişkenlere atanabilir anlamına gelir ve (durumunda `Func` genel temsilciler) daha az türetilmiş dönüş tür.  
  
> [!NOTE]
>  Son genel tür parametresi, `Func` genel temsilciler temsilci imzada dönüş değeri türünü belirtir. Eşdeğişken (`out` anahtar sözcüğü), diğer genel tür parametreleri karşıtı ise (`in` anahtar sözcüğü).  
  
 Aşağıdaki kod bunu göstermektedir. Adlı bir sınıf kod ilk parçasını tanımlayan `Base`, adlı bir sınıf `Derived` , devralınan `Base`ve başka bir sınıf ile bir `static` yöntemi (`Shared` Visual Basic'te) adlı `MyMethod`. Yöntem örneği alır `Base` ve örneğini döndürür `Derived`. (Bağımsız değişken bir örneği ise `Derived`, `MyMethod` bağımsız değişken bir örneği ise; döndürür `Base`, `MyMethod` yeni bir örneğini döndürür `Derived`.) İçinde `Main()`, örnek bir örneğini oluşturur `Func<Base, Derived>` (`Func(Of Base, Derived)` Visual Basic'te) temsil eden `MyMethod`ve değişkeninde depolar `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Kod ikinci parçasını türünde bir değişken için temsilci atanmış olduğunu gösterir `Func<Base, Base>` (`Func(Of Base, Base)` Visual Basic'te), dönüş türü birlikte değişkendir.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Kod üçüncü parçasını türünde bir değişken için temsilci atanmış olduğunu gösterir `Func<Derived, Derived>` (`Func(Of Derived, Derived)` Visual Basic'te), parametre türü karşıtıdır.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Kodu son parçası türünde bir değişken için temsilci atanmış olduğunu gösterir `Func<Derived, Base>` (`Func(Of Derived, Base)` Visual Basic'te), tür parametresi karşıtı etkilerini birleştirme ve eşdeğişken dönüş türü.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Genel ve Genel Olmayan Temsilcilerde Değişken  
 Önceki kodda, imzası `MyMethod` oluşturulan genel temsilcisi imzası tam olarak eşleşir: `Func<Base, Derived>` (`Func(Of Base, Derived)` Visual Basic'te). Tüm temsilci türleri genel temsilcisi türünden oluşturulan sürece bu genel temsilcisi değişkenleri veya daha fazla parametre türleri türetilmiş yöntem parametreleri depolanabilir ve daha az dönüş türleri türetilmiş örnek gösterir <xref:System.Func%602>.  
  
 Bu önemli bir noktadır. Kovaryans ve kontravaryans genel temsilciler tür parametrelerini etkilerini sıradan temsilci bağlama Kovaryans ve kontravaryans etkilerini benzerdir (bkz [Temsilcilerde varyans](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)). Ancak, temsilci bağlamadaki değişken, yalnızca değişken türde parametreleri olan genel temsilci türleriyle değil, tüm temsilci türleriyle birlikte çalışır. Ayrıca, temsilci bağlamada değişken, bir yöntemin daha kısıtlayıcı parametre türleri ve daha az kısıtlayıcı dönüş türü olan herhangi bir temsilciye bağlanmasına olanak tanırken, genel temsilcilerin atanması yalnızca her iki temsilci türünün de aynı genel tür tanımından oluşturulması durumunda çalışır.  
  
 Aşağıdaki örnekte, temsilci bağlamadaki değişkenin ve genel tür parametrelerindeki değişkenin birleşik etkisi gösterilmektedir. Örnek gelen en az üç tür içeren bir türü hiyerarşi tanımlar türetilmiş (`Type1`) en türetilen (`Type3`). Sıradan temsilci bağlama varyans parametre türüyle bir yöntem bağlamak için kullanılan `Type1` ve dönüş türü `Type3` parametre türüne sahip genel bir temsilci `Type2` ve dönüş türü `Type2`. Sonuçta elde edilen genel temsilcisi daha sonra genel temsilci türü türünde bir parametreye sahip başka bir değişkene atanır `Type3` ve dönüş türü `Type1`, Kovaryans ve kontravaryans genel tür parametreleri olarak kullanma. Değişken türü ve temsilci türü aynı genel tür tanımı, bu durumda, oluşturulması ikinci ataması gerektiriyorsa <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Başa dön](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Değişken Genel Arabirimleri ve Temsilcileri Tanımlama  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Visual Basic ve C# genel tür parametreleri arabirimlerinin işaretlemek etkinleştirmeniz ve olarak eşdeğişken temsilcilerin anahtar sözcükleri veya karşıtı sahip.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, genel dil çalışma zamanı, genel tür parametrelerinde değişken açıklamalarını destekler. Öncesinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], bu ek açıklamalar sahip genel bir sınıf tanımlamak için tek yolu, Microsoft Ara dili (MSIL) sınıfıyla derleme ya da kullanmaktır [Ilasm.exe (IL derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) veya bir dinamik yayma derleme.  
  
 Eşdeğişken tür parametresi ile işaretlenmiş `out` anahtar sözcüğü (`Out` Visual Basic anahtar sözcüğü `+` için [MSIL derleyici](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Birlikte değişken türünde bir parametreyi, bir arabirime ait olan bir yöntemin dönüş değeri olarak veya bir temsilcinin dönüş türü olarak kullanabilirsiniz. Birlikte değişken türünde bir parametreyi, arabirim yöntemleri için genel türde bir kısıtlayıcı olarak kullanamazsınız.  
  
> [!NOTE]
>  Bir arabirimin bir yöntemi genel temsilci türünde bir parametreye sahipse, arabirim türünün birlikte değişken türünde bir parametresi, temsilci türünün değişken karşıtı türünde bir parametresini belirtmek için kullanılabilir.  
  
 Karşıtı tür parametresi ile işaretlenmiş `in` anahtar sözcüğü (`In` Visual Basic anahtar sözcüğü `-` için [MSIL derleyici](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Değişken karşıtı türde bir parametreyi, bir arabirime ait olan bir yöntemin bir parametresinin türü olarak veya bir temsilcinin bir parametresinin türü olarak kullanabilirsiniz. Değişken karşıtı türde bir parametreyi, bir arabirim yöntemi için genel türde bir kısıtlama olarak kullanabilirsiniz.  
  
 Yalnızca arabirim türlerinin ve temsilci türlerinin değişken türünde parametreleri olabilir. Bir arabirim veya temsilci türünün hem birlikte değişen hem de değişken karşıtı parametreleri olabilir.  
  
 Visual Basic ve C#, birlikte değişken veya değişken karşıtı türde parametrelerin kullanılmasına ilişkin kuralların ihlal edilmesine veya arabirimlerden ve temsilcilerden başka türde tür parametrelerine birlikte değişken veya değişken karşıtı ek açıklamalar eklenmesine izin vermez. [MSIL derleyici](../../../docs/framework/tools/ilasm-exe-il-assembler.md) bu tür denetimler gerçekleştirmez, ancak bir <xref:System.TypeLoadException> kurallarını ihlal eden bir tür yüklemeye çalışırsanız atılır.  
  
 Bilgi ve örnek kod için bkz: [genel arabirimlerde varyans](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a).  
  
 [Başa dön](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Değişken Genel Arabirim ve Temsilci Türleri Listesi  
 İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], eşdeğişken sahip aşağıdaki arabirimi ve temsilci türleri ve/veya karşıtı parametreleri yazın.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kovaryans ve kontravaryans (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
 [Kovaryans ve kontravaryans (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)    
 [Temsilcilerde Varyans](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)
