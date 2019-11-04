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
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418062"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>İzlenecek yol: C#'de Sorgu Yazma (LINQ)
Bu izlenecek yol, C# LINQ sorgu ifadeleri yazmak için kullanılan dil özelliklerini gösterir.  
  
## <a name="create-a-c-project"></a>Bir C# Projesi Oluşturma  
  
> [!NOTE]
> Aşağıdaki yönergeler Visual Studio içindir. Farklı bir geliştirme ortamı kullanıyorsanız, System. Core. dll başvurusu ve <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir `using` yönergesine sahip bir konsol projesi oluşturun.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Visual Studio 'da bir proje oluşturmak için  
  
1. Visual Studio 'Yu başlatın.  
  
2. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3. **Yüklü**' i genişletin, **Şablonlar**' ı genişletin, **C#görsel**' i genişletin ve **konsol uygulaması**' nı  
  
4. **Ad** metin kutusuna, farklı bir ad girin veya varsayılan adı kabul edin ve **Tamam** düğmesini seçin.  
  
     Yeni proje **Çözüm Gezgini**görüntülenir.  
  
5. Projenizin System. Core. dll dosyasına ve <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir `using` yönergesine başvurduğuna dikkat edin.  
  
## <a name="create-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı Oluşturma  
 Sorgular için veri kaynağı `Student` nesnelerinin basit bir listesidir. Her `Student` kaydı, sınıf içindeki test puanlarını temsil eden bir ad, soyadı ve bir tamsayılar dizisi içerir. Bu kodu projenize kopyalayın. Aşağıdaki özelliklere göz önünde edin:  
  
- `Student` sınıfı otomatik uygulanan özelliklerden oluşur.  
  
- Listedeki her öğrenci bir nesne başlatıcısı ile başlatılır.  
  
- Listenin kendisi bir koleksiyon başlatıcısı ile başlatılır.  
  
 Bu bütün veri yapısı, herhangi bir oluşturucuya veya açık üye erişimine açık çağrılar olmadan başlatılır ve oluşturulur. Bu yeni özellikler hakkında daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../classes-and-structs/auto-implemented-properties.md) ve [nesne ve koleksiyon başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağını eklemek için  
  
- `Student` sınıfını ve başlatılan öğrenciler listesini projenizdeki `Program` sınıfına ekleyin.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir Öğrenci eklemek için  
  
1. `Students` listesine yeni bir `Student` ekleyin ve tercih ettiğiniz bir ad ve test puanlarını kullanın. Nesne başlatıcısının sözdizimini daha iyi öğrenmek için tüm yeni öğrenci bilgilerini yazmayı deneyin.  
  
## <a name="create-the-query"></a>Sorgu Oluşturma  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
- Uygulamanın `Main` yönteminde, ilk testteki puanı 90 'den büyük olan tüm öğrencilerin bir listesini üretecek basit bir sorgu oluşturun. `Student` nesnesinin tamamı seçili olduğundan, sorgunun türü `IEnumerable<Student>`. Kod aynı zamanda [var](../../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak örtük yazma da kullanabilir, ancak sonuçları açıkça göstermek için açık yazma kullanılır. (`var`hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Ayrıca, sorgunun Aralık değişkeni `student`, kaynaktaki her bir `Student` başvuru işlevi görür ve her nesne için üye erişimi sağlar.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Sorguyu Yürütme  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1. Şimdi sorgunun yürütülmesine neden olacak `foreach` döngüsünü yazın. Kod hakkında aşağıdakilere göz önünde edin:  
  
    - Döndürülen dizideki her öğeye, `foreach` döngüsünde yineleme değişkeni üzerinden erişilir.  
  
    - Bu değişkenin türü `Student`ve sorgu değişkeninin türü uyumlu, `IEnumerable<Student>`.  
  
2. Bu kodu ekledikten sonra, sonuçları **konsol** penceresinde görmek için uygulamayı derleyin ve çalıştırın.  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Başka bir filtre koşulu eklemek için  
  
1. Bir sorguyu daha da belirginleştirmek için `where` yan tümcesinde birden çok Boolean koşulu birleştirebilirsiniz. Aşağıdaki kod, sorgunun ilk puanı 90 üzerinde olan ve son puanı 80 ' den az olan bu öğrencileri döndüren bir koşul ekler. `where` yan tümcesi aşağıdaki koda benzemelidir.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Sorguyu Değiştirme  
  
#### <a name="to-order-the-results"></a>Sonuçları sıralamak için  
  
1. Belirli bir sıra türünde olmaları durumunda sonuçların taranması daha kolay olacaktır. Döndürülen sırayı, kaynak öğelerde erişilebilir olan herhangi bir alana göre sıraya alabilirsiniz. Örneğin, aşağıdaki `orderby` yan tümcesi sonuçları alfabetik sırada her öğrencinin son adına göre bir ile Z 'ye sıralar. Sorgunuz için aşağıdaki `orderby` yan tümcesini, `where` deyiminize ve `select` deyimden önce ekleyin:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Şimdi `orderby` yan tümcesini, en yüksek puanın en düşük puanına kadar ilk testteki puana göre ters sırada sipariş verecek şekilde değiştirin.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Puanları görebilmeniz için `WriteLine` biçim dizesini değiştirin:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Sonuçları gruplandırmak için  
  
1. Gruplandırma, sorgu ifadelerinde güçlü bir özelliktir. Group yan tümcesi içeren bir sorgu bir grup sırası üretir ve her bir grubun kendisi bir `Key` ve bu grubun tüm üyelerinden oluşan bir dizi içerir. Aşağıdaki yeni sorgu, en son adının ilk harfini anahtar olarak kullanarak öğrencileri gruplandırır.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Sorgu türünün artık değiştiğini unutmayın. Artık anahtar olarak `char` türüne ve `Student` nesne dizisine sahip bir grup sırası oluşturur. Sorgunun türü değiştiği için aşağıdaki kod `foreach` yürütme döngüsünü de değiştirir:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Uygulamayı çalıştırın ve sonuçları **konsol** penceresinde görüntüleyin.  
  
     Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Değişkenlerin dolaylı olarak yazılmasını sağlamak için  
  
1. `IGroupings` `IEnumerables` açıkça kodlanması hızla sıkıcı hale gelebilir. `var`kullanarak aynı sorgu ve `foreach` döngüsünü çok daha kolay bir şekilde yazabilirsiniz. `var` anahtar sözcüğü, nesnelerinizin türlerini değiştirmez; yalnızca derleyiciye tür çıkarması talimatını verir. `studentQuery` türünü ve `group` yineleme değişkenini `var` olarak değiştirin ve sorguyu yeniden çalıştırın. Inner `foreach` döngüsünde, yineleme değişkeninin hala `Student`olarak yazıldığı ve sorgunun daha önce olduğu gibi çalıştığından emin olmanız gerektiğini unutmayın. `s` yineleme değişkenini `var` olarak değiştirip sorguyu yeniden çalıştırın. Tam olarak aynı sonuçları elde edersiniz.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     [Var](../../../language-reference/keywords/var.md)hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Grupları anahtar değerlerine göre sıralamak için  
  
1. Önceki sorguyu çalıştırdığınızda grupların alfabetik sırada olmadığına dikkat edin. Bunu değiştirmek için, `group` yan tümcesinden sonra bir `orderby` yan tümcesi sağlamanız gerekir. Ancak, bir `orderby` yan tümcesi kullanmak için, önce `group` yan tümcesi tarafından oluşturulan gruplara başvuru olarak hizmet veren bir tanımlayıcıya ihtiyacınız vardır. Tanımlayıcıyı, aşağıdaki gibi `into` anahtar sözcüğünü kullanarak sağlarsınız:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Bu sorguyu çalıştırdığınızda, grupların artık alfabetik sırada sıralanacağını görürsünüz.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Bir tanımlayıcıyı let kullanarak tanıtmak için  
  
1. Sorgu ifadesindeki herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak üzere `let` anahtar sözcüğünü kullanabilirsiniz. Bu tanımlayıcı, aşağıdaki örnekte olduğu gibi kolaylık olabilir veya bir ifadenin sonuçlarını birden çok kez hesaplanmak zorunda kalmayacak şekilde depolayarak performansı geliştirebilir.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Bir sorgu ifadesinde yöntem sözdizimini kullanmak için  
  
1. [Sorgu söz dizimi ve LINQ 'Teki yöntem sözdiziminde](./query-syntax-and-method-syntax-in-linq.md)açıklandığı gibi, bazı sorgu işlemleri yalnızca Yöntem sözdizimi kullanılarak ifade edilebilir. Aşağıdaki kod, kaynak dizideki her bir `Student` için toplam puanı hesaplar ve sonra sınıfın ortalama Puanını hesaplamak için bu sorgunun sonuçlarında `Average()` yöntemini çağırır.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Select yan tümcesinde dönüştürmek ya da planlamak için  
  
1. Bir sorgu için, öğeleri kaynak dizideki öğelerden farklı olan bir sıra üretmek çok yaygındır. Önceki sorgunuzu ve yürütme döngünüzü silin veya bir yorum yapın ve aşağıdaki kodla değiştirin. Sorgunun bir dizi dizeyi (`Students`değil) döndürdüğünü ve bu olguyu `foreach` döngüsünde yansıtıldığını unutmayın.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Bu kılavuzda daha önce bahsedilen kod, Ortalama sınıf puanının yaklaşık 334 olduğunu gösterdi. Toplam puanı, `Student ID`olan ve ortalamasının `Students` bir dizisini oluşturmak için `select` deyimindeki anonim bir tür kullanabilirsiniz:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 İçindeki C#sorgularla çalışmanın temel yönleri hakkında bilgi sahibi olduktan sonra, ilgilendiğiniz LINQ sağlayıcısı türü için belge ve örnekleri okumaya hazırsınızdır:  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ to Objects (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)
- [LINQ sorgu Ifadeleri](../../../linq/index.md)
