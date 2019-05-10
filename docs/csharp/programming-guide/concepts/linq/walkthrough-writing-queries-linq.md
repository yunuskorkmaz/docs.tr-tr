---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: 345acd17a6357f71f5c047475a4494a1fa793a58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595783"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>İzlenecek yol: C#'de Sorgu Yazma (LINQ)
Bu yönerge, LINQ Sorgu ifadeleri yazmak için kullanılan C# dili özellikleri gösterir.  
  
## <a name="create-a-c-project"></a>Bir C# Projesi Oluşturma  
  
> [!NOTE]
>  Visual Studio için aşağıdaki yönergeleri verilmiştir. Farklı bir geliştirme ortamı kullanıyorsanız, bir System.Core.dll başvurusu olan bir konsol projesi oluşturun ve bir `using` yönergesi <xref:System.Linq?displayProperty=nameWithType> ad alanı.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Visual Studio'da bir proje oluşturmak için  
  
1. Visual Studio’yu çalıştırın.  
  
2. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3. Genişletin **yüklü**, genişletme **şablonları**, genişletme **Visual C#** ve ardından **konsol uygulaması**.  
  
4. İçinde **adı** metin kutusunda, farklı bir ad girin veya varsayılan adı kabul edin ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
5. Projenize bir System.Core.dll başvurusu dikkat edin ve bir `using` yönergesi <xref:System.Linq?displayProperty=nameWithType> ad alanı.  
  
## <a name="create-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı Oluşturma  
 Veri kaynağını sorgular için basit bir listesidir `Student` nesneleri. Her `Student` kaydına sahip bir ad, Soyadı ve test puanlarını sınıfında temsil eden tamsayı dizisi. Bu kod projenize kopyalayın. Aşağıdaki özelliklere dikkat edin:  
  
- `Student` Sınıfı otomatik olarak uygulanan özellikler oluşur.  
  
- Listedeki her Öğrenci, bir nesne Başlatıcısı ile başlatılır.  
  
- Liste koleksiyon Başlatıcısı ile başlatılır.  
  
 Bu tüm veri yapısı başlatılamadı ve herhangi bir oluşturucu veya açık üye erişimi yapılan açık çağrıları olmadan örneği. Bu yeni özellikler hakkında daha fazla bilgi için bkz. [Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) ve [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağı eklemek için  
  
- Ekleme `Student` sınıfı ve öğrenciler için başlatılmış listesini `Program` projenizdeki sınıfı.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir Öğrenci eklemek için  
  
1. Yeni bir `Student` için `Students` listesi ve test puanlarının tercih ettiğiniz bir ad kullanın. Daha iyi nesne Başlatıcısı sözdizimi öğrenmek için tüm yeni Öğrenci bilgi yazmayı deneyin.  
  
## <a name="create-the-query"></a>Sorgu Oluşturma  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
- İçinde uygulamanın `Main` yöntemi yürütüldüğünde, tüm Öğrenciler ilk test üzerindeki, puanı 90'dan büyük bir listesini oluşturur ve basit bir sorgu oluşturun. Dikkat edin çünkü bütün `Student` nesne seçildiğinde, sorgu türü `IEnumerable<Student>`. Kod kullanarak dolaylı yazma da kullanabilirsiniz, ancak [var](../../../../csharp/language-reference/keywords/var.md) anahtar sözcüğü, açık yazım açıkça sonuçları göstermek için kullanılır. (Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Ayrıca sorgunun unutmayın aralık değişkeni `student`, her bir başvuru olarak hizmet veren `Student` kaynakta, her nesne için üye erişimi sağlama.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Sorguyu Yürütme  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1. Artık yazma `foreach` sorgu yürütmek neden olacak bir döngü. Kod hakkında aşağıdakileri unutmayın:  
  
    - Döndürülen dizinin her öğesinde, yineleme değişkeni aracılığıyla erişilir `foreach` döngü.  
  
    - Bu değişken türü `Student`, ve sorgu değişkeninin türü uyumlu `IEnumerable<Student>`.  
  
2. Bu kodu ekledikten sonra derleme ve sonuçlarını görmek için uygulamayı çalıştırma **konsol** penceresi.  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Başka bir filtre koşulu eklemek için  
  
1. Birden çok Boole koşulu birleştirebilirsiniz `where` sorgu iyice daraltmak için yan tümcesi. Aşağıdaki kod, böylece sorgu bu Öğrenciler, ilk puanı döndürür. bir koşul üzerinde 90 ve son, puan 80 şeklindeydi ekler. `where` Yan tümcesi, aşağıdaki kod benzemesi gerekir.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Daha fazla bilgi için [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Sorguyu Değiştirme  
  
#### <a name="to-order-the-results"></a>Sonuçları sıralamak için  
  
1. Sipariş çeşit olmaları durumunda tarama sonuçlarını daha kolay olacaktır. Döndürülen dizi kaynak öğeleri erişilebilen herhangi bir alana göre sıralayabilirsiniz. Örneğin, aşağıdaki `orderby` yan tümcesi siparişleri sonuçları alfabetik sırada A'dan Z'ye son her öğrencinin adına göre. Aşağıdaki `orderby` sorgunuzu, sonra sağ yan tümcesini `where` deyimi ve önce `select` deyimi:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Şimdi değiştir `orderby` BT'nin sonuçlarını ters sırada puanına göre ilk testten en yüksek puanı düşük puana göre sıralar için yan tümcesi.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Değişiklik `WriteLine` puanları görebilmeniz için biçimlendirme dizesi:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Daha fazla bilgi için [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Sonuçları gruplandırmak için  
  
1. Gruplandırma sorgu ifadeleri güçlü bir özelliktir. Group yan tümcesi içeren sorgu grupları bir dizi oluşturur ve her grubu içeren bir `Key` ve bu grubun tüm üyelerinin oluşan bir dizi. Aşağıdaki yeni sorgu anahtarı olarak son adlarının ilk harflerini kullanarak Öğrenciler gruplandırır.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Sorgu türü artık değiştirildiğine dikkat edin. Artık bir dizi olan grupları üretir bir `char` bir anahtarı ve bir dizi türü `Student` nesneleri. Sorgu türü değiştiğinden, aşağıdaki değişiklikleri kod `foreach` yürütme döngüsü ayrıca:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Uygulamayı çalıştırmak ve sonuçları görüntülemek **konsol** penceresi.  
  
     Daha fazla bilgi için [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Değişkenlerin dolaylı olarak yazılmasını sağlamak için  
  
1. Açıkça kodlama `IEnumerables` , `IGroupings` hızla zahmetli hale gelebilir. Aynı sorgu yazabilirsiniz ve `foreach` daha rahat kullanarak döngü `var`. `var` Anahtar sözcüğü, nesne türlerini değiştirmez; yalnızca derleyicinin türlerini çıkarması bildirir. Türünü değiştirme `studentQuery` ve yineleme değişkeni `group` için `var` ve sorguyu yeniden çalıştırın. İçinde iç unutmayın `foreach` döngüsünün yineleme değişkeni hala türü olarak `Student`, ve sorgu yalnızca gibi çalışır. Değişiklik `s` yineleme değişkeni `var` ve sorguyu yeniden çalıştırın. Tam olarak aynı sonuçları elde ettiğimizi görürsünüz.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Hakkında daha fazla bilgi için [var](../../../../csharp/language-reference/keywords/var.md), bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Grupları anahtar değerlerine göre sıralamak için  
  
1. Önceki sorguya çalıştırdığınızda, grupları alfabetik sırada olmadığına dikkat edin. Bunu değiştirmek için sağlamalısınız bir `orderby` yan tümcesinden sonra `group` yan tümcesi. Ancak kullanmak için bir `orderby` yan tümcesi, ilk gerekir tarafından oluşturulan grupları başvuru olarak hizmet veren bir tanımlayıcı `group` yan tümcesi. Tanımlayıcısını kullanarak sağlama `into` anahtar sözcüğü, aşağıdaki gibi:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Bu sorgu çalıştırdığınızda, grupları, artık alfabetik olarak sıralanır görürsünüz.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Bir tanımlayıcıyı let kullanarak tanıtmak için  
  
1. Kullanabileceğiniz `let` sorgu ifadesinde herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak için anahtar sözcüğü. Bu tanımlayıcı aşağıdaki örnekte olduğu gibi bir kullanışlı olabilir veya birden çok kez hesaplanacak yok, bir ifadenin sonuçlarını depolayarak performansı geliştirebilirsiniz.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Daha fazla bilgi için [let yan tümcesi](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Bir sorgu ifadesinde yöntem sözdizimini kullanmak için  
  
1. Bölümünde anlatıldığı gibi [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), bazı sorgu işlemlerinin yalnızca yöntemi söz dizimi kullanılarak belirtilebilir. Toplam puanı her biri için aşağıdaki kodu hesaplar `Student` kaynak dizisi, ve ardından aramaları `Average()` sınıfının ortalama puanını hesaplamak için bu sorgunun sonuçlarının yöntemi.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Select yan tümcesinde dönüştürmek ya da planlamak için  
  
1. Öğeleri kaynak dizileri öğeleri farklı bir dizi oluşturmak için bir sorgu çok yaygındır. Silin veya önceki sorgu ve yürütme döngüsü açıklama ve aşağıdaki kodla değiştirin. Sorgu dizeleri bir dizi döndürmediğine dikkat edin (değil `Students`), ve bu olgu yansıtılır `foreach` döngü.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Bu kılavuzda daha önce açıklanan kod ortalama sınıfı puanı yaklaşık 334 belirtilir. Bir dizi oluşturmak için `Students` birlikte sınıfı ortalama'den büyük olan toplam puanı, `Student ID`, anonim bir tür içinde kullanabileceğiniz `select` deyimi:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sorgular, C# ile çalışmanın temel özellikleri hakkında bilgi sahibi olduktan sonra belgelere ve örneklere LINQ sağlayıcısı, ilgilendiğiniz belirli türünün okumaya hazırsınız:  
  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
- [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)
