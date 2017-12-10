---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8db1b59bd8de523ae74ca198302f814c2d43f25a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>İzlenecek yol: C#'de Sorgu Yazma (LINQ)
Bu kılavuzda LINQ Sorgu ifadeleri yazmak için kullanılan C# dili özelliklerini gösterir.  
  
## <a name="create-a-c-project"></a>Bir C# Projesi Oluşturma  
  
> [!NOTE]
>  Visual Studio için aşağıdaki yönergeleri verilmiştir. Farklı geliştirme ortamını kullanıyorsanız, System.Core.dll bir başvurusu olan bir konsol projesi oluşturun ve bir `using` için yönerge <xref:System.Linq?displayProperty=nameWithType> ad alanı.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Visual Studio'da bir proje oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  Genişletme **yüklü**, genişletin **şablonları**, genişletin **Visual C#**ve ardından **konsol uygulaması**.  
  
4.  İçinde **adı** metin kutusunda, farklı bir ad girin veya varsayılan adı kabul edin ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
5.  Projeniz System.Core.dll başvuru sahip olmadığına dikkat edin ve bir `using` için yönerge <xref:System.Linq?displayProperty=nameWithType> ad alanı.  
  
## <a name="create-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı Oluşturma  
 Veri kaynağı sorgular için basit bir listesidir `Student` nesneleri. Her `Student` kaydına sahip bir ad, Soyadı ve test puanlarını sınıfında temsil eden dizisi. Bu kod projenize kopyalayın. Aşağıdaki özelliklere dikkat edin:  
  
-   `Student` Sınıfı otomatik uygulanan özellikler oluşur.  
  
-   Listedeki her Öğrenci nesne Başlatıcı ile başlatıldı.  
  
-   Liste koleksiyon Başlatıcısı ile başlatıldı.  
  
 Bu tüm veri yapısı başlatılamadı ve herhangi bir oluşturucu veya açık üye erişimi açık çağrılar olmaksızın örneği. Bu yeni özellikler hakkında daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) ve [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağı eklemek için  
  
-   Ekleme `Student` sınıfı ve öğrenciler için başlatılmış listesi `Program` projenizdeki sınıfı.  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir Öğrenci eklemek için  
  
1.  Yeni bir ekleme `Student` için `Students` listesi ve bir ad kullanın ve tercih ettiğiniz puanları sınayın. Daha iyi nesne Başlatıcısı sözdizimi öğrenmek için tüm yeni Öğrenci bilgileri yazmayı deneyin.  
  
## <a name="create-the-query"></a>Sorgu Oluşturma  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
-   Uygulamanın içinde `Main` yöntemi yürütüldüğünde, ilk test, puan 90'dan büyük tüm Öğrenciler listesini oluşturan basit bir sorgu oluşturun. Çünkü unutmayın bütün `Student` nesne seçildiğinde, sorgu türü `IEnumerable<Student>`. Kod kullanarak örtük yazarak da kullanabilirsiniz ancak [var](../../../../csharp/language-reference/keywords/var.md) anahtar sözcüğü, açık yazarak açıkça sonuçları göstermek için kullanılır. (Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Sorgunun ayrıca aralık değişkeni `student`, her bir başvuru olarak hizmet veren `Student` kaynağındaki her nesne için üye erişimi sağlama.  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a>Sorguyu Yürütme  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1.  Şimdi yazma `foreach` döngü çalıştırılacak sorgu neden olur. Kod hakkında aşağıdakileri unutmayın:  
  
    -   Döndürülen dizideki her öğe yineleme değişkeni aracılığıyla erişilen `foreach` döngü.  
  
    -   Bu değişken türü `Student`, ve sorgu değişkeninin türü uyumlu `IEnumerable<Student>`.  
  
2.  Bu kod ekledikten sonra yapı ve sonuçları görmek için uygulamayı çalıştırma **konsol** penceresi.  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a>Başka bir filtre koşulu eklemek için  
  
1.  Birden çok Boolean koşullarında birleştirebilirsiniz `where` başka bir sorgu iyileştirmek için yan tümcesi. Aşağıdaki kod, böylece sorgu bu Öğrenciler, ilk puan döndürür. bir koşul üzerinde 90 ve son, puan 80 şeklindeydi ekler. `where` Yan tümcesi aşağıdaki kodu benzer.  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Daha fazla bilgi için bkz: [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Sorguyu Değiştirme  
  
#### <a name="to-order-the-results"></a>Sonuçları sıralamak için  
  
1.  Bu sipariş çeşit olmaları durumunda tarama sonuçlarını daha kolay olacaktır. Kaynak öğelerin erişilebilir herhangi bir alana tarafından döndürülen dizi sıralayabilirsiniz. Örneğin, aşağıdaki `orderby` yan tümcesi siparişleri sonuçları alfabetik sırada A'dan Z'ye son her öğrencinin adını göre. Aşağıdakileri ekleyin `orderby` sorgunuzu, sonra sağ yan tümcesini `where` deyimi ve önce `select` deyimi:  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  Şimdi değiştir `orderby` onun sonuçlarını ters sırada yüksek puanı düşük skoru için ilk testten üzerinde puan göre sıralar şekilde yan tümcesi.  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  Değişiklik `WriteLine` puanları görebilmeniz için biçim dizesi:  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Daha fazla bilgi için bkz: [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Sonuçları gruplandırmak için  
  
1.  Gruplandırma, sorgu ifadelerinde güçlü bir özelliktir. Sorguda bir group yan tümcesi ile grupları dizisi üretir ve her grubu içeren bir `Key` ve bu grubun tüm üyelerini içeren bir dizisi. Aşağıdaki yeni sorgu anahtarı olarak son kullanıcıların adının ilk harfi kullanarak Öğrenciler gruplandırır.  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Sorgunun türü artık değiştiğini unutmayın. Artık bir dizi olan grupları üreten bir `char` türü bir anahtar ve bir dizi olarak `Student` nesneleri. Sorgunun türü değiştiğinden, aşağıdaki değişiklikleri kod `foreach` yürütme döngüsü de:  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Uygulamayı çalıştırın ve sonuçlarda görüntülemek **konsol** penceresi.  
  
     Daha fazla bilgi için bkz: [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Değişkenlerin dolaylı olarak yazılmasını sağlamak için  
  
1.  Açıkça kodlama `IEnumerables` , `IGroupings` hızla can sıkıcı olabilir. Aynı sorgu yazabilirsiniz ve `foreach` çok daha rahat kullanarak döngü `var`. `var` Anahtar sözcüğü, nesne türlerini değiştirmez; yalnızca türlerini anlamak için derleyicisi bildirir. Türünü değiştirme `studentQuery` ve yineleme değişkeni `group` için `var` ve sorguyu yeniden çalıştırın. İç unutmayın `foreach` döngü, yineleme değişkeni hala yazıldığında olarak `Student`, ve sorgu yalnızca gibi çalışır. Değişiklik `s` yineleme değişkeni `var` ve sorguyu yeniden çalıştırın. Tam olarak aynı sonuçları elde bakın.  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Hakkında daha fazla bilgi için [var](../../../../csharp/language-reference/keywords/var.md), bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Grupları anahtar değerlerine göre sıralamak için  
  
1.  Önceki sorgu çalıştırdığınızda, Gruplar alfabetik sırada olmadığına dikkat edin. Bunu değiştirmek için sağlamanız gereken bir `orderby` yan tümcesinden sonra `group` yan tümcesi. Ancak kullanmak için bir `orderby` yan tümcesi, ilk ihtiyacınız tarafından oluşturulan grupları bir başvuru olarak hizmet veren bir tanımlayıcı `group` yan tümcesi. Tanımlayıcısını kullanarak sağlama `into` aşağıdaki gibi anahtar sözcüğü:  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Bu sorgu çalıştırdığınızda grupları şimdi alfabetik sıraya göre sıralanır görürsünüz.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Bir tanımlayıcıyı let kullanarak tanıtmak için  
  
1.  Kullanabileceğiniz `let` sorgu ifadesinde herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak için anahtar sözcüğü. Bu tanımlayıcı aşağıdaki örnekte olduğu gibi bir kolaylık olabilir veya performans sonuçları bir ifade, böylece birden çok kez hesaplanacak yok depolayarak geliştirebilirsiniz.  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Daha fazla bilgi için bkz: [let tümcesi](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Bir sorgu ifadesinde yöntem sözdizimini kullanmak için  
  
1.  Bölümünde açıklandığı gibi [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), bazı sorgu işlemleri yalnızca yöntemi sözdizimini kullanarak ifade edilebilir. Aşağıdaki kod toplam puanı her biri için hesaplar `Student` kaynak sırası, ve ardından çağrıları `Average()` sınıfının ortalama puanını hesaplamak için bu sorgunun sonuçlarını yöntemi. Sorgu ifadesi parantezler yerleşimini unutmayın.  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Select yan tümcesinde dönüştürmek ya da planlamak için  
  
1.  Kaynak sıraları öğelerinde öğeleri farklı bir dizisini oluşturmak için bir sorgu çok yaygındır. Silin veya önceki sorgu ve yürütme döngüsü açıklama ve aşağıdaki kod ile değiştirin. Sorgu dizeleri bir dizi döndürür unutmayın (değil `Students`), ve bu olgu yansıtılmıştır `foreach` döngü.  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  Bu kılavuzda önceki kod ortalama sınıfı puan yaklaşık 334 belirtilir. Bir dizi üretmek için `Students` birlikte sınıfı ortalama'den büyük olan toplam puanı kendi `Student ID`, anonim bir tür kullanabilirsiniz `select` deyimi:  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Temel sorguları C# ile çalışma yönlerini aşina olduktan sonra belgeler ve örnekler LINQ sağlayıcısının ilgilendiğiniz belirli türü için okumaya hazırsınız:  
  
 [LINQ-SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [LINQ-DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ-XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to nesneler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [C# üzerinde LINQ ile çalışmaya başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)
