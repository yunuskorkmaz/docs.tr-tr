---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: f2135c6c3649ba2fc87e3b49770439688a58269b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73418062"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>İzlenecek yol: C#'de Sorgu Yazma (LINQ)
Bu gözden geçirme, LINQ sorgu ifadeleri yazmak için kullanılan C# dil özelliklerini gösterir.  
  
## <a name="create-a-c-project"></a>Bir C# Projesi Oluşturma  
  
> [!NOTE]
> Aşağıdaki talimatlar Visual Studio içindir. Farklı bir geliştirme ortamı kullanıyorsanız, System.Core.dll'ye başvuru içeren `using` bir konsol <xref:System.Linq?displayProperty=nameWithType> projesi ve ad alanı için bir yönerge oluşturun.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Visual Studio'da proje oluşturmak için  
  
1. Visual Studio’yu çalıştırın.  
  
2. Menü çubuğunda **Dosya**, **Yeni**, **Proje'yi**seçin.  
  
     **Yeni Proje** iletişim kutusu açılır.  
  
3. **Yüklü**genişletin, **Şablonları**genişletin, **Visual C#** seçeneğini genişletin ve ardından **Konsol Uygulamasını**seçin.  
  
4. **Ad** metin kutusuna farklı bir ad girin veya varsayılan adı kabul edin ve ardından **Tamam** düğmesini seçin.  
  
     Yeni proje Çözüm **Gezgini'nde**görünür.  
  
5. Projenizin System.Core.dll'ye bir başvurusu `using` ve <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir yönergesi olduğuna dikkat edin.  
  
## <a name="create-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı Oluşturma  
 Sorgular için veri kaynağı `Student` nesnelerin basit bir listesidir. Her `Student` kaydın bir adı, soyadı ve sınıftaki test puanlarını temsil eden bir tamsayı dizisi vardır. Bu kodu projenize kopyalayın. Aşağıdaki özelliklere dikkat edin:  
  
- Sınıf `Student` otomatik olarak uygulanan özelliklerden oluşur.  
  
- Listedeki her öğrenci bir nesne baş harfer ile başharfe işlenir.  
  
- Listenin kendisi bir koleksiyon baş harfer ile başharfe getirilir.  
  
 Tüm bu veri yapısı, herhangi bir oluşturucu ya da açık üye erişimine açık çağrılar yapılmadan başharflere alınacak ve anında elde edilecektir. Bu yeni özellikler hakkında daha fazla bilgi için Otomatik [Uygulanan Özellikler](../../classes-and-structs/auto-implemented-properties.md) ve Nesne ve Koleksiyon [Başlangıç Layıcıları'na](../../classes-and-structs/object-and-collection-initializers.md)bakın.  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağını eklemek için  
  
- Projenizdeki `Student` sınıf ve öğrencilerin başlangıç listesini `Program` sınıfa ekleyin.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir Öğrenci eklemek için  
  
1. `Students` Listeye yeni `Student` bir yeni ekleyin ve seçtiğiniz bir ad ve test puanları kullanın. Nesne başharfini daha iyi öğrenmek için tüm yeni öğrenci bilgilerini yazmayı deneyin.  
  
## <a name="create-the-query"></a>Sorgu Oluşturma  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
- Uygulamanın `Main` yönteminde, yürütüldüğünde ilk testteki puanı 90'dan büyük olan tüm öğrencilerin listesini oluşturacak basit bir sorgu oluşturun. Tüm `Student` nesne seçildiğinden, sorgunun türü `IEnumerable<Student>`. Kod, [var](../../../language-reference/keywords/var.md) anahtar sözcüğü kullanılarak örtük yazıyazmakda da kullanılabilse de, sonuçları açıkça göstermek için açık yazı yazmak kullanılır. (Hakkında `var`daha fazla bilgi için bkz: [Örtülü Olarak Yazılan Yerel Değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Ayrıca, sorgunun aralık değişkeni, `student`kaynaktaki her `Student` biri için bir başvuru görevi görehizmet ederek her nesne için üye erişimi sağladığını da unutmayın.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Sorguyu Yürütme  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1. Şimdi sorguyürütmek için neden olacak `foreach` döngü yazın. Kod hakkında aşağıdakileri not edin:  
  
    - Döndürülen dizideki her elemana `foreach` döngüdeki yineleme değişkeninden erişilir.  
  
    - Bu değişkenin türü `Student`ve sorgu değişkeninin türü `IEnumerable<Student>`uyumludur.  
  
2. Bu kodu ekledikten sonra, **konsol** penceresinde sonuçları görmek için uygulamayı oluşturun ve çalıştırın.  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Başka bir filtre koşulu eklemek için  
  
1. Bir sorguyu `where` daha da hassaslaştırmak için yan tümcedeki birden çok Boolean koşullarını birleştirebilirsiniz. Aşağıdaki kod, ilk puanı 90'ın üzerinde olan ve son puanı 80'den az olan öğrencileri döndüren bir koşul ekler. Yan `where` tümce aşağıdaki koda benzemelidir.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Daha fazla bilgi için [bkz.](../../../language-reference/keywords/where-clause.md)  
  
## <a name="modify-the-query"></a>Sorguyu Değiştirme  
  
#### <a name="to-order-the-results"></a>Sonuçları sıralamak için  
  
1. Bir tür sıradaysa, sonuçları taramayapmak daha kolay olacaktır. Döndürülen sırayı kaynak öğelerdeki erişilebilir herhangi bir alana göre sipariş edebilirsiniz. Örneğin, aşağıdaki `orderby` yan tümce, sonuçları her öğrencinin soyadına göre A'dan Z'ye alfabetik sırayla sıralar. İfadeden `orderby` hemen sonra ve deyimden `select` önce, sorgunuza aşağıdaki yan tümceyi ekleyin: `where`  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. `orderby` Şimdi, sonuçları ilk testteki puana göre, en yüksek puandan en düşük puana göre ters sırayla sipariş edebilmesi için tümceyi değiştirin.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Puanları `WriteLine` görebilmeniz için biçim dizesini değiştirin:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Daha fazla bilgi için [orderby yan tümcesi'ne](../../../language-reference/keywords/orderby-clause.md)bakın.  
  
#### <a name="to-group-the-results"></a>Sonuçları gruplandırmak için  
  
1. Gruplandırma sorgu ifadelerinde güçlü bir yetenektir. Grup yan tümcesi olan bir sorgu bir grup `Key` dizisi üretir ve her grubun kendisi, o grubun tüm üyelerinden oluşan bir dizi içerir. Aşağıdaki yeni sorgu, anahtar olarak soyadlarının ilk harfini kullanarak öğrencileri gruplandırmaktır.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Sorgunun türünün artık değiştiğini unutmayın. Şimdi bir anahtar olarak türü `char` ve `Student` nesnelerin bir dizi grup bir dizi üretir. Sorgunun türü değiştiğinden, aşağıdaki kod yürütme `foreach` döngüsünde de değişiklik gösterir:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Uygulamayı çalıştırın ve sonuçları **Konsol** penceresinde görüntüleyin.  
  
     Daha fazla bilgi için [grup yan tümcesi'ne](../../../language-reference/keywords/group-clause.md)bakın.  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Değişkenlerin dolaylı olarak yazılmasını sağlamak için  
  
1. Açıkça kodlama `IEnumerables` `IGroupings` hızla sıkıcı olabilir. Aynı sorguyu yazabilir `foreach` ve döngüyü çok `var`daha rahat bir şekilde kullanarak. Anahtar `var` kelime nesnelerinizin türlerini değiştirmez; sadece derleyici türleri çıkarmak için talimat verir. Tür ve `studentQuery` yineleme değişkenini `group` değiştirin `var` ve sorguyu yeniden çalıştırın. İç `foreach` döngüde yineleme değişkeninin hala "olarak" `Student`olarak yazılması gerektiğini ve sorgunun eskisi gibi çalıştığını unutmayın. Yineleme `s` değişkenini değiştirin `var` ve sorguyu yeniden çalıştırın. Aynı sonuçları aldığınızı görüyorsunuz.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     [Var](../../../language-reference/keywords/var.md)hakkında daha fazla bilgi için [bkz.](../../classes-and-structs/implicitly-typed-local-variables.md)  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Grupları anahtar değerlerine göre sıralamak için  
  
1. Önceki sorguyu çalıştırdığınızda, grupların alfabetik sırada olmadığını fark esiniz. Bunu değiştirmek için, yan `orderby` tümceden `group` sonra bir yan tümce sağlamanız gerekir. Ancak bir `orderby` yan tümce kullanmak için öncelikle yan tümcetarafından oluşturulan gruplara `group` başvuru görevi görebilen bir tanımlayıcıgerekir. Anahtar kelimeyi kullanarak tanımlayıcıyı `into` aşağıdaki gibi sağlarsınız:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Bu sorguyu çalıştırdığınızda, grupların artık alfabetik sıraya göre sıralanmış olduğunu görürsünüz.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Bir tanımlayıcıyı let kullanarak tanıtmak için  
  
1. `let` Sorgu ifadesinde herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak için anahtar kelimekullanabilirsiniz. Bu tanımlayıcı, aşağıdaki örnekte olduğu gibi kolaylık sağlayabilir veya bir ifadenin sonuçlarını birden çok kez hesaplanması gerekmeyecek şekilde depolayarak performansı artırabilir.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Daha fazla bilgi için [bkz.](../../../language-reference/keywords/let-clause.md)  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Bir sorgu ifadesinde yöntem sözdizimini kullanmak için  
  
1. [Linq'te Sorgu Sözdizimi ve Yöntem Sözdizimi'nde](./query-syntax-and-method-syntax-in-linq.md)açıklandığı gibi, bazı sorgu işlemleri yalnızca yöntem sözdizimi kullanılarak ifade edilebilir. Aşağıdaki kod kaynak sıradaki her `Student` biri için toplam puanı `Average()` hesaplar ve sonra sınıfın ortalama puanını hesaplamak için bu sorgunun sonuçlarında yöntemi çağırır.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Select yan tümcesinde dönüştürmek ya da planlamak için  
  
1. Bir sorgunun, öğeleri kaynak dizideki öğelerden farklı olan bir dizi oluşturması çok yaygındır. Önceki sorgu ve yürütme döngünüzün silin veya yorumunuzu yapın ve aşağıdaki kodla değiştirin. Sorgunun bir dize sırasını döndürtettiğini (değil) `Students`ve `foreach` bu gerçeğin döngüye yansıttığını unutmayın.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Bu gözden geçirmede daha önceki kod, ortalama sınıf puanının yaklaşık 334 olduğunu belirtmiştir. Toplam puanı sınıf `Students` ortalamasından büyük olan bir dizi oluşturmak `Student ID`için, onların , `select` deyiminde anonim bir tür kullanabilirsiniz:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 C#'daki sorgularla çalışmanın temel yönlerini tanıdıktan sonra, ilgilendiğiniz belirli türde LINQ sağlayıcısına ait belgeleri ve örnekleri okumaya hazırsınız:  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LinQ xml (C#) için](./linq-to-xml-overview.md)  
  
 [Nesnelere LINQ (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil-Tümleşik Sorgu (LINQ) (C#)](./index.md)
- [LINQ Sorgu İfadeleri](../../../linq/index.md)
