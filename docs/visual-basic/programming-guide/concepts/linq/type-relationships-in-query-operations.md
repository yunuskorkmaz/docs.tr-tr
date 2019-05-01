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
ms.openlocfilehash: 14f17e89e2a4143580b4a2ca7f9d30013ded58f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053190"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)
Kullanılan değişkenleri [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu işlemleri kesin olarak belirlenmiştir ve birbiriyle uyumlu olması gerekir. Güçlü veri kaynağının, sorgu ve sorgu yürütme kullanılır. Aşağıdaki çizimde açıklamak için kullanılan terimler tanımlayan bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu. Bir sorgunun bölümlerini hakkında daha fazla bilgi için bkz: [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Sözde kod sorgu ile vurgulanmış öğelerin gösteren ekran görüntüsü.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 Sorgudaki Aralık değişkeninin türü, veri kaynağındaki öğelerin türü ile uyumlu olmalıdır. Sorgu değişkeninin türü tanımlanan dizisi öğe ile uyumlu olmalıdır `Select` yan tümcesi. Son olarak, dizisinin öğelerinin türü de kullanılan döngü denetim değişkeni türü ile uyumlu olmalıdır `For Each` Sorguyu yürüten deyimi. Bu güçlü yazım, Yazım hatalarının derleme zamanında kimliği kolaylaştırır.  
  
 Visual Basic yapar güçlü yazarak uygun olarak da bilinen bir yerel tür çıkarımı uygulayarak *örtülü yazma*. Özellik, önceki örnekte kullanılır ve genelinde kullanılan görürsünüz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnekler ve belgeler. Visual Basic'te yerel tür çıkarımı yalnızca'i kullanılarak başarılır bir `Dim` deyimi olmadan bir `As` yan tümcesi. Aşağıdaki örnekte, `city` bir dize olarak kesin.  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Yerel tür çıkarımı yalnızca çalışır `Option Infer` ayarlanır `On`. Daha fazla bilgi için [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, ancak aynı tür ilişkilerini veri kaynağındaki değişkenleri, sorgu değişkeni ve sorgu yürütme döngüsü arasında yok. Siz yazarken bu tür ilişkilerini temel bir anlayışa sahip olmak yararlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları veya kod örneklerinde belgeleri ve örnekleri ile çalışma.  
  
 Veri kaynağından döndürülen tür eşleşmeyen bir aralık değişkeni için açık bir tür belirtmeniz gerekebilir. Aralık değişkeninin türünü kullanarak belirtebileceğiniz bir `As` yan tümcesi. Ancak, bu hatayla sonuçlanır bir dönüştürme ise bir [daraltma dönüştürmesi](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve `Option Strict` ayarlanır `On`. Bu nedenle, veri kaynağından alınan değerleri dönüştürme almanızı öneririz. Kullanarak açık aralığı değişken türü için veri kaynağından değerleri dönüştürebilirsiniz <xref:System.Linq.Enumerable.Cast%2A> yöntemi. Seçilen değerleri de çevirebilirsiniz `Select` yan tümcesinin aralık değişkeni türünden farklı olan açık bir tür. Bu noktaları, aşağıdaki kodda gösterilmiştir.  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Tüm öğeleri kaynak verilerin döndüren sorgular  
 Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgulama işlemi, veri kaynağından seçilen öğelerin bir dizisini döndürür. Kaynak `names`, dizelerden oluşan bir dizi içeriyor ve sorgu çıktısı M harfi ile başlayan dizeleri içeren bir dizidir.  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 Bu, aşağıdaki koda eşdeğerdir, ancak çok daha kısa ve yazmak daha kolay. Yerel tür çıkarımı sorgularda güvenme Visual Basic'te tercih edilen stilidir.  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 Türleri açık veya örtük olarak belirlenmiş olup olmadığını aşağıdaki ilişkileri hem de önceki kod örnekleri, mevcut.  
  
1. Veri kaynağındaki öğelerin türü `names`, Aralık değişkeninin türü `name`, sorgu.  
  
2. Seçili olan nesnenin türü `name`, sorgu değişkeni türünü belirler `mNames`. Burada `name` sorgu değişkeni Visual Basic'de IEnumerable (Of String), bu nedenle, bir dize ise.  
  
3. Nde tanımlanan sorgu `mNames` yürütüldü `For Each` döngü. Döngü sorgu yürütmenin sonucu üzerinde yinelenir. Çünkü `mNames`, yürütüldüğünde, dizeler, döngü yineleme değişkeni, bir dizi döndürür `nm`, ayrıca bir dizedir.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Seçilen öğelerden bir alan döndüren sorgular  
 Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgulama veri kaynağından seçilen her öğe yalnızca bir bölümünü içeren bir dizi döndüren işlemi. Sorgu koleksiyonunu alır `Customer` nesneleri, veri kaynağı olarak ve yalnızca projeleri `Name` sonucun bir özellik. Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dize sırası üretir.  
  
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
  
1. Veri kaynağındaki öğelerin türü `customers`, Aralık değişkeninin türü `cust`, sorgu. Türü bu örnekte, `Customer`.  
  
2. `Select` Deyimi döndürür `Name` her özellik `Customer` nesnenin tamamı yerine nesne. Çünkü `Name` sorgu değişkeni bir dize ise `custNames`, yeniden IEnumerable (Of String), olmayacaktır `Customer`.  
  
3. Çünkü `custNames` dizeleri temsil `For Each` döngüsünün yineleme değişkeni `custName`, bir dize olmalıdır.  
  
 Önceki örnekte yerel tür çıkarımı, yazma ve anlama, aşağıdaki örnekte gösterildiği gibi daha kullanışsız olur.  
  
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
 Aşağıdaki örnek, daha karmaşık bir durum gösterir. Önceki örnekte, tüm değişkenlerin türleri açıkça belirtmek uygun. Bu örnekte, mümkün değildir. Tümünü seçmek yerine `Customer` öğeleri veri kaynağından veya tek bir alan her öğeden `Select` bu sorgu yan tümcesi, iki özellik özgün döndürür `Customer` nesne: `Name` ve `City`. Yanıt olarak `Select` yan tümcesi, derleyici, bu iki özellik içeren bir anonim tür tanımlar. Yürütmenin sonucu `nameCityQuery` içinde `For Each` döngü, yeni anonim türdeki örneklerin koleksiyonudur. Anonim tür kullanılabilir adı olduğundan, türünü belirtemezsiniz `nameCityQuery` veya `custInfo` açıkça. Diğer bir deyişle, anonim bir tür ile hiçbir tür adı yerine kullanılacak elinizde `String` içinde `IEnumerable(Of String)`. Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
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
  
 Önceki örnekte tüm değişkenlerin türleri belirlemek mümkün olmasa da, ilişkileri aynı kalır.  
  
1. Veri kaynağındaki öğelerin türü yeniden sorgudaki Aralık değişkeninin türüdür. Bu örnekte, `cust` örneğidir `Customer`.  
  
2. Çünkü `Select` deyimi, sorgu değişkeni anonim bir tür ürettiğinden `nameCityQuery`, anonim bir tür dolaylı olarak yazılmalıdır. Anonim bir tür kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.  
  
3. Yineleme değişkeni türünü `For Each` döngü 2. adımda oluşturduğunuz anonim türdür. Tür kullanılabilir adı olduğundan, döngü yineleme değişkeninin türü örtülü olarak belirlenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
