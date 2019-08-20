---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: 9fa15f1506d2fb22ef6c693508a2cd045f920add
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590898"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>İzlenecek yol: C#'de Sorgu Yazma (LINQ)
Bu izlenecek yol, C# LINQ sorgu ifadeleri yazmak için kullanılan dil özelliklerini gösterir.  
  
## <a name="create-a-c-project"></a>Bir C# Projesi Oluşturma  
  
> [!NOTE]
>  Aşağıdaki yönergeler Visual Studio içindir. Farklı bir geliştirme ortamı kullanıyorsanız, System. Core. dll başvurusu ve `using` <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir yönerge içeren bir konsol projesi oluşturun.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Visual Studio 'da bir proje oluşturmak için  
  
1. Visual Studio’yu çalıştırın.  
  
2. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3. **Yüklü**' i genişletin, **Şablonlar**' ı genişletin, **C#görsel**' i genişletin ve **konsol uygulaması**' nı  
  
4. **Ad** metin kutusuna, farklı bir ad girin veya varsayılan adı kabul edin ve **Tamam** düğmesini seçin.  
  
     Yeni proje **Çözüm Gezgini**görüntülenir.  
  
5. Projenizin System. Core. dll dosyasına ve `using` <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir yönergeye sahip olduğuna dikkat edin.  
  
## <a name="create-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı Oluşturma  
 Sorgular için veri kaynağı basit bir `Student` nesne listesidir. Her `Student` kaydın adı, soyadı ve, sınıftaki test puanlarını temsil eden bir tamsayılar dizisi vardır. Bu kod projenize kopyalayın. Aşağıdaki özelliklere göz önünde edin:  
  
- `Student` Sınıfı otomatik uygulanan özelliklerden oluşur.  
  
- Listedeki her öğrenci bir nesne başlatıcısı ile başlatılır.  
  
- Listenin kendisi bir koleksiyon başlatıcısı ile başlatılır.  
  
 Bu bütün veri yapısı, herhangi bir oluşturucuya veya açık üye erişimine açık çağrılar olmadan başlatılır ve oluşturulur. Bu yeni özellikler hakkında daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../classes-and-structs/auto-implemented-properties.md) ve [nesne ve koleksiyon başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağını eklemek için  
  
- `Program` Kuruluşunuzdaki sınıfa `Student` sınıfını ve başlatılan öğrenci listesini ekleyin.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir Öğrenci eklemek için  
  
1. Listeye`Students` yeni `Student` bir ad ekleyin ve seçtiğiniz bir adı ve test puanlarını kullanın. Nesne başlatıcısının sözdizimini daha iyi öğrenmek için tüm yeni öğrenci bilgilerini yazmayı deneyin.  
  
## <a name="create-the-query"></a>Sorgu Oluşturma  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
- Uygulamanın `Main` yönteminde, yürütüldüğü bir basit sorgu oluşturun, bu, ilk testteki puanı 90 ' den büyük olan tüm öğrencilerin bir listesini oluşturur. Tüm `Student` nesnenin seçildiği, sorgunun türünün olduğunu `IEnumerable<Student>`unutmayın. Kod aynı zamanda [var](../../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak örtük yazma da kullanabilir, ancak sonuçları açıkça göstermek için açık yazma kullanılır. (Hakkında `var`daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Ayrıca sorgunun Aralık değişkeni `student`, her bir nesne için üye erişimi sağlayan, kaynakta her birine `Student` bir başvuru olarak işlev görür.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Sorguyu Yürütme  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1. Şimdi sorgunun yürütülmesine `foreach` neden olacak döngüyü yazın. Kod hakkında aşağıdakilere göz önünde edin:  
  
    - Döndürülen dizideki her öğeye, `foreach` döngüdeki yineleme değişkeni üzerinden erişilir.  
  
    - Bu değişkenin `Student`türü ve sorgu değişkeninin türü `IEnumerable<Student>`uyumludur.  
  
2. Bu kodu ekledikten sonra, sonuçları **konsol** penceresinde görmek için uygulamayı derleyin ve çalıştırın.  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Başka bir filtre koşulu eklemek için  
  
1. Bir sorguyu daha iyi daraltmak için `where` yan tümcesinde birden çok Boolean koşulu birleştirebilirsiniz. Aşağıdaki kod, sorgunun ilk puanı 90 üzerinde olan ve son puanı 80 ' den az olan bu öğrencileri döndüren bir koşul ekler. `where` Yan tümce aşağıdaki koda benzemelidir.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Sorguyu Değiştirme  
  
#### <a name="to-order-the-results"></a>Sonuçları sıralamak için  
  
1. Belirli bir sıra türünde olmaları durumunda sonuçların taranması daha kolay olacaktır. Döndürülen sırayı, kaynak öğelerde erişilebilir olan herhangi bir alana göre sıraya alabilirsiniz. Örneğin, aşağıdaki `orderby` yan tümce sonuçları her öğrencinin son adına göre a 'dan Z 'ye alfabetik sırada sıralar. Aşağıdaki `orderby` yan tümceyi, `where` deyiminize ve deyimden önceye `select` ekleyin:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Şimdi, `orderby` yan tümceyi, en yüksek puanın en düşük puanına kadar, ilk testteki puana göre ters sırada sipariş verecek şekilde değiştirin.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Puanları görebilmeniz için biçim dizesini değiştirin: `WriteLine`  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Sonuçları gruplandırmak için  
  
1. Gruplandırma, sorgu ifadelerinde güçlü bir özelliktir. Group yan tümcesi içeren bir sorgu bir grup sırası üretir ve her bir grubun kendisi ve bu grubun `Key` tüm üyelerinden oluşan bir dizi içerir. Aşağıdaki yeni sorgu, en son adının ilk harfini anahtar olarak kullanarak öğrencileri gruplandırır.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Sorgu türünün artık değiştiğini unutmayın. Artık anahtar olarak bir `char` türe ve bir `Student` nesne dizisine sahip olan bir grup sırası oluşturur. Sorgunun türü değiştiği için aşağıdaki kod `foreach` yürütme döngüsünü de değiştirir:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Uygulamayı çalıştırın ve sonuçları **konsol** penceresinde görüntüleyin.  
  
     Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Değişkenlerin dolaylı olarak yazılmasını sağlamak için  
  
1. Açıkça kodlama `IEnumerables` , `IGroupings` hızlı bir şekilde sıkıcı hale gelebilir. `foreach` Kullanarak`var`aynı sorguyu ve döngüyü çok daha kolay bir şekilde yazabilirsiniz. `var` Anahtar sözcüğü nesnelerinizin türlerini değiştirmez; yalnızca derleyiciye tür çıkarması talimatını verir. Türünü `studentQuery` ve `group` yineleme`var` değişkenini değiştirin ve sorguyu yeniden çalıştırın. İç `foreach` döngüde yineleme değişkeninin hala olarak `Student`yazılmış olduğunu ve sorgunun daha önce olduğu gibi çalışıp çalışmadığını unutmayın. Yineleme değişkenini olarak `var` değiştirin ve sorguyu yeniden çalıştırın. `s` Tam olarak aynı sonuçları elde edersiniz.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     [Var](../../../language-reference/keywords/var.md)hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Grupları anahtar değerlerine göre sıralamak için  
  
1. Önceki sorguyu çalıştırdığınızda grupların alfabetik sırada olmadığına dikkat edin. Bunu değiştirmek için, `orderby` `group` yan tümcesinden sonra bir yan tümce sağlamanız gerekir. Ancak `orderby` yan tümce kullanmak için önce `group` yan tümce tarafından oluşturulan gruplara başvuru olarak hizmet veren bir tanımlayıcıya ihtiyacınız vardır. Aşağıdaki gibi `into` anahtar sözcüğünü kullanarak tanımlayıcıyı sağlarsınız:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Bu sorguyu çalıştırdığınızda, grupların artık alfabetik sırada sıralanacağını görürsünüz.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Bir tanımlayıcıyı let kullanarak tanıtmak için  
  
1. Sorgu ifadesinde herhangi bir `let` ifade sonucu için bir tanımlayıcı tanıtmak üzere anahtar sözcüğünü kullanabilirsiniz. Bu tanımlayıcı, aşağıdaki örnekte olduğu gibi kolaylık olabilir veya bir ifadenin sonuçlarını birden çok kez hesaplanmak zorunda kalmayacak şekilde depolayarak performansı geliştirebilir.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Bir sorgu ifadesinde yöntem sözdizimini kullanmak için  
  
1. [Sorgu söz dizimi ve LINQ 'Teki yöntem sözdiziminde](./query-syntax-and-method-syntax-in-linq.md)açıklandığı gibi, bazı sorgu işlemleri yalnızca Yöntem sözdizimi kullanılarak ifade edilebilir. Aşağıdaki kod, kaynak dizideki her biri `Student` için toplam puanı hesaplar ve ardından sınıfın ortalama Puanını hesaplamak için bu sorgunun sonuçlarında `Average()` yöntemi çağırır.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Select yan tümcesinde dönüştürmek ya da planlamak için  
  
1. Bir sorgu için, öğeleri kaynak dizideki öğelerden farklı olan bir sıra üretmek çok yaygındır. Önceki sorgunuzu ve yürütme döngünüzü silin veya bir yorum yapın ve aşağıdaki kodla değiştirin. Sorgunun bir dizi dizeyi (değil `Students`) döndürdüğünü ve bu olgunun `foreach` döngüde yansıtıldığını unutmayın.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Bu kılavuzda daha önce bahsedilen kod, Ortalama sınıf puanının yaklaşık 334 olduğunu gösterdi. Toplam puanı, ortalamasının `Students` , `Student ID`ile birlikte ortalamasının daha büyük olduğu bir dizi oluşturmak için, `select` bildiriminde anonim bir tür kullanabilirsiniz:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 İçindeki C#sorgularla çalışmanın temel yönleri hakkında bilgi sahibi olduktan sonra, ilgilendiğiniz LINQ sağlayıcısı türü için belge ve örnekleri okumaya hazırsınızdır:  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ to Objects (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)
- [LINQ sorgu Ifadeleri](../../linq-query-expressions/index.md)
