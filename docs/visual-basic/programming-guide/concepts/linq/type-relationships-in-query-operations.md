---
title: LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: ed0072eeb44a17201ddab2af6f6a44fd14461029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655348"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)
Kullanılan değişkenleri [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu işlemleri kesin türü belirtilmiş ve birbiriyle uyumlu olması gerekir. Güçlü yazarak, veri kaynağı, sorgu ve sorgu yürütmesi kullanılır. Aşağıdaki çizimde açıklamak için kullanılan terimler tanımlayan bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu. Bir sorgunun bölümlerini hakkında daha fazla bilgi için bkz: [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Öğeleri vurgulanmış sahte kod sorgu. ] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
LINQ Sorgu bölümleri  
  
 Sorgudaki Aralık değişkeninin türü veri kaynağındaki öğelerin türü ile uyumlu olmalıdır. Sorgu değişkeninin türü tanımlanan dizisi öğesi ile uyumlu olmalıdır `Select` yan tümcesi. Son olarak, sıra öğelerin türü ayrıca kullanılan for döngüsü denetim değişkeni türü ile uyumlu olmalıdır `For Each` Sorguyu yürüten deyimi. Bu güçlü yazarak türü hataları tanımlaması derleme zamanında kolaylaştırır.  
  
 Visual Basic hale getirir yazmaya güçlü uygun yerel türü çıkarımı olarak da bilinen uygulayarak *örtülü yazma*. Özellik, önceki örnekte kullanılır ve bunu genelinde kullanılan görür [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnekler ve belgeler. Visual Basic'te yerel türü çıkarımı yalnızca kullanılarak gerçekleştirilen bir `Dim` deyimi olmadan bir `As` yan tümcesi. Aşağıdaki örnekte, `city` bir dize olarak kesin türü belirtilmiş.  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  Yerel türü çıkarımı çalışır yalnızca `Option Infer` ayarlanır `On`. Daha fazla bilgi için bkz: [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Ancak, bir sorguda yerel türü çıkarımı kullansanız bile aynı tür ilişkileri veri kaynağındaki değişkenleri sorgu değişkeni ve sorgu yürütme döngüsü arasında mevcut. Yazarken bu tür ilişkileri ilgili temel bilgilere sahip yararlıdır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular veya belgelerinde örnekleri ve kodu ile çalışma.  
  
 Veri kaynağından döndürülen türü eşleşmiyor bir aralık değişkeni için bir açık tür belirtmeniz gerekebilir. Aralık değişkeninin türünü kullanarak belirtebilirsiniz bir `As` yan tümcesi. Ancak, bu hatayla sonuçlanır dönüştürme ise bir [dönüştürme daraltma](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve `Option Strict` ayarlanır `On`. Bu nedenle, veri kaynağından alınan değerleri dönüştürme gerçekleştirmenizi öneririz. Kullanarak açık aralık değişkeni türü veri kaynağından değerleri dönüştürebilirsiniz <xref:System.Linq.Enumerable.Cast%2A> yöntemi. Seçilen değerleri de çevirebilirsiniz `Select` yan tümcesinin aralık değişkeni türünden farklı bir açık tür. Bu noktalar aşağıdaki kodda gösterilmiştir.  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Kaynak verilerin tüm öğeleri döndüren sorgular  
 Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işleminin veri kaynağından seçilen öğeleri bir dizi döndürür. Kaynak `names`, bir dizisini içerir ve sorgu çıktısı M harfle başlayan dizelerini içeren bir dizidir.  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 Bu, aşağıdaki kodu eşdeğerdir, ancak daha kısa ve yazma daha kolay. Yerel türü çıkarımı sorgularda bağımlılık Visual Basic'te tercih edilen stili ' dir.  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 Türü örtük veya açık olarak belirlenir olup olmadığını aşağıdaki ilişkileri önceki kod örnekleri, ikisi de yok.  
  
1.  Veri kaynağındaki öğelerin türü `names`, Aralık değişkeninin tür `name`, sorgu.  
  
2.  Seçili nesne türünü `name`, sorgu değişken türünü belirler `mNames`. Burada `name` sorgu değişkeni Visual Basic'de IEnumerable (Of dize) olacak şekilde bir dize değil.  
  
3.  Tanımlanan sorgu `mNames` yürütülür `For Each` döngü. Döngü sorgu yürütmenin sonucu yineler. Çünkü `mNames`, yürütüldüğünde, bir dizi dize, döngü yineleme değişkeni döndürür `nm`, ayrıca bir dizedir.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Seçilen öğeleri bir alan döndüren sorgular  
 Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu işleminin veri kaynağından seçilen her öğe yalnızca bir bölümünü içeren bir dizi döndürür. Sorgu bir koleksiyonunu alır `Customer` nesneleri, veri kaynağı olarak ve yalnızca projeleri `Name` sonucun bir özellik. Müşteri adı bir dize olduğundan, sorgu dizeleri dizisi çıktı olarak üretir.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 Bu basit örnekte değişkenleri arasındaki ilişkileri gibidir.  
  
1.  Veri kaynağındaki öğelerin türü `customers`, Aralık değişkeninin tür `cust`, sorgu. Türü bu örnekte, `Customer`.  
  
2.  `Select` Deyiminin döndüreceği `Name` her özellik `Customer` nesnenin tamamı yerine nesne. Çünkü `Name` sorgu değişken bir dize `custNames`, yeniden (dize), IEnumerable, olmaz `Customer`.  
  
3.  Çünkü `custNames` dizeler, bir dizi temsil eden `For Each` döngünün yineleme değişkeni `custName`, bir dize olmalıdır.  
  
 Yerel türü çıkarımı önceki örnek yazmak için ve anlaşılması aşağıdaki örnekte gösterildiği gibi daha kullanışsız olabilir.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>Anonim türler gerektiren sorguları  
 Aşağıdaki örnek, daha karmaşık bir durumu gösterir. Önceki örnekte, tüm değişkenleri türlerinde açıkça belirtmek kullanışsız. Bu örnekte, mümkün değildir. Tüm seçmek yerine `Customer` veri kaynağı veya tek bir alan her öğeden öğelerinden `Select` bu sorgu yan tümcesinde iki özgün özelliklerini döndürür `Customer` nesne: `Name` ve `City`. Yanıt olarak `Select` yan tümcesi, derleyici, bu iki özellik içeren bir anonim türü tanımlar. Yürütmenin sonucu `nameCityQuery` içinde `For Each` döngü yeni anonim türdeki örneklerin koleksiyonudur. Anonim tür kullanılabilir ad olduğundan türünü belirtemezsiniz `nameCityQuery` veya `custInfo` açıkça. Diğer bir deyişle, sahip anonim bir tür, hiçbir tür adı yerine kullanılacak elinizde `String` içinde `IEnumerable(Of String)`. Daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 Önceki örnekte tüm değişkenleri türlerinde belirlemek mümkün olmasa da ilişkileri aynı kalır.  
  
1.  Veri kaynağındaki öğelerin türü yeniden sorgusunda aralık değişkeni türüdür. Bu örnekte, `cust` örneği `Customer`.  
  
2.  Çünkü `Select` bildirimi üreten anonim bir tür, sorgu değişkeni `nameCityQuery`, anonim bir tür olarak örtülü olarak yazılan gerekir. Anonim bir tür kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.  
  
3.  Yineleme değişkeni türü `For Each` döngü 2. adımda oluşturduğunuz anonim türüdür. Kullanılabilir ad türüne sahip olduğundan, döngü yineleme değişkeni türü örtük olarak belirlenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'te Lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Sorgular](../../../../visual-basic/language-reference/queries/queries.md)
