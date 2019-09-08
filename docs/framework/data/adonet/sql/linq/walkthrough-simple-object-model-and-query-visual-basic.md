---
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: c21a187739ba19be2dc8e89b4dddc94ad799f036
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792123"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)

Bu izlenecek yol, en az karmaşıklıklarla temel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uçtan uca bir senaryo sağlar. Örnek Northwind veritabanındaki Customers tablosunu modelleyen bir varlık sınıfı oluşturacaksınız. Ardından, Londra 'da bulunan müşterileri listelemek için basit bir sorgu oluşturacaksınız.

Bu izlenecek yol, kavramları göstermeye [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yardımcı olmak için tasarıma göre kod odaklı bir yönergedir. Normalde konuşarak, nesne modelinizi oluşturmak için Nesne İlişkisel Tasarımcısı kullanırsınız.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.

## <a name="prerequisites"></a>Önkoşullar

- Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest") kullanır. Yönergeye başlamadan önce bu klasörü oluşturun.

- Bu izlenecek yol, Northwind örnek veritabanı gerektirir. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md). Veritabanını indirdikten sonra, dosyayı c:\linqtest klasörüne kopyalayın.

## <a name="overview"></a>Genel Bakış

Bu izlenecek yol altı ana görevden oluşur:

- Visual Studio 'da çözüm oluşturma. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]

- Bir sınıfı bir veritabanı tablosuna eşleme.

- Veritabanı sütunlarını temsil etmek için sınıfında Özellikler belirleme.

- Northwind veritabanı bağlantısı belirtiliyor.

- Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.

- Sorgu Yürütülüyor ve sonuçları gözlemleme.

## <a name="creating-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturma

Bu ilk görevde, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz.

### <a name="to-create-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturmak için

1. **Dosya** menüsünde **Yeni proje**' ye tıklayın.

2. **Yeni proje** Iletişim kutusunun **proje türleri** bölmesinde **Visual Basic**' ye tıklayın.

3. **Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.

4. **Ad** kutusuna **LinqConsoleApp**yazın.

5. **Tamam**'ı tıklatın.

## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme

Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır. Projenizde bir başvuru olarak listelenmiyorsa (Çözüm Gezgini **tüm dosyaları göster** ' e tıklayın ve **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin. `System.Data.Linq`

### <a name="to-add-systemdatalinq"></a>System. Data. LINQ eklemek için

1. **Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.

     Derleme projeye eklenir.

3. Ayrıca, **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, öğesine gidin ve System. Windows. Forms ' a tıklayın ve ardından **Tamam**' a tıklayın.

     Yönergedeki ileti kutusunu destekleyen bu derleme projeye eklenir.

4. Aşağıdaki yönergeleri yukarıya `Module1`ekleyin:

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Bir sınıfı bir veritabanı tablosuna eşleme

Bu adımda, bir sınıf oluşturur ve bunu bir veritabanı tablosuyla eşleyin. Böyle bir sınıf bir *varlık sınıfı*olarak adlandırılır. Eşlemenin yalnızca <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği eklenerek gerçekleştirildiğine unutmayın. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Özelliği, veritabanında tablonun adını belirtir.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Bir varlık sınıfı oluşturmak ve veritabanını bir veritabanı tablosuyla eşlemek için

- Aşağıdaki kodu yazın veya hemen üstüne `Sub Main`Module1. vb öğesine yapıştırın:

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Sınıf üzerinde veritabanı sütunlarını temsil etmek için özellikler belirleme

Bu adımda, birkaç görevi gerçekleştirirsiniz.

- <xref:System.Data.Linq.Mapping.ColumnAttribute> Özniteliği, veritabanı tablosundaki sütunları temsil eden `City` varlık sınıfını belirlemek `CustomerID` için kullanın.

- Özelliği, `CustomerID` veritabanında bir birincil anahtar sütununu temsil edecek şekilde belirlersiniz.

- Özel depolama `_CustomerID` alanı `_City` için ve alanlarını belirlersiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]daha sonra, iş mantığını içerebilen ortak erişimcileri kullanmak yerine doğrudan değerleri saklayabilir ve alabilir.

### <a name="to-represent-characteristics-of-two-database-columns"></a>İki veritabanı sütununun özelliklerini temsil etmek için

- Aşağıdaki kodu bir daha önce `End Class`Module1. vb öğesine yazın veya yapıştırın:

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Northwind veritabanı bağlantısını belirtme

Bu adımda, kod tabanlı veri <xref:System.Data.Linq.DataContext> yapılarınız ve veritabanının kendisi arasında bağlantı kurmak için bir nesnesi kullanılır. , <xref:System.Data.Linq.DataContext> Veritabanından nesneleri alıp değişiklikleri gönderdiğiniz ana kanaldır.

Ayrıca, veritabanınızdaki müşteriler `Table(Of Customer)` tablosuna karşı sorgularınız için mantıksal, türü belirlenmiş tablo olarak davranacak bir de bildirir. Daha sonraki adımlarda bu sorguları oluşturup yürüteceksiniz.

### <a name="to-specify-the-database-connection"></a>Veritabanı bağlantısını belirtmek için

- `Sub Main` Yöntemine aşağıdaki kodu yazın veya yapıştırın.

     `northwnd.mdf` Dosyanın linqtest klasöründe olduğunu varsaydığına emin olun. Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a>Basit sorgu oluşturma

Bu adımda, veritabanı müşterileri tablosundaki hangi müşterilerin Londra 'da bulunacağını bulmak için bir sorgu oluşturursunuz. Bu adımdaki sorgu kodu yalnızca sorguyu açıklar. Bunu yürütmez. Bu yaklaşım *ertelenmiş yürütme*olarak bilinir. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Ayrıca, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üreten SQL komutlarını göstermek için bir günlük çıktısı oluşturacaksınız. Bu günlüğe kaydetme özelliğinin (kullandığı <xref:System.Data.Linq.DataContext.Log%2A>) hata ayıklama işlemi sırasında ve veritabanına gönderilen komutların sorgunuzu doğru şekilde temsil ettiğini belirlemek için yararlıdır.

### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için

- Aşağıdaki kodu `Sub Main` , `Table(Of Customer)` bildiriminden sonra yöntemine yazın veya yapıştırın:

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a>Sorgu Yürütülüyor

Bu adımda, aslında sorguyu yürütütemezsiniz. Önceki adımlarda oluşturduğunuz sorgu ifadeleri, sonuçlar gerekene kadar değerlendirilmez. `For Each` Yinelemeye başladığınızda, veritabanına karşı bir SQL komutu yürütülür ve nesneler gerçekleştirilmiş olur.

### <a name="to-execute-the-query"></a>Sorguyu yürütmek için

1. `Sub Main` Yönteminin sonuna aşağıdaki kodu yazın veya yapıştırın (sorgu açıkladıktan sonra):

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. Uygulamada hata ayıklamak için F5 tuşuna basın.

    > [!NOTE]
    > Uygulamanız bir çalışma zamanı hatası oluşturursa, [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md)konusunun sorun giderme bölümüne bakın.

     İleti kutusu, altı müşterinin bir listesini görüntüler. Konsol penceresinde oluşturulan SQL kodu görüntülenir.

3. İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.

     Uygulama kapanır.

4. Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.

     Sonraki yönergeye devam ederseniz bu uygulamaya ihtiyacınız olacaktır.

## <a name="next-steps"></a>Sonraki Adımlar

[İzlenecek yol: İlişkiler genelinde sorgulama (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md) konusu Bu izlenecek yolun sona erdiği yerde devam eder. İlişkiler genelinde sorgulama izlenecek yol, ilişkisel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veritabanındaki *birleştirmelere* benzer şekilde tablolar arasında nasıl sorgu yapılacağını gösterir.

Ilişkiler genelinde sorgulama yapmak istiyorsanız, bir önkoşul olan, az önce tamamladığınız yönergeler için çözümü kaydettiğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
